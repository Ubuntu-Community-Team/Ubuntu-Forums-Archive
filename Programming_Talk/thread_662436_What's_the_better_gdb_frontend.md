---
title: "What's the better gdb frontend?"
date: 2008-01-08
forum: Programming Talk
---

### Post by TheOrangePeanut on 2008-01-08
I'm looking for a front-end for gdb.  I don't want a full fledged IDE, I just want to use gedit and a separate visual debugger to do some C and C++ programming.  I was looking at ddd and nemiver.  ddd hasn't been updated in a long time, and nemiver hasn't got any help docs on it's site so I don't even know what features it has.  Which would be the better front-end?

Or, if you have any suggestions for a visual debugger that will work with gcc/g++ that ISN'T reliant on gdb, that'd be okay too.

---

### Post by Relain on 2008-01-09
Well all i've tried are totalview and ddd. Total view is one of those products where you get a trial version and then people call you and ask you if you'd like to spend all the money you've ever seen on i it, months after the license expires. That being said it is nice and it's full of features.

However, for all of the problems i've had to hunt down i've found ddd to be more than adaquate. You get lots of info, it supports a whole shed load of debuggers (not just gdb) which is a neat feature. The current version is still a very spare X type application and it can get a bit cranky and crash.

Anyway, i did not get totalview and i don't regret it at all, ddd and gdb all the way.

 I do enjoy telling people that an open source application is better value for me than their product. The IDL people were particularly upset by this.

---

### Post by ideasman42 on 2008-06-03
Hi, I use gedit for editing and eclipse as a debugger, it IS overkill, but its GDB integration is good. Setting up your project just to debug it can be a bit of a pain. but since I only debug sometimes it seems ok.

I can also recomment kdevelop for debugging, its a lot faster then eclipse, especially to start the application (its almost instant), it also has a gdb command line if youd like to use gdb directly.
KDevelop also has valgrind and kcachegrind, not as well integrated as they could be. But much easier then running them from the command line.

So if you only want to debug, Id go with kdevelop, Your app doesn't need to be KDE or anything like that, and you dont need to use it to build your app either.

---

### Post by Can+~ on 2008-06-03
I develop projects with the eclipse cdt plugin, and the frontend of the debugger is quite good.

Before that, I used kdbg, which works well too.

---

### Post by ideasman42 on 2008-07-20
Just found this list of gdb frontends.
[http://en.wikipedia.org/wiki/Debugger_front-end](http://en.wikipedia.org/wiki/Debugger_front-end)

Insight is worth a look.

---

### Post by Mark20 on 2010-02-21
insight (I've tried the latest version - 6.8-1, and an older one) does not compile on Ubuntu 9.04

cc1: warnings being treated as errors
linux-nat.c: In function &#8216;linux_nat_info_proc_cmd&#8217;:
linux-nat.c:2879: error: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
make[2]: *** [linux-nat.o] Error 1
make[2]: Leaving directory `/home/mark/insight-6.8-1/gdb'
make[1]: *** [all-gdb] Error 2
make[1]: Leaving directory `/home/mark/insight-6.8-1'
make: *** [all] Error 2

---

### Post by dwhitney67 on 2010-02-21
> **Mark20 said:**
> insight (I've tried the latest version - 6.8-1, and an older one) does not compile on Ubuntu 9.04

cc1: warnings being treated as errors
linux-nat.c: In function ‘linux_nat_info_proc_cmd’:
linux-nat.c:2879: error: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
make[2]: *** [linux-nat.o] Error 1
make[2]: Leaving directory `/home/mark/insight-6.8-1/gdb'
make[1]: *** [all-gdb] Error 2
make[1]: Leaving directory `/home/mark/insight-6.8-1'
make: *** [all] Error 2

Great!  So... you thought that resurrecting a thread from July 2008 would bring you good fortune?

---

### Post by jpkotta on 2010-02-21
Why do you need to compile it anyway?  It's in the repos.

---

### Post by Mark20 on 2010-02-21
@jpkotta

Good call I should have checked the repos, I was able to get it and it's working great.  Insight seems to be a little better than DDD.  That being said I still think Eclipse is better (assuming you have the time to set it up to properly debug :) )

@dwhitney67
I resurrected a thread from 2008 so that other people in 2010 and beyond will hopefully not make the same mistake I made :p

Cheers,
Mark

---

### Post by MadCow108 on 2010-02-22
> **Mark20 said:**
> insight (I've tried the latest version - 6.8-1, and an older one) does not compile on Ubuntu 9.04

cc1: warnings being treated as errors
linux-nat.c: In function &#8216;linux_nat_info_proc_cmd&#8217;:
linux-nat.c:2879: error: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
make[2]: *** [linux-nat.o] Error 1
make[2]: Leaving directory `/home/mark/insight-6.8-1/gdb'
make[1]: *** [all-gdb] Error 2
make[1]: Leaving directory `/home/mark/insight-6.8-1'
make: *** [all] Error 2

you can fix this with the flag: -Wno-unused-result
or -D_FORTIFY_SOURCE=0 which is 2 by default on ubuntu
or by disabling -Werror

---

