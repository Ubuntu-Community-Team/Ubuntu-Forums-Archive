---
title: "Load different version of libfdk-aac.so than ldd is showing"
date: 2017-04-17
forum: Packaging and Compiling Programs
---

### Post by monkeypy on 2017-04-17
I am having an issue where I need <file>.sc  to load libfdk-aac.so.0 but when I do ldd <file>.sc I am getting 
    libfdk-aac.so.1 => /usr/lib/x86_64-linux-gnu/libfdk-aac.so.1 (0x00007ff6953bf000)

I have been trying to figure out in the code if there is a place to set this. I have tried changing the LD_LIBRARY_PATH. I've searched stackoverflow but I can't seem to get it to load so.0 rather than so.1.
Another thing I tried was completely removing libfdk-aac.so.1 from my computer but then the program would not compile.

Could anyone give me some advice on how to fix this or where to look? Thanks.

---

### Post by mc4man on 2017-04-17
If <file>.sc (whatever that is) is compiled by you then you've used libfdk-aac-dev (0.1.4.x), so it links to libfdk-aac.so.1 (libfdk-aac1 package
If you need it to use libfdk-aac.so.0, (libfdk-aac0 package),  then you need to install libfdk-aac-dev ( 0.1.3.x)

While it's possible to have both libfdk-aac0 & libfdk-aac1 installed at the same time, only one version of the -dev can be installed (both sources uses the same name for the -dev package..

Post ```
apt-cache policy libfdk-aac*
```

---

### Post by monkeypy on 2017-04-17
Awesome, thank you for the quick response. I am not able to test this out until tomorrow morning. I will try it and update. Thank you.

---

### Post by monkeypy on 2017-04-19
Update: This solved my problem. Thank you.

---

