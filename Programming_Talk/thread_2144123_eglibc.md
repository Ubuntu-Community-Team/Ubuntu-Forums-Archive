---
title: "eglibc?"
date: 2013-05-11
forum: Programming Talk
---

### Post by thedardanius on 2013-05-11
Ok,

so as in my bitmap thread, I got linker errors because of the libxpm library... so I doubted if this has anything to do with my source.
I checked on internet and Im afraid this has to do with the c library im using...
So i checked the version of my libc. Most linux users there say they have sth like libc.so.6 or so, but apparently I  have eglibc.
What??!?
This is really confusing.
And I read that updating/changing the c lib is a arduous and dangerous task....
Please help me out. If I get undefined reference to __fxstats, does this has to do with the c library? And why do I have eglibc, while it is targetting embedded platforms??
Is my ABI for x86 processors and not for embedded? Im using a full laptop...not really embedded.

---

### Post by MadCow108 on 2013-05-11
can't help with the problem, but I can explain was eglibc is.

eglibc is a fork of glibc. It was done because glibc developers were not so friendly towards embedded platforms and some developers were highly skilled but difficult to deal with.
It is fully compatible with glibc and also always kept up to date.
Regular PC developers you should not see any differences.

Recently the glibc steering commission has been dissolved in favor of a more community based model.
This will likely lead to eglibc and glibc merging together again in future.

---

### Post by xytron on 2013-05-11
Ubuntu 9.10 shipped with eglibc 2.10 for it's C library other versions may have as well.

---

### Post by thedardanius on 2013-05-12
but if I compile sth on suse eg with their clib.a, can it actually run and be compatible withthe ABI of ubuntu?

---

### Post by thedardanius on 2013-05-12
is there seriously no solution for undefined references to __fxstat?

---

### Post by xytron on 2013-05-12
An undefined reference then some standard library is not being used and mostly likely to be stat.h

try including both or either one of these;

#include <sys/stat.h>

#include <unistd.h>

to see if it makes a difference

---

### Post by Gyokuro on 2013-05-12
You have not posted a lot of information what is really the problem and further discussion should be done either on eglibc or glibc mailing list in case it is really a libc problem and not some kind of optimization for a certain libc.  Debian and Ubuntu are using eglibc ([http://www.eglibc.org/home](http://www.eglibc.org/home)) whereas Suse/RedHat are using glibc ([http://www.gnu.org/software/libc/](http://www.gnu.org/software/libc/)) and concerning your last post here is some information ([http://refspecs.linuxbase.org/LSB_3.0.0/LSB-Core-generic/LSB-Core-generic/baselib-xstat-1.html](http://refspecs.linuxbase.org/LSB_3.0.0/LSB-Core-generic/LSB-Core-generic/baselib-xstat-1.html)) but your posting is missing information: what is your current Ubuntu release or SuSE release to find out the correct libc version and maybe you can post your code or in case of repo post the url to pull it.

---

### Post by thedardanius on 2013-05-12
guys, I found out that I linked to the lib in the wrong spot. I seperately downloaded it and put it somewhere, of course missing standard libs. Now i linked with -l libXpm, it works! Strange I cant find that lib anywhere manually...

---

