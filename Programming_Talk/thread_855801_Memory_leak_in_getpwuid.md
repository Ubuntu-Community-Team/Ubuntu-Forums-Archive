---
title: "Memory leak in getpwuid?"
date: 2008-07-10
forum: Programming Talk
---

### Post by tanis1 on 2008-07-10
Basically, I've been having issues trying to track down a memory leak that only seems to affect my Ubuntu 8.04 machine.  I finally narrowed it down to a bunch of calls that query user/group info from the system.

Here is just a quick sample to show the problem with one of the system commands I used: struct passwd *getpwuid(uid_t uid)

```

#include <sys/types.h>
#include <pwd.h>
int main()
{
   uid_t _rootId = 0;
   for ( int i = 0; i < 1000000; i++ )
      getpwuid( _rootId );
   return(0);
}

```

You can run a top and watch the memory climb up quickly... at least on my machine it does.  Other sys calls that seem to be affected are:
getpwuid_r
getgrgid
getgrgid_r
getpwnam

I've basically run this quick example on a machine running RHEL 4 and Fedora Core 9 (and one with Core 5).  No problems at all... the memory doesn't even flinch on those machines.

This box is up to date with the latest core updates as of today (July 10th, 2008).

Am I missing something (VERY possible)?

---

### Post by tanis1 on 2008-07-10
UPDATE:

Did some more testing on my laptop (which also has Ubuntu 8.04) and all is well with that.

The only difference is that the laptop was a fresh 8.04 install versus the problem machine that was an upgrade from a previous version of Ubuntu (7.10).

---

### Post by nvteighen on 2008-07-11
Increase in memory usage is not a memory leak. [http://en.wikipedia.org/wiki/Memory_leak](http://en.wikipedia.org/wiki/Memory_leak)

To check for memory leaks and other memory errors, use the "valgrind" utility. It's in the repos and fairly easy to use.

---

### Post by tanis1 on 2008-07-11
My fault... I should have been more detailed.  Basically, with every loop ... it'll gobble up a little more memory until it reaches the memory limit and dies.  For whatever reason, it doesn't seem to release the memory it consumes for that routine.

Thanks for the note on valgrind... I'll check it out.

---

### Post by tanis1 on 2008-07-11
Valgrind produced a lot of info... here's just a basic summary of running the command (getpwuid) once with no looping routine in place:

==11816== ERROR SUMMARY: 22 errors from 7 contexts (suppressed: 83 from 1)
==11816== malloc/free: in use at exit: 36,079 bytes in 103 blocks.
==11816== malloc/free: 344 allocs, 241 frees, 128,997 bytes allocated.
==11816== For counts of detected errors, rerun with: -v
==11816== searching for pointers to 103 not-freed blocks.
==11816== checked 124,896 bytes.
==11816== 
==11816== LEAK SUMMARY:
==11816==    definitely lost: 34,977 bytes in 97 blocks.
==11816==      possibly lost: 0 bytes in 0 blocks.
==11816==    still reachable: 1,102 bytes in 6 blocks.
==11816==         suppressed: 0 bytes in 0 blocks.


At this point, I have a feeling something might be off from my upgrade.  But it's a strange situation...

---

### Post by nvteighen on 2008-07-12
Run "valgrind -v" It will fire up where the errors are occurring, whether in memory allocated by you or by the library. If it's yours, well it's your job :) If not, there's little you can do.

---

### Post by tanis1 on 2008-07-14
Ran that 'valgrind -v' and it pretty much details all the crazy stuff that is triggered from that getpwuid call.  And like you mentioned... I don't think there's much left for me to do short of re-installing a fresh copy of Ubuntu 8.04.

It's odd... there's obviuosly something (via the upgrade or install of some module) that created this situation.  Ahh well... at least it's noted in case someone else runs into this.

---

### Post by escapee on 2008-07-14
May want to file a bug report if you've concluded it's definitely the library and due to the upgrade.

---

