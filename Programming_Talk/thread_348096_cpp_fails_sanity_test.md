---
title: "cpp fails sanity test"
date: 2007-01-28
forum: Programming Talk
---

### Post by surhudm on 2007-01-28
Dear all,

I am trying to compile some programs like (recordmydesktop) on ubuntu edgy. When I run configure it gives me the /lib/cpp fails sanity test error. I tried to search for help and found that if I install build-essential the problem would be solved. Unfortunately this also did not happen.

gcc libc6 libc6-dev cpp g++ build-essential : I have all of these packages installed. If I do a sudp apt-get install for these packages then it reports that all the packages are installed.

In the config.log which is the file suggested to be seen after the ./configure does not work, I found the following lines...

In file included from conftest.c:12:
/usr/include/limits.h:125:26: error: no include path in which to search for limits.h
configure:3770: $? = 1

I checked whether the file exists and /usr/include/limits.h exists. What does this no include path error mean? I even tried removing build-essential and reinstalling it. But it made no difference.

Since every configure file has this conftest.c I cannot compile any program from the source on my edgy. Please guide me as to what to do.

Surhud

---

### Post by surhudm on 2007-01-28
Hi all,

I realised there was some problem with my bashrc. I had exported the GCC_ROOT variable although with the correct path. I do not know how that made a difference. But when I removed that, the program compiled neatly. 

So all that one needs is build-essential I suppose...

Surhud

---

