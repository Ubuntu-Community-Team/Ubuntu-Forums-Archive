---
title: "Can't install gcc3.4"
date: 2008-12-29
forum: Programming Talk
---

### Post by calender2002 on 2008-12-29
I want to install gcc 3.4 on ubuntu8.10. But I found libstdc++6-dev_3.4.6-1ubuntu2_i386.deb and g++-3.4_3.4.6-1ubuntu2_i386.deb depend each other. What's wrong with it? Thanks.

---

### Post by monkeyking on 2008-12-29
try checking out multilib.

I remember I had issues like this in the past,
and multilib apparantly had some needed .so's
---------------------------------
edit:

I have no problems install g++ 3.4,
are you using 32 og 64 bit?

---

### Post by calender2002 on 2008-12-29
I use 32 bits system. And I don't know what's your meaning of multili following def without mistake:

cpp-3.4_3.4.6-1ubuntu2_i386.deb
cpp-3.4-doc_3.4.6-6ubuntu2_all.deb
gcc-3.4_3.4.6-1ubuntu2_i386.deb
gcc-3.4-base_3.4.6-1ubuntu2_i386.deb
libg2c0_3.4.6-1ubuntu2_i386.deb
libg2c0-dev_3.4.6-1ubuntu2_i386.deb

Does someone know why?

---

### Post by jmartrican on 2008-12-29
Maybe you can post what is showing up on the screen?  What steps is the README file having you follow and where does the process breakdown?

---

### Post by calender2002 on 2008-12-30
I just download these files from ubuntu by hand, and copy them to a directory, then double click them, a dialog will display, prompt you to install. And linux is clean. Did someone encounter such question?

---

### Post by monkeyking on 2008-12-30
Have you simply tried

```

sudo apt-get install gcc-3.4

```

?

---

### Post by jmartrican on 2008-12-30
Normally I use apt (apt-get or aptitude) no experience with GUI installs.  The other method for installing software from code is to follow the README or INSTALL guides that the software comes with.  The guides will usually list some libraries you need to install first (so you follow the same procedures for those first).  Eventually the guide will have you do something like configure.sh and/or make and/or make install.  This is where one has to be very careful to read the error messages that get spit out; which might lead to installing more libraries.  The process can take over a day in some cases, other times it goes fairly quickly.

In some cases I needed to disable or enable something or other.  These issues are not too bad because someone on the Internet has encountered it and wrote about it on some forum.  Just do a search for the error message you are getting.

---

