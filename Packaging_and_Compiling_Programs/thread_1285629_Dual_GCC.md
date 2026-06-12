---
title: "Dual GCC"
date: 2009-10-08
forum: Packaging and Compiling Programs
---

### Post by LinLux451 on 2009-10-08
Hello, I am a long time linux user.... well.. kinda.. I know my way around, let's just say that. I am currently running Hardy on an old P4. My true intention is to build a beowulf off of openMosix and an old vanilla 2.24.26 kernel for a CISCO project. I have patched and configurated off of [http://ubuntuforums.org/showthread.php?t=17012]("http://ubuntuforums.org/showthread.php?t=17012") and tried to compile and install but alas, I was shut down by the fact openMosix kernel require the 2.95.3 and I'm still using whatever Hardy came with (not usually a compiler.. usually a firefoxer), anyway, I downloaded the tarball from a mirror, and have been using [http://www.tellurian.com.au/whitepapers/multiplegcc.php]("http://www.tellurian.com.au/whitepapers/multiplegcc.php") as my guide to installing gcc-2.95.3. My problem is I get compiling errors with the bootstrap command. The last few lines of output being:
```
/usr/local/gcc/2.95.3/i686-pc-linux-gnu/bin/ -c -g -O2 -I. -I/home/skynet/gcc-2.95.3/libio -D_IO_MTSAFE_IO  /home/skynet/gcc-2.95.3/libio/iogetline.c -o pic/iogetline.o
/home/skynet/gojb/gcc/xgcc -B/home/skynet/gojb/gcc/ -B/usr/local/gcc/2.95.3/i686-pc-linux-gnu/bin/ -c -g -O2 -I. -I/home/skynet/gcc-2.95.3/libio -D_IO_MTSAFE_IO /home/skynet/gcc-2.95.3/libio/iogetline.c
In file included from /home/skynet/gcc-2.95.3/libio/libio.h:167,
                 from /home/skynet/gcc-2.95.3/libio/iolibio.h:1,
                 from /home/skynet/gcc-2.95.3/libio/libioP.h:47,
                 from /home/skynet/gcc-2.95.3/libio/iogetline.c:26:
/usr/include/bits/stdio-lock.h:24: lowlevellock.h: No such file or directory
make[2]: *** [iogetline.o] Error 1
make[2]: Leaving directory `/home/skynet/gojb/i686-pc-linux-gnu/libio'
make[1]: *** [all-target-libio] Error 2
make[1]: Leaving directory `/home/skynet/gojb'
make: *** [bootstrap] Error 2

```

Any help with getting gcc 2.95 installed would be lovely! I should be in the clear for "Unibuntu" after that, but... no promises. Thanks for all the help with Ubuntu, Debain, Linux, and life. The ubuntuforums is probably one of the most amazing communities on the web! (BTW, I couldn't think of a better beowulf name then skynet:lolflag:)

---

### Post by LinLux451 on 2009-10-10
*bump

---

### Post by dinxter on 2009-10-11
unfortunately I'm amd64 so can't test the compile, shows you how old 2.95 is :) But you might want to check out old packages from ubuntu and see if they work
[http://se.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-2.95/](http://se.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-2.95/)

---

### Post by LinLux451 on 2009-10-14
No luck. I still got compiling errors through Hardy. I installed Sarge on the box, patched and configurated the 2.4.26 code, and tried to compile, but it failed. I found the gcc version to be 4.1
well apt can fix that!
```
# apt-get install gcc-2.95
# apt-get remove gcc-4.1
```

So that's the damage of my commands. Now when I ask the version, I get: 
```
- bash /usr/bin/gcc: No such file or directory
```

So if there was some way to get gcc-2.95 from my apt cache to the /usr/bin , I think that would work out.. hahaha... I'm so ancy to compile this thing.... it's been far too long.

---

### Post by dinxter on 2009-10-15
You can pass the compiler as a environmental variable ie,
./configure CC=gcc-2.95 
so you can have a number of different compilers installed and specify each one to configure as you see fit.
I think openmosix on anything vaguely modern could be a pain to get going, if you have the choice I would try and look at some other beowulfery options, ones that are still active

---

### Post by LinLux451 on 2009-10-15
:D Danka!
I have looked at other options, and I don't believe Kerringhed uses shared memory support, or automatic process migration... which makes it... sort of worthless. I do think openMosix is my best bet, even with all the compile errors... the machines I'm planning on running this are pretty old so... If I can get around all the compile errors, I'd say I'm good. *finger cross*
Anyway, I love using STD (Straight Terminal Debian) :D It's nice to refresh my wget and tarball skills, indstead of just X.

---

