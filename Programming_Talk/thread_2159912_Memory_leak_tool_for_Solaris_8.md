---
title: "Memory leak tool for Solaris 8"
date: 2013-07-05
forum: Programming Talk
---

### Post by Blackbug on 2013-07-05
Hi,

I know its not related to Ubuntu, but I am facing this issue at my workplace.
The client's machine is Solaris 8 ( which is pretty old ), and there are some significant memory leaks. The application is multi-threaded, thus its difficult to find memory leaks via code walk through.

Purify isnt helping much, its showing some random memory leaks in 3rd Party apps not in the application I am trying to debug/analyze. The 3rd party app is okay, since same is working fine on solaris 10 and 11, but the application codebase is completely different in those solaris platforms.

Valgrind isnt supported with Solaris.

So, do I have any other hope in terms of tool for solaris?

Thats why linux is always great........ :)

Thanks.

---

