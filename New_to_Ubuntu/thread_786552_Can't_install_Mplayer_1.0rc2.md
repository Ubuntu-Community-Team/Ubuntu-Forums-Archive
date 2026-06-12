---
title: "Can't install Mplayer 1.0rc2"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by happyee on 2008-05-08
I'm a beginner in linux and found Ubuntu is very easy to use.
but when want to watch .mkv video I need to install Mplayer, and then I got this problem:




Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.1.3, ok 
Checking for host cc ... cc 
Checking for cross compilation ... yes 
Checking for CPU vendor ... GenuineIntel (6:15:13) 
Checking for CPU type ...  Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz 
Checking for kernel support of mmx ... failed 
It seems that your kernel does not correctly support mmx.
To use mmx extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of mmxext ... failed 
It seems that your kernel does not correctly support mmxext.
To use mmxext extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse ... failed 
It seems that your kernel does not correctly support sse.
To use sse extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse2 ... failed 
It seems that your kernel does not correctly support sse2.
To use sse2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of ssse3 ... failed 
It seems that your kernel does not correctly support ssse3.
To use ssse3 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of cmov ... failed 
It seems that your kernel does not correctly support cmov.
To use cmov extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for mtrr support ... yes 
Checking for GCC & CPU optimization abilities ... CPU optimization disabled. CPU not recognized or your compiler is too old. 
error 
Checking for assembler support of -pipe option ... no 
Checking for compiler support of named assembler arguments ... yes 
Checking for assembler (as ) ... ok 
Checking for .align is a power of two ... no 
Checking for Linux kernel version ... 2.6.22-14-generic, ok 
Checking for -lposix ... no 
Checking for -lm ... no 
Checking for langinfo ... no 
Checking for language ... using en (man pages: en ) 
Checking for enable sighandler ... yes 
Checking for runtime cpudetection ... no 
Checking for restrict keyword ... none 
Checking for __builtin_expect ... no 
Checking for kstat ... no 
Checking for posix4 ... no 
Checking for lrintf ... no 
Checking for mkstemp ... no 
Checking for nanosleep ... no 
Checking for socklib ... no 
Checking for inet_pton() ... no (trying inet_aton next)
Checking for inet_aton() ... no (network support disabled)
Checking for network ... no 
Checking for inttypes.h (required) ... no 
Checking for bitypes.h (inttypes.h predecessor) ... 
Error: Cannot find header either inttypes.h or bitypes.h. There is no chance for compilation to succeed.


Hoping someone can help me~~

---

### Post by warbread on 2008-05-08
Have you tried just playing the file in VLC?  I believe it comes with the H264 codec, which should play .MKV files.

---

### Post by sy88 on 2008-05-08
Are you compiling from source?  Instead, you can try installing through "apt-get install mplayer" in cli.  VLC's a viable alternative as well.

---

### Post by hermes0710 on 2008-05-08
Why don't you install mplayer through the medibuntu repositories?

Open a terminal and execute:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install mplayer w32codecs libdvdcss2
```

---

