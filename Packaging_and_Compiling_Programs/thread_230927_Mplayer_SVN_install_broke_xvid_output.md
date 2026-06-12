---
title: "Mplayer SVN install broke xvid output"
date: 2006-08-06
forum: Packaging and Compiling Programs
---

### Post by mikeym on 2006-08-06
Hi,

I have been trying to install mplayer from the SVN following [this guide]("http://www.ubuntuforums.org/showthread.php?t=187709") and I managed to get it installed, but when I came to try and use mencoder to encode a xvid file I found that the xvid codec ouput was gone. :/

The input codec was still there in mplayer and it would play xvid files.

So I went back and got the output from my call to ./configure and it tells me that xvid video output is enabled????? :confused: 

```
$./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --enable-theora --confdir=/etc/mplayer --with-win32libdir=/usr/lib/win32 --enable-menu --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa --enable-xvid --enable-x264 --disable-runtime-cpudetection
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.0.3, ok
Checking for host cc ... cc
Checking for cross compilation ... no
Checking for CPU vendor ... AuthenticAMD (6:3:1)
Checking for CPU type ...  AMD Duron(tm) processor
Checking for GCC & CPU optimization abilities ... athlon
Checking for kernel support of mmx ... yes
Checking for kernel support of mmxext ... yes
Checking for kernel support of 3dnow ... yes
Checking for kernel support of 3dnowext ... yes
Checking for mtrr support ... yes
Checking for mm3dnow.h ... yes
Checking for assembler support of -pipe option ... yes
Checking for assembler (as 2.16.91) ... ok
Checking for Linux kernel version ... 2.6.15-26-386, ok
Checking for MPlayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for -lposix ... no
Checking for -lm ... yes
Checking for langinfo ... yes
Checking for language ... using en (man pages:  en)
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... __restrict
Checking for __builtin_expect ... yes
Checking for kstat ... no
Checking for posix4 ... no
Checking for lrintf ... yes
Checking for round ... yes
Checking for nanosleep ... yes
Checking for socklib ... yes (using -lnsl)
Checking for inet_pton() ... yes (using -lnsl)
Checking for inttypes.h (required) ... yes
Checking for int_fastXY_t in inttypes.h ... yes
Checking for word size ... 32
Checking for stddef.h ... yes
Checking for malloc.h ... yes
Checking for memalign() ... yes
Checking for alloca.h ... yes
Checking for mman.h ... yes
Checking for dynamic loader ... yes
Checking for dynamic a/v plugins support ... no
Checking for pthread ... yes (using -lpthread)
Checking for rpath ... no
Checking for iconv ... yes
Checking for sys/soundcard.h ... yes
Checking for sys/dvdio.h ... no
Checking for sys/cdio.h ... no
Checking for linux/cdrom.h ... yes
Checking for dvd.h ... no
Checking for termcap ... yes (using -lncurses)
Checking for termios ... yes (using sys/termios.h)
Checking for shm ... yes
Checking for linux devfs ... no
Checking for scandir() ... yes
Checking for strsep() ... yes
Checking for strlcpy() ... no
Checking for strlcat() ... no
Checking for fseeko() ... yes
Checking for localtime_r() ... yes
Checking for vsscanf() ... yes
Checking for swab() ... yes
Checking for POSIX select() ... yes
Checking for gettimeofday() ... yes
Checking for glob() ... yes
Checking for setenv() ... yes
Checking for sys/sysinfo.h ... yes
Checking for Samba support (libsmbclient) ... no
Checking for 3dfx ... no
Checking for tdfxfb ... no
Checking for s3fb ... no
Checking for tdfxvid ... no
Checking for tga ... yes
Checking for DirectFB ... no
Checking for X11 headers presence ... yes (using /usr/include)
Checking for X11 ... yes (using /usr/X11R6/lib)
Checking for DPMS ... yes (using Xdpms 4)
Checking for Xv ... yes
Checking for XvMC ... no
Checking for Xinerama ... yes
Checking for Xxf86vm ... no
Checking for XF86keysym ... yes
Checking for DGA ... no
Checking for OpenGL ... yes
Checking for /dev/mga_vid ... no
Checking for xmga ... no
Checking for GGI ... no
Checking for GGI extension: libggiwmh ... no
Checking for AA ... no
Checking for CACA ... yes
Checking for SVGAlib ... no
Checking for FBDev ... yes
Checking for DVB ... no
Checking for DVB HEAD ... yes
Checking for PNG support ... yes
Checking for JPEG support ... yes
Checking for PNM support ... yes
Checking for GIF support ... no
Checking for VESA support ... no
Checking for SDL ... yes (using sdl-config)
Checking for NAS ... yes
Checking for DXR2 ... no
Checking for DXR3/H+ ... no
Checking for IVTV TV-Out ... no
Checking for libfame ... no
Checking for OSS Audio ... yes
Checking for aRts ... no
Checking for EsounD ... yes
Checking for esd_get_latency() ... yes
Checking for Polyp ... no
Checking for JACK ... no
Checking for OpenAL ... no
Checking for ALSA audio ... yes (using alsa 1.0.x and alsa/asoundlib.h)
Checking for Sun audio ... no
Checking for VCD support ... yes
Checking for DVD support (libmpdvdkit2) ... yes
Checking for DVD support (libdvdread) ... no (disabled by libmpdvdkit2)
Checking for DVD support (libdvdnav) ... no
Checking for cdparanoia ... no
Checking for libcdio ... no
Checking for freetype >= 2.0.9 ... yes
Checking for fontconfig ... yes
Checking for SSA/*** support ... yes
Checking for fribidi with charsets ... no
Checking for ENCA ... no
Checking for zlib ... yes
Checking for RTC ... yes
Checking for external liblzo support ... no
Checking for mad support ... yes
Checking for Toolame ... no
Checking for Twolame ... no
Checking for OggVorbis support ... yes (internal Tremor)
Checking for libspeex (version >= 1.1 required) ... no
Checking for OggTheora support ... yes
Checking for mp3lib support ... yes
Checking for liba52 support ... yes
Checking for libdts support ... yes
Checking for libmpeg2 support ... yes
Checking for libmpcdec (musepack, version >= 1.2.1 required) ... yes
Checking for FAAC (AAC encoder) support ... yes
Checking for FAAD2 (AAC) support ... yes
Checking for LADSPA plugin support ... no
Checking for Win32 codec DLL support ... yes (using /usr/lib/win32)
Checking for Win32 loader support ... yes
Checking for XAnim DLL ... yes (using /usr/lib/codecs)
Checking for RealPlayer DLL ... yes (using /usr/lib/codecs)
Checking for LIVE555 Streaming Media libraries ... no
Checking for FFmpeg libavutil (static) ... yes
Checking for FFmpeg libavcodec (static) ... yes
Checking for FFmpeg libavformat (static) ... yes
Checking for FFmpeg libpostproc (static) ... yes
Checking for md5sum support ... yes
Checking for AMR narrowband ... no
Checking for AMR narrowband, fixed point ... no
Checking for AMR wideband ... no
Checking for libdv-0.9.5+ ... no
Checking for zr ... no
Checking for bl ... no
[COLOR="Red"][B]Checking for XviD ... yes
Checking for XviD two pass plugin ... yes[/B][/COLOR]
Checking for DivX4 compatibility in XviD ... no
Checking for x264 ... yes
Checking for libmp3lame (for mencoder) ... yes
[COLOR="Red"]**Checking for mencoder ... yes**[/COLOR]
Checking for fastmemcpy ... yes
Checking for UniquE RAR File Library ... yes
Checking for TV interface ... yes
Checking for Video 4 Linux TV interface ... yes
Checking for Video 4 Linux 2 TV interface ... yes
Checking for Video 4 Linux 2/IVTV PVR interface ... no
Checking for audio select() ... yes
Checking for network ... yes
Checking for ftp ... yes
Checking for vstream client ... no
Checking for byte order ... little-endian
Checking for OSD menu ... yes
Checking for QuickTime codecs ... yes
Checking for Subtitles sorting ... yes
Checking for XMMS inputplugin support ... no
Checking for inet6 ... yes
Checking for gethostbyname2 ... yes
Checking for GUI ... yes
Checking for XShape extension ... yes
Checking for GTK+ version ... 2.8.20
Checking for glib version ... 2.10.3
Checking for iconv program ... yes
Checking for automatic gdb attach ... no
Checking for compiler support for -fno-PIC ... yes
Checking for compiler support for noexecstack ... yes
Checking for ftello() ... yes
Checking for VIDIX (internal) ... yes
Checking for VIDIX (external) ... no
Checking for joystick ... no
Checking for lirc ... no
Checking for lircc ... no
Creating config.mak
Creating config.h

Config files successfully generated by ./configure !

  Install prefix: /usr
  Data directory: /usr/share/mplayer
  Config direct.: /etc/mplayer

  Byte order: little-endian
  Optimizing for: athlon mmx mmxext 3dnow 3dnowext mtrr

  Languages:
    Messages/GUI: en
    Manual pages:  en

  Enabled optional drivers:
    Input: ftp network tv-v4l2 tv-v4l tv mpdvdkit2 vcd dvb
    Codecs: qtx x264 xvid libavcodec real xanim win32 faad2 faac musepack libmpeg2 libdts liba52 mp3lib libtheora tremor(internal) libmad
    Audio output: alsa esd oss nas sdl mpegpes(dvb)
    [COLOR="Red"]**Video output: xvidix**[/COLOR] cvidix md5sum sdl pnm jpeg png mpegpes(dvb) fbdev caca opengl xv x11 xover tga
    Audio filters:
  Disabled optional drivers:
    Input: vstream pvr live555 cdda dvdnav dvdread smb
    Codecs: libdv amr_wb amr_nb speex twolame toolame liblzo gif
    Audio output: sun openal jack polyp arts ivtv dxr2
    Video output: winvidix bl zr zr2 ivtv dxr3 dxr2 vesa gif89a svga aa ggi xmga mga dga xvmc directfb tdfx_vid s3fb tdfxfb 3dfx
    Audio filters: ladspa


```

But here is the output from mencoder:

```

$mencoder -ovc help
MEncoder dev-SVN-r19335-4.0.3 (C) 2000-2006 MPlayer Team
CPU: AMD Duron(tm) processor (Family: 6, Model: 3, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx


Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   x264     - H.264 encodin

```

Do you know how I can fix this?

---

### Post by mikeym on 2006-08-09
Hi,

I have now downloaded the latest SVN code and installed it. This seems to have fixed my problem.

The mencoder build I was having problems with was:

```
MPlayer dev-SVN-r19335-4.0.3 (C) 2000-2006 MPlayer Team

```

---

