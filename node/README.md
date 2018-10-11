# Problems

## 1
```
<--- Last few GCs --->

[60212:0x104802400]   115403 ms: Scavenge 1300.8 (1423.7) -> 1300.6 (1424.2) MB, 3.0 / 0.0 ms  (average mu = 0.338, current mu = 0.328) allocation failure
[60212:0x104802400]   115408 ms: Scavenge 1301.2 (1424.2) -> 1300.8 (1424.2) MB, 3.4 / 0.0 ms  (average mu = 0.338, current mu = 0.328) allocation failure
[60212:0x104802400]   115413 ms: Scavenge 1301.6 (1424.2) -> 1301.1 (1425.2) MB, 3.0 / 0.0 ms  (average mu = 0.338, current mu = 0.328) allocation failure


<--- JS stacktrace --->

==== JS stack trace =========================================

    0: ExitFrame [pc: 0x21c701f841bd]
Security context: 0x27c02f79e6c9 <JSObject>
    1: _replaceInStringNode [0x27c0f3868921] [/Users/ndavalos/Development/castleblack/node_modules/webpack-sources/lib/ReplaceSource.js:~197] [pc=0x21c70356e135](this=0x27c0908ab271 <Source map = 0x27c0aedd06a1>,output=0x27c0731304e1 <JSArray[53]>,replace=0x27c073130491 <ReplacementEnumerator map = 0x27c02b596e11>,getOriginalSource=0x27c073130719 <JSFunction...

FATAL ERROR: Ineffective mark-compacts near heap limit Allocation failed - JavaScript heap out of memory
 1: 0x100033aa9 node::Abort() [/usr/local/bin/node]
 2: 0x100035236 node::FatalTryCatch::~FatalTryCatch() [/usr/local/bin/node]
 3: 0x10017a8fb v8::Utils::ReportOOMFailure(v8::internal::Isolate*, char const*, bool) [/usr/local/bin/node]
 4: 0x10017a89d v8::internal::V8::FatalProcessOutOfMemory(v8::internal::Isolate*, char const*, bool) [/usr/local/bin/node]
 5: 0x1004532f2 v8::internal::Heap::UpdateSurvivalStatistics(int) [/usr/local/bin/node]
 6: 0x100454f95 v8::internal::Heap::CheckIneffectiveMarkCompact(unsigned long, double) [/usr/local/bin/node]
 7: 0x100452657 v8::internal::Heap::PerformGarbageCollection(v8::internal::GarbageCollector, v8::GCCallbackFlags) [/usr/local/bin/node]
 8: 0x1004515a8 v8::internal::Heap::CollectGarbage(v8::internal::AllocationSpace, v8::internal::GarbageCollectionReason, v8::GCCallbackFlags) [/usr/local/bin/node]
 9: 0x1004597a7 v8::internal::Heap::AllocateRawWithRetry(int, v8::internal::AllocationSpace, v8::internal::AllocationAlignment) [/usr/local/bin/node]
10: 0x1004373b0 v8::internal::Factory::NewFillerObject(int, bool, v8::internal::AllocationSpace) [/usr/local/bin/node]
11: 0x1006318d1 v8::internal::Runtime_AllocateInNewSpace(int, v8::internal::Object**, v8::internal::Isolate*) [/usr/local/bin/node]
12: 0x21c701f841bd
[1]    60210 abort      npm run watch
```
## Solution
Running the script with `NODE_OPTIONS=--max-old-space-size=4096`. Information on `NODE_OPTIONS` found [here](https://stackoverflow.com/questions/48387040/nodejs-recommended-max-old-space-size)
