---
title: "wineboot.exe hogs CPU ..."
date: 2014-08-15
forum: New to Ubuntu
---

### Post by cwmoser on 2014-08-15
The process wineboot.exe hogs my CPU - it consumes 50%.
If I log off and log back in, its still running.
I can kill it but its functionality is not working.

Apparently wineboot.exe starts with the Codeweavers software when I try
to start Quicken I have installed.

I have Ubuntu 14.04, Codeweavers and Quicken on both my desktop PC and my laptop.
This works like a champ on the laptop, fails on the desktop.

Here are some observations on the desktop:
1- no problem with Linux kernel 3.13.0-24 but fails on all subsequent kernel upgrades including:  -30, -32, -33, and -34
2- I am running Gnome Desktop on the desktop, Unity on the laptop
3- winboot.exe consumes 50% CPU and never stops - its hung up on something.

Any ideas?

---

### Post by cwmoser on 2014-08-15
OK, I found a fix.
This thread describes it:
[http://ubuntuforums.org/showthread.php?t=2228133&highlight=wineboot.exe](http://ubuntuforums.org/showthread.php?t=2228133&highlight=wineboot.exe)

Basically there is a "security issue" with 16-bit Windows applications running via WINE in
64-bit versons of Ubuntu - but not a problem with 32-bit Ubuntu.  

The "fix" with its ramifications will work with Linux Kernels 3.13.0-31 and later.
Its simply the following:

$ uname -a
Linux klaatu-2 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

$ sudo echo 1 > /proc/sys/abi/ldt16
bash: /proc/sys/abi/ldt16: Permission denied

$ sudo su
# echo 1 > /proc/sys/abi/ldt16
# 

NOTE:  sudo usage results in a "Permission denied".  You have to su.

I issued this fix and it works properly now.
Check your kernel version - if it is less than -31 this fix will not work.

There is supposed to be an update in the future 3.15 kernel that permanently fixes this.

---

### Post by cwmoser on 2014-08-16
FYI If anyone complains that their Windows application no longer runs on Ubuntu 14.04
64-bit version, above is a likely solution.

---

### Post by JeQhdMD on 2014-08-16
Thanks CW . . . good to know.

---

