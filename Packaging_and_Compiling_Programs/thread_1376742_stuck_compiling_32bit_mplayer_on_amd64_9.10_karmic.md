---
title: "stuck compiling 32bit mplayer on amd64 9.10 karmic"
date: 2010-01-09
forum: Packaging and Compiling Programs
---

### Post by DexterF on 2010-01-09
checked out today's mplayer svn. 

Ran with the instructions found here:
[http://ubuntuforums.org/showthread.php?t=739011](http://ubuntuforums.org/showthread.php?t=739011)

Installed gcc-4.2 package since MPlayer people told me <4.4.2 = not good.
Installed libc6-dev-i386 and all the other stuff, running the config line I modified to 

CC="/usr/bin/gcc-4.2 -m32" ./configure --disable-runtime-cpudetection --target=i686-linux --libdir=/usr/lib32 --prefix=/usr/local --win32codecsdir=/usr/lib/win32 --enable-x11 --enable-xv

gets me

Error: Cannot find header either inttypes.h or bitypes.h. There is no chance for compilation to succeed.

inttypes.h is in the mplayer checkout, bitypes.h is in /usr/incluse/sys/.

Dunno what else to check. 

Help?

---

### Post by adam814 on 2010-01-09
Hmm...I think the Medibuntu Repository has a w64codecs package designed for 64-bit systems.

You could try "apt-get build-dep vlc" to see if you're missing any libraries you need to build vlc.

---

### Post by andrew.46 on 2010-01-10
Hi DexterF,

> **DexterF said:**
> Dunno what else to check. 

I cannot help much with compiling the 32bit MPlayer on a 64bit system but I suspect your system needs a little more preparation. Have a look at this guide:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

and extract what you need in terms of building tools and development packages. Unfortunately I know next to nothing about building a 32bit player on a 64bit system so I cannot be too much more help than that :(.

Andrew

---

### Post by mc4man on 2010-01-10
While I use 32 bit just to see did build a 32bit mplayer on amd64 (live cd, I guess last summer

I don't remember all the particulars, but it did work out, found this post which shows some of the steps.
- i may or may not of also tried using getlibs, but for karmic you'd need to be careful there 
(getlibs uses a package list to get and install deps, so a karmic mplayer would show the ffmpeg libs which you definitely don't want installed. (libavcodec-dev. libavformat-dev, ect.

I may try again sometime to see, though if the reason for using a 32 bit is for wmap (wma3) then just build your own current 64 bit mplayer

[http://ubuntuforums.org/showthread.php?t=1232173&highlight=32+bit+mplayer&page=3](http://ubuntuforums.org/showthread.php?t=1232173&highlight=32+bit+mplayer&page=3)  post #28

Edit: actually reading thru the above link I did use getlibs and whatever else is linked to.
note that any file versions mentioned were for whatever livecd I was using (maybe jaunty, don't remember, though in any event with a little patience it all worked out  fine

---

