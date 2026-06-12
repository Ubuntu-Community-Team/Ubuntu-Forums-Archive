---
title: "How To Install 32 bit ZSNES without chroot on amd64"
date: 2006-10-07
forum: Outdated Tutorials &amp; Tips
---

### Post by cborga1985 on 2006-10-07
[COLOR="Red"][I][B][SIZE="5"]Notice: This only works for Dapper at the moment. 
If you find another way, let me know and I will update this post with you credited.[/SIZE][/B][/I][/COLOR]

This is my first howto so don't be too harsh on me please. I recommend you copy and paste to simplify this howto.

**Step 1 Open Terminal**
Alt+F2 on keyboard and paste this
```
gnome-terminal
```
now click run or just hit enter/return :twisted: 

**Step 2 Download ZSNES package**
```
wget http://71.200.156.30/Custom%20Debs/zsnes/zsnes_cvs20060815-1_i386.deb
```
**or**
In Terminal Paste
```
firefox http://www.megaupload.com/?d=W59RU0HO
```
Then type in the random letters/numbers in the box in the **upper right corner**
Then Click Download of course. Save it somewhere and then cd in terminal to where you saved it.

**Step 3 Install the depends** :lol:
```
sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl ia32-alsa-oss nasm
```

**Step 4 Install ZSNES package**
```
sudo dpkg -i --force-architecture zsnes_cvs20060815-1_i386.deb
```
P.S. Don't use that very often as that is kind of dangerous. :-k

---

### Post by cborga1985 on 2006-10-09
Edit: Moderator feel free to remove #2 post.

---

### Post by cborga1985 on 2006-10-15
Edit: Moderator feel free to remove #3 post.

---

### Post by infinit1 on 2006-10-17
Nice job, and thanks. :KS

---

### Post by glenn45 on 2006-10-29
Thanks for this guide. Finally i can convince my girlfriend to use ubuntu and i am one step closer to deleting my windows partition.  Zsnes is one of the reason why i keep my computer on dual boot. Hopefully with this guide i can let her be weaned away from windows. hehehehe. Thanks!:p

---

### Post by cborga1985 on 2006-11-03
> **glenn45 said:**
> Thanks for this guide. Finally i can convince my girlfriend to use ubuntu and i am one step closer to deleting my windows partition.  Zsnes is one of the reason why i keep my computer on dual boot. Hopefully with this guide i can let her be weaned away from windows. hehehehe. Thanks!:p
no problem

---

### Post by incubus on 2006-11-04
Good job, cborga!
It works flawlessly, even the audio.

Thanks a lot.

incubus

---

### Post by Jingu on 2006-11-26
```
$ sudo apt-get install ia32-alsa-oss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-alsa-oss
```

:( 

I'm pretty sure I have all the repositories enabled.
Everything else seemed to install correctly.

---

### Post by moxfyre on 2006-12-05
This strategy worked great for me under dapper, but doesn't work any longer under edgy or feisty as far as I can tell :-(

The ia32-alsa-oss package isn't available, and zsnes can't find libncurses when it starts (why zsnes needs ncurses is beyond me...)

```

ldd `which zsnes`
        linux-gate.so.1 =>  (0xffffe000)
        libz.so.1 => /usr/lib32/libz.so.1 (0xf7f64000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7edc000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ec4000)
        libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf7ea1000)
        libncurses.so.5 => not found
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7e32000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7d4d000)
        libm.so.6 => /lib32/libm.so.6 (0xf7d25000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7d1a000)
        libc.so.6 => /lib32/libc.so.6 (0xf7bd8000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7b16000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7b12000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7a49000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7a3c000)
        /lib/ld-linux.so.2 (0xf7f8f000)
        libXxf86vm.so.1 => /usr/lib32/libXxf86vm.so.1 (0xf7a36000)
        libdrm.so.2 => /usr/lib32/libdrm.so.2 (0xf7a2f000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7a2c000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7a27000)

```

It seems that if there were a way to install the 32-bit ncurses library, zsnes would probably work.  Any thoughts?

---

### Post by cborga1985 on 2006-12-07
> **moxfyre said:**
> This strategy worked great for me under dapper, but doesn't work any longer under edgy or feisty as far as I can tell :-(

The ia32-alsa-oss package isn't available, and zsnes can't find libncurses when it starts (why zsnes needs ncurses is beyond me...)

```

ldd `which zsnes`
        linux-gate.so.1 =>  (0xffffe000)
        libz.so.1 => /usr/lib32/libz.so.1 (0xf7f64000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7edc000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ec4000)
        libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf7ea1000)
        libncurses.so.5 => not found
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7e32000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7d4d000)
        libm.so.6 => /lib32/libm.so.6 (0xf7d25000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7d1a000)
        libc.so.6 => /lib32/libc.so.6 (0xf7bd8000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7b16000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7b12000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7a49000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7a3c000)
        /lib/ld-linux.so.2 (0xf7f8f000)
        libXxf86vm.so.1 => /usr/lib32/libXxf86vm.so.1 (0xf7a36000)
        libdrm.so.2 => /usr/lib32/libdrm.so.2 (0xf7a2f000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7a2c000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7a27000)

```

It seems that if there were a way to install the 32-bit ncurses library, zsnes would probably work.  Any thoughts?
nothing personal but stuff like this is why i don't use edgy. maybe someone with edgy can figure this out.

---

### Post by janfsd on 2006-12-18
Thanks for the guide, I am on Edgy and is working for me, just the sound is not the best quality, but it doesn't matter, any possibilty for a newer deb? for instance the last wip, or a svn release?

EDIT: I installed the Ubuntu deb (its v.1.42) and the sound now is working great!!

---

### Post by cborga1985 on 2006-12-31
> **janfsd said:**
> Thanks for the guide, I am on Edgy and is working for me, just the sound is not the best quality, but it doesn't matter, any possibilty for a newer deb? for instance the last wip, or a svn release?

EDIT: I installed the Ubuntu deb (its v.1.42) and the sound now is working great!!
oh that version always gave me problems

---

### Post by dfreer on 2007-01-09
hmmm... I'm running a Intel Core 2 Duo (with Edgy 64-bit), so maybe that makes a difference. But I was able to download all of the dependencies, and then install the zsnes package without a problem. Works great! Thanks for the guide.

---

### Post by janfsd on 2007-01-09
Well, I managed to compile the last version (1.50).
However the svn version has implented libao support, I think it is better than sdl (and gives me a better quality of sound), and it's no hard to compile :)

---

### Post by janfsd on 2007-01-12
Well I am posting one of the latest svn builds (it includes libao) so if you have problems with sdl, then this works better:
[http://rapidshare.com/files/11407904/zsnes.tar.gz](http://rapidshare.com/files/11407904/zsnes.tar.gz)

To run, with libao, type:
```
./zsnes -ad oss
```
you can change oss with alsa, esd ,arts,etc. but for me oss works the best (i get some sound delay with alsa option)
Don't forget to install the libao libraries (32 bit) Just extract them in /usr/lib32 and sudo ldconfig

---

### Post by cborga1985 on 2007-03-15
> **janfsd said:**
> Well I am posting one of the latest svn builds (it includes libao) so if you have problems with sdl, then this works better:
[http://rapidshare.com/files/11407904/zsnes.tar.gz](http://rapidshare.com/files/11407904/zsnes.tar.gz)

To run, with libao, type:
```
./zsnes -ad oss
```
you can change oss with alsa, esd ,arts,etc. but for me oss works the best (i get some sound delay with alsa option)
Don't forget to install the libao libraries (32 bit) Just extract them in /usr/lib32 and sudo ldconfig
that didn't work for me but the one i have is working just fine

---

### Post by dfreer on 2007-04-11
here's zsnes stable version 1.51 *.debs with libao compiled in (I compiled them both in Ubuntu Feisty, although they should install on Dapper and Edgy). 

[_*zsnes 1.51 for amd64*_]("http://www.dfreer.org/~dfreer/zsnes/zsnes_latest_amd64.deb")
[_*zsnes 1.51 for i386*_]("http://www.dfreer.org/~dfreer/zsnes/zsnes_latest_i386.deb")

Oh yeah, they should both launch from Applications > Games > zsnes

Let me know if they help anyone/if there is any problems with them!

---

### Post by dfreer on 2007-04-11
updated the .deb files so that they are official builds (recompiled with both --enable-release and --enable-libao). Same links as before.

---

### Post by Slammer64 on 2007-04-20
dfreer: Tried your method on a AMD64 bit install of Feisty, ZSNES promptly seg-faults with a core-dump I have lib32ncurses installed and have the libao libraries in /lib32, even did an ldd to check and make sure it has all the required libraries, stumped myself, but if you could pass along how you compiled it on AMD64 Fiesty, please let me know, ok?

---

### Post by dfreer on 2007-04-21
hmmm I'll check it out. It isn't compiled in amd64, it is a x86 build using a AMD64 package. For now you can use the i386 build with: 
```
sudo dpkg -i --force-architecture zsnes_latest_i386.deb
```
Since that is basically the same as the AMD64 package (although the AMD64 package would install things *nicely*). I'll try to create a how-to and update the amd64.deb here really quick. 

Could you post all output, in case I can't get it to reproduce? Also, what version of Ubuntu are you using?

---

### Post by dfreer on 2007-04-22
hmmm. so I did a reinstall of x86_64 (for one, upgraded to feisty :) but also to try the zsnes amd64 package on a fresh install). I'm having the exact same problems. Even the i386.deb (which runs fine in x86) seg faults when using --force-architecture. 

I compiled zsnes using the following commands (after downloading source and cd to src directory within zsnes):
```
./autogen.sh --enable-release --enable-libao
make
```
And then I simply wrapped the binary in a nice comfy *.deb. I will try to see if I can fix this, so for now the zsnes amd64 .deb's are broken.

---

### Post by dfreer on 2007-04-23
it seems that if you compile zsnes with libao support it segfaults. Prolly has to do with libao dependencies. I will continue to work on libao support, but for now I will update my amd64 .debs so that libao is not included. the link in my profile should take you to them (check changes.txt for details)

compiling from svn (zsnes version 1.52), with libao and release enabled, produces binaries that don't seg fault. However, from the output it looks like it is using SDL instead of libao. 
```
$ ./zsnes.svn.release.libao
ZSNES v1.52, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
**[B]Driver: Simple DirectMedia Layer output**[/B]
Channels: 2
Rate: 32000

ZSNES could not find any joysticks.
```

---

