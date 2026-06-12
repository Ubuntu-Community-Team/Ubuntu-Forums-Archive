---
title: "issues with make when compiling"
date: 2016-09-13
forum: Packaging and Compiling Programs
---

### Post by NotQuiteSU on 2016-09-13
I noticed a few people having a similiar experience. I'm trying to build this tool, comskip. [https://github.com/erikkaashoek/Comskip](https://github.com/erikkaashoek/Comskip) on Linux Server 14.

I am able to get to everything except the last step of 

```

git clone git://github.com/erikkaashoek/Comskip
cd Comskip
./autogen.sh
./configure
make
```

When I run make, I get the following error:

> 
gcc -g -O2 -mtune=generic    -o comskip comskip-comskip.o  comskip-mpeg2dec.o comskip-platform.o comskip-video_out_dx.o  ccextratorwin/comskip-608.o ccextratorwin/comskip-ccextractor.o  ccextratorwin/comskip-encoding.o ccextratorwin/comskip-general_loop.o  ccextratorwin/comskip-myth.o -largtable2   -pthread -L/opt/ffmpeg/lib  -L/build/ffmpeg-zTq240/ffmpeg-3.1.1~trusty/build_libs/lib -lavformat  -lavcodec -lXv -lXext -lvdpau -lva-drm -lva-x11 -lva -lxcb-shm  -lxcb-xfixes -lxcb-render -lxcb-shape -lxcb -lX11 -lasound -lSDL  -lxvidcore -lx265 -lx264 -lpthread -lvpx -lvorbisenc -lvorbis -logg  -lvidstab -lspeex -lpulse -lopus -lopencore-amrwb -lopencore-amrnb  -lmp3lame -lfreetype -lfdk-aac -lass -lgnutls -lbz2 -lz -ldl  -lswresample -lsoxr -lavutil -lm    -lpthread -lm
/usr/bin/ld: cannot find -lXv
/usr/bin/ld: cannot find -lvdpau
/usr/bin/ld: cannot find -lxcb-shm
collect2: error: ld returned 1 exit status
make: *** [comskip] Error 1


I know that /usr/bin/ld exists.

---

### Post by &amp;KyT$0P# on 2016-09-13
You need to install those libraries and the corresponding dev packages.

It looks like in the package manager those specific missing libraries are [FONT=Courier New]libxv1[/FONT], [FONT=Courier New]libvdpau1[/FONT], [FONT=Courier New]libxcb-shm0[/FONT] (but what's weird is it seems only libxcb-shm0 has a dev package?)

---

### Post by NotQuiteSU on 2016-09-13
I tried that - 

root:# apt-get install libxv1
Reading package lists... Done
Building dependency tree
Reading state information... Done
libxv1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by mc4man on 2016-09-13
It's libxv-dev, libvdpau-dev, libxcb-shm0-dev ect.

---

### Post by NotQuiteSU on 2016-09-13
Thank you. How can I determine that so I don't keep bugging you? Now I'm getting

/usr/bin/ld: cannot find -lvidstab
/usr/bin/ld: cannot find -lfreetype
/usr/bin/ld: cannot find -lass
/usr/bin/ld: cannot find -lgnutls

Which I can't find any packages for

---

### Post by mc4man on 2016-09-13
Though don't see any need for those files, builds fine here without. (Ubuntu 16.04
What Linux Server 14 may need I've no clue, maybe post the results of your ./configure

---

### Post by NotQuiteSU on 2016-09-13
```
# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for fmax in -lm... yes
checking for sem_post in -lpthread... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether host is win32... no
checking whether host is darwin... no
checking whether to enable donator features... yes
checking whether to build a statically linked binary... no
checking whether to build with debugging options enabled... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for argtable2... yes
checking for ffmpeg... yes
checking for sdl... yes
checking whether to build the graphical user interface... yes
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: executing depfiles commands

```

Then
```
# make
gcc -g -O2 -mtune=generic    -o comskip comskip-comskip.o comskip-mpeg2dec.o comskip-platform.o comskip-video_out_dx.o ccextratorwin/comskip-608.o ccextratorwin/comskip-ccextractor.o ccextratorwin/comskip-encoding.o ccextratorwin/comskip-general_loop.o ccextratorwin/comskip-myth.o -largtable2   -pthread -L/opt/ffmpeg/lib -L/build/ffmpeg-zTq240/ffmpeg-3.1.1~trusty/build_libs/lib -lavformat -lavcodec -lXv -lXext -lvdpau -lva-drm -lva-x11 -lva -lxcb-shm -lxcb-xfixes -lxcb-render -lxcb-shape -lxcb -lX11 -lasound -lSDL -lxvidcore -lx265 -lx264 -lpthread -lvpx -lvorbisenc -lvorbis -logg -lvidstab -lspeex -lpulse -lopus -lopencore-amrwb -lopencore-amrnb -lmp3lame -lfreetype -lfdk-aac -lass -lgnutls -lbz2 -lz -ldl -lswresample -lsoxr -lavutil -lm    -lpthread -lm
/usr/bin/ld: cannot find -lvidstab
/usr/bin/ld: cannot find -lfreetype
/usr/bin/ld: cannot find -lass
/usr/bin/ld: cannot find -lgnutls
collect2: error: ld returned 1 exit status
make: *** [comskip] Error 1

```

---

### Post by &amp;KyT$0P# on 2016-09-13
> **NotQuiteSU said:**
> Thank you. How can I determine that 
See how they're all start with a [FONT=Courier New]-l[/FONT]?  Ignore that part.  It's the rest you pay attention to.
What I would do is just put that in Synaptic Package Manager quick filter and look for the related-seeming dev package.  If you don't have Synaptic, enter these commands in a Terminal to get it (plus apt-xapian-index, which is needed for the quick filter feature to work).
```
sudo apt-get install apt-xapian-index
sudo apt-get --no-install-recommends install synaptic
```

So, take this error for example -
```
/usr/bin/ld: cannot find -lgnutls
```
So open up Synaptic and put in [FONT=Courier New]gnutls[/FONT] in the quick filter, and you should see [FONT=Courier New]libgnutls-dev[/FONT].

[This site]("http://packages.ubuntu.com/") can also help you determine the package name, but for this purpose, it's not as easy to work with as Synaptic.

---

### Post by #&amp;thj^% on 2016-09-13
> **NotQuiteSU said:**
> Then

I am not quite sure you have read the whole page that you have for your install.
You will need Ubuntu Trusty (14.04)

```
sudo add-apt-repository -y ppa:mc3man/trusty-media
  sudo apt-get update
```

```
sudo apt-get install -y git build-essential libargtable2-dev libsdl1.2-dev
  sudo apt-get install -y ffmpeg libva-dev libsoxr-dev libvorbis-dev libbz2-dev zlib1g-dev libxvidcore-dev libvpx-dev libx264-dev libx265-dev libspeex-dev libfdk-aac-dev libvorbisenc2 libopus-dev libmp3lame-dev libdca-dev libfaac-dev libopencore-amrnb-dev libvo-aacenc-dev libopencore-amrwb-dev
```

```
 git clone https://github.com/foo86/dcadec
$ cd dcadec
$ make install

```
Then maybe try again with your install.

---

### Post by &amp;KyT$0P# on 2016-09-13
By the way, it really should be up to the configure script to checking for needed libraries / dev packages and giving an informative error if they're not present.  I have never seen something like the way this configure script apparently handles it, which is, er, basically not at all.

Probably you should file a bug with comskip about it.

---

### Post by NotQuiteSU on 2016-09-13
More issues

```

/Comskip# make
/bin/bash ./config.status --recheck
running CONFIG_SHELL=/bin/bash /bin/bash ./configure PKG_CONFIG_PATH=/opt/ffmpeg/lib/pkgconfig --no-create --no-recursion
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for fmax in -lm... yes
checking for sem_post in -lpthread... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether host is win32... no
checking whether host is darwin... no
checking whether to enable donator features... yes
checking whether to build a statically linked binary... no
checking whether to build with debugging options enabled... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for argtable2... yes
checking for ffmpeg... yes
checking for sdl... yes
checking whether to build the graphical user interface... yes
checking that generated files are newer than configure... done
configure: creating ./config.status
 /bin/bash ./config.status
config.status: creating Makefile
config.status: executing depfiles commands
gcc -g -O2 -mtune=generic    -o comskip comskip-comskip.o comskip-mpeg2dec.o comskip-platform.o comskip-video_out_dx.o ccextratorwin/comskip-608.o ccextratorwin/comskip-ccextractor.o ccextratorwin/comskip-encoding.o ccextratorwin/comskip-general_loop.o ccextratorwin/comskip-myth.o -largtable2   -pthread -L/opt/ffmpeg/lib -L/build/ffmpeg-zTq240/ffmpeg-3.1.1~trusty/build_libs/lib -lavformat -lavcodec -lXv -lXext -lvdpau -lva-drm -lva-x11 -lva -lxcb-shm -lxcb-xfixes -lxcb-render -lxcb-shape -lxcb -lX11 -lasound -lSDL -lxvidcore -lx265 -lx264 -lpthread -lvpx -lvorbisenc -lvorbis -logg -lvidstab -lspeex -lpulse -lopus -lopencore-amrwb -lopencore-amrnb -lmp3lame -lfreetype -lfdk-aac -lass -lgnutls -lbz2 -lz -ldl -lswresample -lsoxr -lavutil -lm    -lpthread -lm
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_free':
(.text+0x17fc): undefined reference to `XCloseDisplay'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_create':
(.text+0x1870): undefined reference to `XOpenDisplay'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_create':
(.text+0x1885): undefined reference to `vaGetDisplay'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_create':
(.text+0x1899): undefined reference to `XDisplayName'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_create':
(.text+0x191f): undefined reference to `vaGetDisplayDRM'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_create':
(.text+0x1954): undefined reference to `XDisplayName'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_create':
(.text+0x19f5): undefined reference to `XDisplayName'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vdpau.o): In function `vdpau_device_create':
(.text+0x58e): undefined reference to `XOpenDisplay'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vdpau.o): In function `vdpau_device_create':
(.text+0x5a3): undefined reference to `XDisplayString'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vdpau.o): In function `vdpau_device_create':
(.text+0x5af): undefined reference to `XDefaultScreen'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vdpau.o): In function `vdpau_device_create':
(.text+0x5c1): undefined reference to `vdp_device_create_x11'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vdpau.o): In function `vdpau_device_create':
(.text+0x68b): undefined reference to `XDisplayName'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vdpau.o): In function `vdpau_device_free':
(.text+0x6cc): undefined reference to `XCloseDisplay'
collect2: error: ld returned 1 exit status
make: *** [comskip] Error 1


```

---

### Post by NotQuiteSU on 2016-09-13
> **1fallen said:**
> I am not quite sure you have read the whole page that you have for your install.
You will need Ubuntu Trusty (14.04)

```
sudo add-apt-repository -y ppa:mc3man/trusty-media
  sudo apt-get update
```

```
sudo apt-get install -y git build-essential libargtable2-dev libsdl1.2-dev
  sudo apt-get install -y ffmpeg libva-dev libsoxr-dev libvorbis-dev libbz2-dev zlib1g-dev libxvidcore-dev libvpx-dev libx264-dev libx265-dev libspeex-dev libfdk-aac-dev libvorbisenc2 libopus-dev libmp3lame-dev libdca-dev libfaac-dev libopencore-amrnb-dev libvo-aacenc-dev libopencore-amrwb-dev
```

```
 git clone https://github.com/foo86/dcadec
$ cd dcadec
$ make install

```
Then maybe try again with your install.

I have absolutely done that. But I'll try it all again from scratch. I may just scrap this whole thing and upgrade to 16.

---

### Post by #&amp;thj^% on 2016-09-13
Installed fine here?

---

### Post by NotQuiteSU on 2016-09-13
what path did you install it in? what version of linux?

---

### Post by &amp;KyT$0P# on 2016-09-13
> **NotQuiteSU said:**
> 
```

/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_free':
(.text+0x17fc): undefined reference to `XCloseDisplay'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_create':
(.text+0x1870): undefined reference to `XOpenDisplay'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_create':
(.text+0x1885): undefined reference to `vaGetDisplay'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_create':
(.text+0x1899): undefined reference to `XDisplayName'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_create':
(.text+0x191f): undefined reference to `vaGetDisplayDRM'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_create':
(.text+0x1954): undefined reference to `XDisplayName'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vaapi.o): In function `vaapi_device_create':
(.text+0x19f5): undefined reference to `XDisplayName'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vdpau.o): In function `vdpau_device_create':
(.text+0x58e): undefined reference to `XOpenDisplay'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vdpau.o): In function `vdpau_device_create':
(.text+0x5a3): undefined reference to `XDisplayString'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vdpau.o): In function `vdpau_device_create':
(.text+0x5af): undefined reference to `XDefaultScreen'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vdpau.o): In function `vdpau_device_create':
(.text+0x5c1): undefined reference to `vdp_device_create_x11'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vdpau.o): In function `vdpau_device_create':
(.text+0x68b): undefined reference to `XDisplayName'
/opt/ffmpeg/lib/libavutil.a(hwcontext_vdpau.o): In function `vdpau_device_free':
(.text+0x6cc): undefined reference to `XCloseDisplay'
collect2: error: ld returned 1 exit status
make: *** [comskip] Error 1


```
What ffmpeg is that and how/where did you get it?

---

### Post by NotQuiteSU on 2016-09-13
from the instructions?

---

### Post by #&amp;thj^% on 2016-09-13
> **NotQuiteSU said:**
> what path did you install it in? what version of linux?

local/comskip 0.93-3
    Comskip is a free MPEG commercial break detector.
Since the instructions were for trusty...14.04 but my DE is "mate" but that should not make a difference.
Maybe? mc4man has changed something in his PPA... this has been installed years ago. I do testing here so there may have been some changes.
But this has gone through several kernel upgrades that I also test...current kernel 4.7.2-1
EDIT: I also compile FFMPEG from source on trusty...I just remembered this.

---

### Post by NotQuiteSU on 2016-09-13
i cloned my stuff to /opt/. I don't think that should matter, would you?

---

### Post by #&amp;thj^% on 2016-09-13
Good Question...I have mine in Home
That is just my preference.
I am hoping that mc4man will add anything relating to his PPA here.

---

### Post by NotQuiteSU on 2016-09-13
I'll try it out in Home. I am using server, and may just take this oppourtunity to jump to 16.

---

### Post by #&amp;thj^% on 2016-09-13
You know it might be worth it to upgrade to 16.04...but test it first in a live environment to see if it is compatible with your current hardware.
I tweak my system very hard so I won't be of much help here.
My current version of FFMPEG is as follows
```
ffmpeg --version
ffmpeg version 3.1.3 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 6.1.1 (GCC) 20160802
  configuration: --prefix=/usr --disable-debug --disable-static --disable-stripping --enable-avisynth --enable-avresample --enable-fontconfig --enable-gmp --enable-gnutls --enable-gpl --enable-ladspa --enable-libass --enable-libbluray --enable-libfreetype --enable-libfribidi --enable-libgsm --enable-libiec61883 --enable-libmodplug --enable-libmp3lame --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libv4l2 --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx264 --enable-libx265 --enable-libxvid --enable-netcdf --enable-shared --enable-version3 --enable-x11grab
  libavutil      55. 28.100 / 55. 28.100
  libavcodec     57. 48.101 / 57. 48.101
  libavformat    57. 41.100 / 57. 41.100
  libavdevice    57.  0.101 / 57.  0.101
  libavfilter     6. 47.100 /  6. 47.100
  libavresample   3.  0.  0 /  3.  0.  0
  libswscale      4.  1.100 /  4.  1.100
  libswresample   2.  1.100 /  2.  1.100
  libpostproc    54.  0.100 / 54.  0.100

```
And mc4man has already confirmed it installs on 16.04.
Sorry I am not more helpful here.

---

### Post by &amp;KyT$0P# on 2016-09-13
> **NotQuiteSU said:**
> i cloned my stuff to /opt/. I don't think that should matter, would you?
Yes.  Some of this stuff is path-dependent, I wouldn't "clone" anything anywhere else.

If you need a custom path for ffmpeg, I'd suggest compiling it from source (which might have other advantages for you as well).  But why are you cloning it at all?


* To be clear, it should be OK to work with downloaded source code in /opt and build stuff from in /opt.  That path is generally up to you.
Just don't copy random other stuff there as well, leave it where it was installed.

---

### Post by mc4man on 2016-09-13
I won't be at my trusty machine until tonight but in 14.04 you wouldn't be using ffmpeg shared & devel libs, you'd be using libav9's
(-the ffmpeg in that ppa is only for use of the ffmpeg binaries, not for building against. And in that regard you wouldn't be building against as the .h & .a files are installed to /opt/, e.g. not in the default ld path

So it's possible that that current git source cannot use libav9 or you've done something. It'll only take a few minutes later to figure that out...

---

### Post by mc4man on 2016-09-13
You cannot build the current git using trusty's libav libraries (libav9), as  the min. requirements have been moved up. Can be seen here - 
> configure: error: Package requirements (libavutil >= 54.7 libavformat >= 56.4 libavcodec >= 56.1) were not met: 

Even with libav11 in 14.04 it still not good enough, seen here - 
> configure: error: Package requirements (libavutil >= 54.7 libavformat >= 56.4 libavcodec >= 56.1) were not met:

Requested 'libavutil >= 54.7' but version of libavutil is 54.3.0
Requested 'libavformat >= 56.4' but version of libavformat is 56.1.0


However with ffmpeg-2.8.6 (shared) in 14.04 it will configure & build - 
> checking for ffmpeg... yes
..clipped
gcc -g -O2 -mtune=generic    -o comskip-gui comskip_gui-comskip.o comskip_gui-mpeg2dec.o comskip_gui-platform.o comskip_gui-video_out_dx.o ccextratorwin/comskip_gui-608.o ccextratorwin/comskip_gui-ccextractor.o ccextratorwin/comskip_gui-encoding.o ccextratorwin/comskip_gui-general_loop.o ccextratorwin/comskip_gui-myth.o comskip_gui-video_out_sdl.o -largtable2   -lavutil-ffmpeg -lavformat-ffmpeg -lavcodec-ffmpeg   -lSDL    -lpthread -lm 

So whatever you did to get it to find compatible ffmpeg libs was wrong. While the source's configure.log isn't very verbose if you open it, search ffmpeg & post the found versions it may be informative as to what you've done.

If you wish to remain on 14.04 this should be do-able though you'd need newer ffmpeg, either from a ppa as shared or self built as static, you cannot use the build from the multimedia ppa.
(- among other reasons it statically links to a newer vpx 
So while with an export it would use those headers in /opt it would fail on vpx - 
> gcc -g -O2 -mtune=generic    -o comskip comskip-comskip.o comskip-mpeg2dec.o comskip-platform.o comskip-video_out_dx.o ccextratorwin/comskip-608.o ccextratorwin/comskip-ccextractor.o ccextratorwin/comskip-encoding.o ccextratorwin/comskip-general_loop.o ccextratorwin/comskip-myth.o -largtable2   -pthread -L/opt/ffmpeg/lib -L/build/ffmpeg-Gwtx8e/ffmpeg-3.1.1~trusty/build_libs/lib -lavformat -lavcodec -lXv -lXext -lvdpau -lva-drm -lva-x11 -lva -lxcb-shm -lxcb-xfixes -lxcb-render -lxcb-shape -lxcb -lX11 -lasound -lSDL -lxvidcore -lx265 -lx264 -lpthread -lvpx -lvorbisenc -lvorbis -logg -lvidstab -lspeex -lpulse -lopus -lopencore-amrwb -lopencore-amrnb -lmp3lame -lfreetype -lfdk-aac -lass -lgnutls -lbz2 -lz -ldl -lswresample -lsoxr -lavutil -lm    -lpthread -lm 
/usr/bin/ld: cannot find -lvpx
collect2: error: ld returned 1 exit status

---

### Post by NotQuiteSU on 2016-09-14
Thank you for the very diligent explanation. I think I'll make the cut to 16. The debate will be a clean install or uprade

---

### Post by #&amp;thj^% on 2016-09-14
> **NotQuiteSU said:**
> Thank you for the very diligent explanation. I think I'll make the cut to 16. The debate will be a clean install or uprade
If I may make a bold suggestion here...A Clean Install insures a better experience for you. Lots of threads here with problems with upgrading.:)
And just a reminder for proper back-ups.

---

