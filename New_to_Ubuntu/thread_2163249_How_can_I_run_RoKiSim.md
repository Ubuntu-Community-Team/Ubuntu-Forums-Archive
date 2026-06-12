---
title: "How can I run RoKiSim??"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by lucapozzobon on 2013-07-17
Hello everybody,
I'm a newbie.
Rokisim is a program where you can simulate robotics tasks. It's pretty cool.
I downloaded the program here [http://www.parallemic.org/RoKiSim.html](http://www.parallemic.org/RoKiSim.html) .
i extracted it in a folder (rokisim) in my desktop. 
I have Ubuntu 12.10 64 bit with wubi.
I place myself in bin folder and i double click RoKiSim.
But nothing happens.
I open terminal, type "ls -l". here's the output (don't bother the language...;)
```
utonto@ubuntu:~/Scrivania/rokisim/RoKiSim 1.20/bin$ ls -ltotale 26004
-rwxr-xr-x 1 utonto utonto   134344 apr 20  2012 ld-2.15.so
-rwxr-xr-x 1 utonto utonto  1713640 apr 20  2012 libc-2.15.so
lrwxrwxrwx 1 utonto utonto       12 lug 12 19:33 libc.so.6 -> libc-2.15.so
-rw-r--r-- 1 utonto utonto    13940 apr 20  2012 libdl-2.15.so
lrwxrwxrwx 1 utonto utonto       13 lug 12 19:33 libdl.so.2 -> libdl-2.15.so
lrwxrwxrwx 1 utonto utonto       17 lug 12 19:33 libexpat.so.1 -> libexpat.so.1.5.2
-rw-r--r-- 1 utonto utonto   165232 mar 15  2012 libexpat.so.1.5.2
lrwxrwxrwx 1 utonto utonto       15 lug 12 19:33 libffi.so.6 -> libffi.so.6.0.0
-rw-r--r-- 1 utonto utonto    21944 ott 13  2011 libffi.so.6.0.0
lrwxrwxrwx 1 utonto utonto       22 lug 12 19:33 libfontconfig.so.1 -> libfontconfig.so.1.4.4
-rw-r--r-- 1 utonto utonto   211660 apr 18  2012 libfontconfig.so.1.4.4
lrwxrwxrwx 1 utonto utonto       20 lug 12 19:33 libfreetype.so.6 -> libfreetype.so.6.8.0
-rw-r--r-- 1 utonto utonto   624084 apr  3  2012 libfreetype.so.6.8.0
-rw-r--r-- 1 utonto utonto   116232 apr 16  2012 libgcc_s.so.1
lrwxrwxrwx 1 utonto utonto       23 lug 12 19:33 libglib-2.0.so.0 -> libglib-2.0.so.0.3200.1
-rw-r--r-- 1 utonto utonto  1014644 apr 16  2012 libglib-2.0.so.0.3200.1
lrwxrwxrwx 1 utonto utonto       12 lug 12 19:33 libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 utonto utonto   878028 mar 23  2012 libGL.so.1.2
lrwxrwxrwx 1 utonto utonto       26 lug 12 19:33 libgobject-2.0.so.0 -> libgobject-2.0.so.0.3200.1
-rw-r--r-- 1 utonto utonto   317288 apr 16  2012 libgobject-2.0.so.0.3200.1
lrwxrwxrwx 1 utonto utonto       26 lug 12 19:33 libgthread-2.0.so.0 -> libgthread-2.0.so.0.3200.1
-rw-r--r-- 1 utonto utonto     5408 apr 16  2012 libgthread-2.0.so.0.3200.1
lrwxrwxrwx 1 utonto utonto       15 lug 12 19:33 libICE.so.6 -> libICE.so.6.3.0
-rw-r--r-- 1 utonto utonto    92364 mar  2  2012 libICE.so.6.3.0
-rw-r--r-- 1 utonto utonto   173576 apr 20  2012 libm-2.15.so
lrwxrwxrwx 1 utonto utonto       12 lug 12 19:33 libm.so.6 -> libm-2.15.so
lrwxrwxrwx 1 utonto utonto       17 lug 12 19:33 libpcre.so.3 -> libpcre.so.3.12.1
-rw-r--r-- 1 utonto utonto   238984 ott 18  2011 libpcre.so.3.12.1
lrwxrwxrwx 1 utonto utonto       18 lug 12 19:33 libpng12.so.0 -> libpng12.so.0.46.0
-rw-r--r-- 1 utonto utonto   165756 apr  5  2012 libpng12.so.0.46.0
-rwxr-xr-x 1 utonto utonto   124663 apr 20  2012 libpthread-2.15.so
lrwxrwxrwx 1 utonto utonto       18 lug 12 19:33 libpthread.so.0 -> libpthread-2.15.so
lrwxrwxrwx 1 utonto utonto       18 lug 12 19:33 libQtCore.so.4 -> libQtCore.so.4.8.1
-rwxr-xr-x 1 utonto utonto  3038008 giu  6  2012 libQtCore.so.4.8.1
lrwxrwxrwx 1 utonto utonto       17 lug 12 19:33 libQtGui.so.4 -> libQtGui.so.4.8.1
-rwxr-xr-x 1 utonto utonto 11661216 giu  6  2012 libQtGui.so.4.8.1
lrwxrwxrwx 1 utonto utonto       21 lug 12 19:33 libQtNetwork.so.4 -> libQtNetwork.so.4.8.1
-rwxr-xr-x 1 utonto utonto  1374052 giu  6  2012 libQtNetwork.so.4.8.1
lrwxrwxrwx 1 utonto utonto       20 lug 12 19:33 libQtOpenGL.so.4 -> libQtOpenGL.so.4.8.1
-rwxr-xr-x 1 utonto utonto  1053764 giu  6  2012 libQtOpenGL.so.4.8.1
-rw-r--r-- 1 utonto utonto    30684 apr 20  2012 librt-2.15.so
lrwxrwxrwx 1 utonto utonto       13 lug 12 19:33 librt.so.1 -> librt-2.15.so
lrwxrwxrwx 1 utonto utonto       14 lug 12 19:33 libSM.so.6 -> libSM.so.6.0.1
-rw-r--r-- 1 utonto utonto    30108 mar  2  2012 libSM.so.6.0.1
lrwxrwxrwx 1 utonto utonto       19 lug 12 19:33 libstdc++.so.6 -> libstdc++.so.6.0.16
-rw-r--r-- 1 utonto utonto   905712 apr 16  2012 libstdc++.so.6.0.16
lrwxrwxrwx 1 utonto utonto       16 lug 12 19:33 libuuid.so.1 -> libuuid.so.1.3.0
-rw-r--r-- 1 utonto utonto    18012 mar 30  2012 libuuid.so.1.3.0
lrwxrwxrwx 1 utonto utonto       15 lug 12 19:33 libX11.so.6 -> libX11.so.6.3.0
-rw-r--r-- 1 utonto utonto  1254264 mar  2  2012 libX11.so.6.3.0
lrwxrwxrwx 1 utonto utonto       15 lug 12 19:33 libXau.so.6 -> libXau.so.6.0.0
-rw-r--r-- 1 utonto utonto     9588 nov  9  2011 libXau.so.6.0.0
lrwxrwxrwx 1 utonto utonto       15 lug 12 19:33 libxcb.so.1 -> libxcb.so.1.1.0
-rw-r--r-- 1 utonto utonto   132660 mar 22  2012 libxcb.so.1.1.0
lrwxrwxrwx 1 utonto utonto       17 lug 12 19:33 libXdmcp.so.6 -> libXdmcp.so.6.0.0
-rw-r--r-- 1 utonto utonto    21824 nov  9  2011 libXdmcp.so.6.0.0
lrwxrwxrwx 1 utonto utonto       16 lug 12 19:33 libXext.so.6 -> libXext.so.6.4.0
-rw-r--r-- 1 utonto utonto    68232 mar  2  2012 libXext.so.6.4.0
lrwxrwxrwx 1 utonto utonto       19 lug 12 19:33 libXrender.so.1 -> libXrender.so.1.3.0
-rw-r--r-- 1 utonto utonto    34424 mar  2  2012 libXrender.so.1.3.0
lrwxrwxrwx 1 utonto utonto       15 lug 12 19:33 libz.so.1 -> libz.so.1.2.3.4
-rw-r--r-- 1 utonto utonto    83572 nov 10  2011 libz.so.1.2.3.4
-rwxrwxrwx 1 utonto utonto   751840 mag  1 03:38 RoKiSim

```
in terminal I try typing RoKiSim or ./RoKiSim... but nothing happens...The program isn't available in the Ubuntu Software Center.
How can I run it????
THX.

---

### Post by Toz on 2013-07-17
Please do not create duplicate threads. The active thread can be found [here]("http://ubuntuforums.org/showthread.php?t=2163247"). Closing this one.

---

