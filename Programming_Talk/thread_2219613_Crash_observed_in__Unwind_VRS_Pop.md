---
title: "Crash observed in _Unwind_VRS_Pop"
date: 2014-04-24
forum: Programming Talk
---

### Post by mmk622 on 2014-04-24
I am using ARM toolchain to cross compile my driver and application code. Gcc-4.2.1, uClibc-0.29.x,binutils-2.19 etc.

My application is crashing by generating a core dump (Segmentation fault). When I analyzed the core dump, I see that crash happens in _Unwind_VRS_Pop() call. Its crashing while writing return address to a local pointer.

Actually _Unwind_VRS_Pop() will be called when there is an exception. Based on ARM documents available online, I see the source of exception is Prefetched Abort.

As per my understanding, when an exception happens, the CPU should store the current register status and return address and quit (when there is no MMU). But in my case, the application is crashing. When analysed the core it shows bactrace with _Unwind_VRS_Pop() as frame 0 (crash in this function). Is this fault with application or toolchain.

Few more important points to mention.
In my applicaiton, I am using a fixed memory pool for all operations. If I increase this memory pool (heap area), I dont see this issue.
I even tried upgrading my toolchain gcc version to 4.2.4. I still see the issue.

Many Thanks, Murali

---

