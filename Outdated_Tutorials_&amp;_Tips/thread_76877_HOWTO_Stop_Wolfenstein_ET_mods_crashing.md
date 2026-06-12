---
title: "HOWTO: Stop Wolfenstein ET mods crashing"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Curufir on 2005-10-15
I don't know how many people play this game, but the information probably applies to a lot of other commercial games too.

Basically what happens is that when you try to join a server using certain mods the game crashes.

If you're using the terminal to launch the game you'll see a message like:
```
Sys_Error: VM_Create on UI failed
```

What you probably won't see is that further back the game tries to load a .so file that depends on the libstdc++.so.5 library, which Breezy doesn't use (Hoary _did_ use it).

Simple fix:

sudo apt-get install libstdc++5

This just installs the library and a symlink to it, your standard Breezy libraries will be unaffected.

---

### Post by Jenda on 2005-10-16
Thanks! this might save some trouble!

---

### Post by pbmax on 2006-08-27
I tried that, and the lib was already installed.
I've had this working, then no sound, then sound, but it crashes on map connect.
sigh.
anyone ?

---

### Post by pbhj on 2009-11-08
This seems to have sorted things out for me ... added libstdc5++ package from [http://packages.debian.org/lenny/i386/libstdc++5/download](http://packages.debian.org/lenny/i386/libstdc++5/download) . As I'm on a 64 but system though I needed to extract the two files and put them in my /usr/lib32 folder. I had already installed the amd64 version without success - I'd try with just the 32 bit ones first and if it doesn't work add the other too.

---

