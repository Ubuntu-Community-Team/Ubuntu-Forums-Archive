---
title: "crazy thing with compiler"
date: 2006-04-16
forum: Programming Talk
---

### Post by marco34 on 2006-04-16
Hi,

Recently I've tried to compile some tarball package (ddccontrol) and I run into problems. It seems that for some reason compiler can't find GTK includes. I have to mention that I've installed GTK dev package.
Is seems that compiler can't find files in /usr/include subdirectories. How can I "register" /usr/include subdirectories to be recognited as default include locations, too?

Thanks,
marco

---

### Post by LordHunter317 on 2006-04-16
You can't and you shouldn't have to.  How did you run configure?

---

### Post by nagilum on 2006-04-16
Well, you can do so by adjusting your $CFLAGS environment variable but as LordHunter317 already said, you usually don't have to. This is handled by your configure script which (in most cases) utilizes pkg-config for the actual work of finding the right include directories and libraries needed for linking.

---

### Post by marco34 on 2006-04-16
I just run ./configure inside build directory

---

### Post by LordHunter317 on 2006-04-16
You likely needed to pass it some options run 'configure --help' to find out what they are.  Post here if you need anymore help.

---

