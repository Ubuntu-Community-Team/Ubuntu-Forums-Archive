---
title: "needs codec for MPlayer movie player"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by misswham on 2008-11-06
I just reinstalled ubuntu and I was able to play these videos with the movie players on here but it says now

The playback of this movie requires a video/x-avi-unknown decoder plugin which is not installed.

where can I find it and what do i do?

---

### Post by LowSky on 2008-11-06
if you use 32 bit 

```
wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb
```
```
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb
```

if you use 64bit **dont install both 32 and 64**

```
wget -c http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb
```
```
sudo dpkg -i w64codecs_20071007-0medibuntu1_amd64.deb
```

look into adding the medibuntu repos if you need DVD support and more

---

### Post by misswham on 2008-11-06
How can I know if I am using 32 or 64?

---

### Post by misswham on 2008-11-06
Linux ree-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux


does this help in finding out what i am running?

---

### Post by sisco311 on 2008-11-06
> **misswham said:**
> Linux ree-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 **i686** GNU/Linux


does this help in finding out what i am running?

yes, you are running the 32bit version.

---

### Post by Idefix82 on 2008-11-06
You don't need to post the same question in different threads. While people are helping you, they can't help others. You wouldn't want to wait for an answer for a long time simply because somebody else is asking his question in multiple threads: [http://ubuntuforums.org/showthread.php?t=973194]("http://ubuntuforums.org/showthread.php?t=973194")

---

### Post by philinux on 2008-11-06
i686 means you're running 32bit

---

### Post by misswham on 2008-11-06
this is the error message i got from running the above commands  what can i do?

:~$ wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb)
--12:35:37--  [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb)
           => `w32codecs_20071007-0medibuntu2_i386.deb'
Resolving packages.medibuntu.org... 88.191.79.39, 88.191.82.11
Connecting to packages.medibuntu.org|88.191.79.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14,283,118 (14M) [application/x-debian-package]

100%[====================================>] 14,283,118   737.04K/s    ETA 00:00

12:35:58 (701.38 KB/s) - `w32codecs_20071007-0medibuntu2_i386.deb' saved [14283118/14283118]

ree@ree-desktop:~$ sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb
[sudo] password for ree: 
Selecting previously deselected package w32codecs.
(Reading database ... 124902 files and directories currently installed.)
Unpacking w32codecs (from w32codecs_20071007-0medibuntu2_i386.deb) ...
dpkg: dependency problems prevent configuration of w32codecs:
 w32codecs depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing w32codecs (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 w32codecs

---

### Post by clb137 on 2008-11-06
> **misswham said:**
> I just reinstalled ubuntu and I was able to play these videos with the movie players on here but it says now

The playback of this movie requires a video/x-avi-unknown decoder plugin which is not installed.

where can I find it and what do i do?

HI,

have look at this thread [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

it has all the info you need

clint

---

### Post by mafi29 on 2009-02-24
> **misswham said:**
> this is the error message i got from running the above commands  what can i do?


dpkg: dependency problems prevent configuration of w32codecs:
 w32codecs depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing w32codecs (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 w32codecs

The error message says that the package w32codecs depends on libstdc++5, but libstdc++5 is not installed. It means that you need to install the GNU Standard C++ Library (libstdc++5).
You can do this by 

```
sudo aptitude install libstdc++5
```

---

