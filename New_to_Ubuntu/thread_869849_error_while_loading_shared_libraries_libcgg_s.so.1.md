---
title: "error while loading shared libraries: libcgg_s.so.1"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by yello_ubu on 2008-07-25
I cannot run apt-get/aptitude/synaptic without getting this error

error while loading shared libraries: libcgg_s.so.1: cannot open shared object file: no such file or directory

And it's right, 'find' doesn't find that file

Brief history;

- took an auto update this morning
- it complained about dependancies on xulrunner and something else
- I had a 'forced version' of xulrunner to run an app called'Pytrainer'
- I removed 'pytrainer' & it look python with it plus and a whole heap of other stuff... apps and gnu (front end graphical stuff I guess)
- reboot and only get command line
- I'm trying to rebuild the system but, as I say, can't get update anything... there's a hole in my bucket!!

Edit: can find libgcc bits on the file system, notably in /usr/lib/gcc/i486-linux/gnu/4.2

Um, HELP!!! basically!

---

### Post by Bachstelze on 2008-07-25
It's a wonder your systèm still runs at all... I guess you're in for a reinstall.

---

### Post by yello_ubu on 2008-07-25
I don't think I'll need to re-install. I have pretty much everything bar a front end. I have network access so can get at repositories etc. 

Besides, my original install disk is banjoed!!

---

### Post by yello_ubu on 2008-07-25
I'll take that as a 'no' then shall I?;)

I'm currently burning another disk but if that doesn't work, I'm tempted to head back to win2k, sad as that may be. Not sure I can handle stuff breaking when updates are loaded. It's happened to me a few times now and whilst it's fun digging myself out of the hole, I am getting a bit paranoid about when the next one will be.

---

