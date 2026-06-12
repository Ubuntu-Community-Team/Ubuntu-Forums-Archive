---
title: "Compiling 32 bit mplayer on a 64 bit system?"
date: 2008-03-29
forum: Packaging and Compiling Programs
---

### Post by eyelessfade on 2008-03-29
I'm trying to compile 32bit binarys of mplayer to run on my 64bit host. until now without luck.

```
./configure --enable-cross-compile --target=i686-linux --prefix=/home/user/software/mplayer-svn/ --win32codecsdir=/home/user/software/essential-20071007
```

gives the output of:
```
Detected operating system: Linux
Detected host architecture: i686
Checking for cc version ... 4.1.3, ok
Checking for host cc ... cc
Checking for cross compilation ... yes
Checking for CPU vendor ... GenuineIntel (6:15:6)
Checking for CPU type ...  Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
Checking for kernel support of mmx ... yes
Checking for kernel support of mmxext ... yes
Checking for kernel support of sse ... yes
Checking for kernel support of sse2 ... yes
Checking for kernel support of ssse3 ... yes
Checking for kernel support of cmov ... yes
Checking for mtrr support ... yes
Checking for GCC & CPU optimization abilities ... CPU optimization disabled. CPU not recognized or your compiler is too old.
i686
Checking for extern symbol prefix ...
Checking for assembler support of -pipe option ... yes
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
Checking for llrint ... no
Checking for lrint ... no
Checking for lrintf ... no
Checking for round ... no
Checking for roundf ... no
Checking for mkstemp ... no
Checking for nanosleep ... no
Checking for socklib ... no
Checking for inet_pton() ... no (trying inet_aton next)
Checking for inet_aton() ... no (network support disabled)
Checking for network ... no
Checking for inttypes.h (required) ... no
Checking for bitypes.h (inttypes.h predecessor) ...
Error: Cannot find header either inttypes.h or bitypes.h. There is no chance for compilation to succeed.

Check "configure.log" if you do not understand why it failed.
```

"configure.log" gives ```
============ Checking for bitypes.h (inttypes.h predecessor) ============

#include <sys/bitypes.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=i686 -mtune=i686 -pipe -ffast-math -fomit-frame-pointer      -o /tmp/mplayer-conf--31425 /tmp/mplayer-conf--31425.c
/tmp/mplayer-conf--31425.c:1: error: CPU you selected does not support x86-64 instruction set
```

I have "ia32-libs lib32gcc1 lib32stdc++6 libc6-dev-i386 gcc-multilib" installed.

---

### Post by mc4man on 2008-03-29
> Error: Cannot find header either inttypes.h or bitypes.h.
Haven't done any work on or for 64 bit - possibly you should also add libc6-dev-amd64

---

### Post by eyelessfade on 2008-03-29
already got libc6-dev.
the thing is it compiles just fine for 64 bit, but that doesn't help me since I want the win32codecs.

---

### Post by eyelessfade on 2008-04-01
anyone?

---

### Post by hoarycripple on 2008-05-05
I've compiled 32 bit mplayer successfully on x86_64 after some experimentation.  Everything works well, and you can use the win32 codecs to play virtually any media file. 

Install the required libraries prior to attempting the compile:
1.  ia32-libs
2.  libc6-dev-i386
3.  g++-multilib

There may be a library I'm forgetting here, but configure will complain about it if there is something missing.  If it complains about something and you can't figure it out, let me know and I'll try and decipher the error message for you.

Next, we need to go to the /usr/lib32 directory and make symlinks.  For some reason, once the 32bit libs are installed, the correct symlinks are not made.  

```
cd /usr/lib32
ln -s libX11.so.6 libX11.so
ln libXv.so.1 libXv.so
```

After that we can attempt the compile:

```
CC="gcc -m32" \
./configure --disable-runtime-cpudetection \
--target=i686-linux \
--libdir=/usr/lib32 \
--prefix=/usr/local \
--win32codecsdir=/usr/lib/win32 \
--enable-x11 \
--enable-xv
```

If all goes well, execute:

```
make
sudo make install
mv /usr/local/bin/mplayer /usr/local/bin/mplayer32
mv /usr/local/bin/mencoder /usr/local/bin/mencoder32
```

That should do it.  You'll have to experiment with the video output configs for mplayer if you want something other than xv or X11 output.  If, say, you want SDL output, you'll have to go into your /usr/lib32 dir and make the appropriate symlinks.  But you get the idea...

I hope that helps.

hoarycripple

---

### Post by eyelessfade on 2008-05-07
Thank you I will try this :)



Worked like a charm.

---

### Post by phsource on 2008-09-15
Hi,

Sorry to resurrect such an old thread, but I am having trouble compiling MPlayer using this method. The problem is that it detects none of my encoder libraries or related items: here's what I found in configure.log

Here's what it says:
```
============ Checking for Xvid ============

#include <xvid.h>
int main(void) { xvid_global(0, 0, 0, 0); return 0; }

gcc -m32 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=i686 -mtune=i686 -pipe -ffast-math -fomit-frame-pointer         -o /tmp/mplayer-conf--3282 /tmp/mplayer-conf--3282.c -lxvidcore -lm
/usr/bin/ld: skipping incompatible /usr/local/lib/libxvidcore.a when searching for -lxvidcore
/usr/bin/ld: cannot find -lxvidcore
collect2: ld returned 1 exit status

```

It does not appear to look for the 32-bit version of xvid. Now, for Xvid, there's only one library and set of includes in /usr/local/lib, so I'm not sure if I can get that to work. However, I remember a few days back that it worked when I tried to compile it with everything. However, a reinstall's been done, and now it doesn't.

but for Freetype:

```
gcc -m32 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=i686 -mtune=i686 -pipe -ffast-math -fomit-frame-pointer         -o /tmp/mplayer-conf--3282 /tmp/mplayer-conf--3282.c -I/usr/include/freetype2 -lfreetype -lz
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libfreetype.so when searching for -lfreetype
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libfreetype.a when searching for -lfreetype
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libfreetype.so when searching for -lfreetype
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libfreetype.a when searching for -lfreetype
/usr/bin/ld: skipping incompatible /usr/lib/libfreetype.so when searching for -lfreetype
/usr/bin/ld: skipping incompatible /usr/lib/libfreetype.a when searching for -lfreetype
/usr/bin/ld: cannot find -lfreetype
collect2: ld returned 1 exit status
```

How can I make it so that it looks in the right places? Freetype occurs in /usr/lib32, but it's not looking there. Do I need to get 32-bit libraries by getting new packages or anything? Do I need to use a different set of options?

Thanks

---

### Post by duffrecords on 2008-11-10
It probably *is* looking in /usr/lib.  Take a look at the error message.  It needs freetype.so but if you look in /usr/lib32 you'll probably only find something like freetype.so**.6**.  Just make a symbolic link to the library.  I wrote a [bash script]("http://ubuntuforums.org/showthread.php?t=977064") that automatically does this for every library in /usr/lib32.

---

### Post by marysiak on 2009-04-09
I got the message "bash: ./configure: No such file or directory" on trying to compile.

I just want audio on my wmv files, can they not pu some sort of warning on the 64-bit version that tells you not to bother installing it if you want your computer to actually work, I regret the day #i ever went near 64 bit architecture. I have spent so much time trying to get things to work that don't have 64-bit support.

---

### Post by Cracauer on 2009-04-09
> **marysiak said:**
> I got the message "bash: ./configure: No such file or directory" on trying to compile.

I just want audio on my wmv files, can they not pu some sort of warning on the 64-bit version that tells you not to bother installing it if you want your computer to actually work, I regret the day #i ever went near 64 bit architecture. I have spent so much time trying to get things to work that don't have 64-bit support.

That particular error message doesn't lead me assume it is an overly obscure 64 bit related problem...

---

### Post by mc4man on 2009-04-11
There is a mplayer patch now for the 64 bit version that allows playback of wmv3 and wma3 (wma pro audio
wma lossless is still not playable

post about
[http://ubuntuforums.org/showthread.php?p=7036084#post7036084](http://ubuntuforums.org/showthread.php?p=7036084#post7036084)

---

### Post by laplaceme on 2009-09-15
For someone who meet the same problem as me.

I used hoarycripple's method and got errors like this when compile:

libavcodec/libavcodec.a(lcl.o)(.text+0xe5): In function `decode_frame':
: undefined reference to `inflateReset' 

It turns out the problem is the zlib. I successfully compiled after adding "-lz" after "$(EXTRA_LIB) " in the Makefile and force installing  "zlib1g-dev_1.2.3-6ubuntu4_i386.deb" 


> **hoarycripple said:**
> I've compiled 32 bit mplayer successfully on x86_64 after some experimentation.  Everything works well, and you can use the win32 codecs to play virtually any media file. 

Install the required libraries prior to attempting the compile:
1.  ia32-libs
2.  libc6-dev-i386
3.  g++-multilib

There may be a library I'm forgetting here, but configure will complain about it if there is something missing.  If it complains about something and you can't figure it out, let me know and I'll try and decipher the error message for you.

Next, we need to go to the /usr/lib32 directory and make symlinks.  For some reason, once the 32bit libs are installed, the correct symlinks are not made.  

```
cd /usr/lib32
ln -s libX11.so.6 libX11.so
ln libXv.so.1 libXv.so
```

After that we can attempt the compile:

```
CC="gcc -m32" \
./configure --disable-runtime-cpudetection \
--target=i686-linux \
--libdir=/usr/lib32 \
--prefix=/usr/local \
--win32codecsdir=/usr/lib/win32 \
--enable-x11 \
--enable-xv
```

If all goes well, execute:

```
make
sudo make install
mv /usr/local/bin/mplayer /usr/local/bin/mplayer32
mv /usr/local/bin/mencoder /usr/local/bin/mencoder32
```

That should do it.  You'll have to experiment with the video output configs for mplayer if you want something other than xv or X11 output.  If, say, you want SDL output, you'll have to go into your /usr/lib32 dir and make the appropriate symlinks.  But you get the idea...

I hope that helps.

hoarycripple

---

