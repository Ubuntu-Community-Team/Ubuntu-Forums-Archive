---
title: "MPlayer compiling error"
date: 2006-01-05
forum: Packaging and Compiling Programs
---

### Post by no1pointguard on 2006-01-05
hey out there! i'm an ab absolute newbie with linux and ubuntu so i apologise for my lack of knowlege. been trying to install Mplayer didnt work through synaptic so was trying through terminal using instructions from ([http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt))
problem is when i get to
./configure --enable-gui

i get
Error: X11 support required for GUI compilation
can anyone help me fix this
many thanks!

---

### Post by Peter76 on 2006-01-05
you probably have to instal the x window dev files:
sudo apt-get install x-window-system-dev
or install the package through synaptic. Probably you also need the package build-essential. Most of the times when configure fails you need to install the .dev files of the package it thinks it's missing, but always check if the "normal" package is installed.

Good luck

---

### Post by no1pointguard on 2006-01-05
yeah have x window dev and essential-build but still having same problem :confused:

---

### Post by Peter76 on 2006-01-06
Can you post the complete output of ./configure?

---

### Post by no1pointguard on 2006-01-06
eddie@stuED8F:~/MPlayer-1.0pre5$ ./configure --enable-gui
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.0.2, bad
Checking for gcc version ... 4.0.2, bad
Checking for gcc-3.3 version ... 3.3.6, ok
Checking for CPU vendor ... CentaurHauls (6:7:3)
Checking for CPU type ...  VIA Samuel 2
Checking for GCC & CPU optimization abilities ... i586
Checking for kernel support of mmx ... yes
Checking for kernel support of 3dnow ... yes
Checking for mtrr support ... yes
Checking for assembler (as 2.16.1) ... ok
Checking for Linux kernel version ... 2.6.12-10-386, ok
Checking for mplayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for i18n ... yes
Checking for setlocale() ... yes
Checking for iconv ... yes
Checking for langinfo ... yes
Checking for language ... using en (man pages: en)
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... __restrict
Checking for kstat ... no
Checking for posix4 ... no
Checking for lrintf ... yes
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
Checking for sys/soundcard.h ... yes
Checking for sys/dvdio.h ... no
Checking for sys/cdio.h ... no
Checking for linux/cdrom.h ... yes
Checking for dvd.h ... no
Checking for BSDI dvd.h ... no
Checking for HPUX SCSI header ... no
Checking for userspace SCSI headers (Solaris) ... no
Checking for termcap ... yes (using -ltermcap)
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
Checking for posix select() ... yes
Checking for gettimeofday() ... yes
Checking for glob() ... yes
Checking for sys/sysinfo.h ... yes
Checking for Mac OS X APIs ... no
Checking for Samba support (libsmbclient) ... no
Checking for 3dfx ... no
Checking for tdfxfb ... no
Checking for tdfxvid ... no
Checking for tga ... yes
Checking for DirectFB headers presence ... not found
Checking for DirectFB ... no
Checking for X11 headers presence ... yes (using /usr/include)
Checking for X11 libs presence ... not found (check if the dev(el) packages are installed)
Checking for X11 ... no
Checking for DPMS ... no
Checking for Xv ... no
Checking for XvMC ... no
Checking for Xinerama ... no
Checking for Xxf86vm ... no
Checking for DGA ... no
Checking for OpenGL ... no
Checking for /dev/mga_vid ... no
Checking for xmga ... no
Checking for GGI ... no
Checking for AA ... yes
Checking for CACA ... no
Checking for SVGAlib ... no
Checking for FBDev ... yes
Checking for DVB ... no (specify path to DVB/ost/include with --with-dvbincdir=DIR)
Checking for DVB HEAD ... yes
Checking for PNG support ... yes
Checking for JPEG support ... yes
Checking for GIF support ... no
Checking for VESA support ... yes
Checking for SDL ... yes (using sdl-config)
Checking for Windows waveout ... no
Checking for Directx ... no
Checking for NAS ... yes
Checking for DXR2 ... no
Checking for DXR3/H+ ... no
Checking for libmp1e ... no
Checking for libfame ... no
Checking for OSS Audio ... yes
Checking for aRts ... yes
Checking for EsounD ... yes
Checking for esd_get_latency() ... yes
Checking for JACK ... no
Checking for ALSA audio ... yes (using alsa 1.0.x and alsa/asoundlib.h)
Checking for Sun audio ... no
Checking for Sun mediaLib ... no
Checking for SGI audio ... no
Checking for VCD support ... ok
Checking for DVD support (libmpdvdkit) ... yes
Checking for DVD support (libdvdread) ... disabled by libmpdvdkit2
Checking for cdparanoia ... no
Checking for freetype >= 2.0.9 ... yes
Checking for fontconfig ... no
Checking for fribidi with charsets ... no
Checking for ENCA ... no
Checking for zlib ... yes
Checking for RTC ... yes
Checking for external liblzo support ... no
Checking for mad support ... no
Checking for OggVorbis support ... no
Checking for OggTheora support (only the CVS version!) ... no
Checking for mp3lib support ... yes
Checking for liba52 support ... yes
Checking for libmpeg2 support ... yes
Checking for Matroska support (external 0.6.0 or later OR internal) ... yes, internal
Checking for internal FAAD2 (AAC) support ... yes
Checking for external FAAD2 (AAC) support ... no
Checking for FAAD2 version ... 2.0
Checking for MacOS X SHLB (shared lib) support ... no
Checking for Win32 codec DLL support ... yes (using /usr/local/lib/codecs)
Checking for Win32 loader support ... yes
Checking for DirectShow ... yes
Checking for XAnim DLL ... yes (using /usr/local/lib/codecs)
Checking for RealPlayer DLL ... yes (using /usr/local/lib/codecs)
Checking for LIVE.COM Streaming Media libraries ... no
Checking for FFmpeg libavcodec (static) ... yes
Checking for FFmpeg libavformatc (static) ... no
Checking for libdv-0.9.5+ ... yes
Checking for zr ... no
Checking for bl ... no
Checking for XviD ... no
Checking for DivX4linux/DivX5linux/OpenDivX decore ... no
Checking for libmp3lame (for mencoder) ... no
Checking for DivX4linux encore (for mencoder) ... no
Checking for mencoder ... yes
Checking for fastmemcpy ... yes
Checking for UniquE RAR File Library ... yes
Checking for TV interface ... yes
Checking for EDL support ... yes
Checking for *BSD BrookTree 848 TV interface ... no
Checking for Video 4 Linux TV interface ... no
Checking for Video 4 Linux 2 TV interface ... no
Checking for audio select() ... yes
Checking for network ... yes
Checking for ftp ... yes
Checking for byte order ... Little Endian
Checking for shared postprocess lib ... no
Checking for OSD menu ... no
Checking for QTX codecs ... yes
Checking for Subtitles sorting ... yes
Checking for XMMS inputplugin support ... no
Checking for inet6 ... yes
Checking for gethostbyname2 ... yes
Checking for GUI ... yes

Error: X11 support required for GUI compilation

Check "configure.log" if you do not understand why it failed.
eddie@stuED8F:~/MPlayer-1.0pre5$

---

### Post by mo_x on 2006-01-06
sudo apt-get libx11-dev libxv-dev

---

### Post by no1pointguard on 2006-01-06
yes ive got both of those but still have th same prob

---

### Post by Peter76 on 2006-01-06
The output from configure says it can't fin X11 libs. Like it says at the end, check configure.log to see if you can get any more info, or if you don't understand it, ppost it as well. My guess is that you have your X11 libs installed in another place than configure looks for it, or that they have another name than configure looks for  ( eg X11-2.3.7.so instead of X11.so or something like that. ) If you know where they are, you can tell configure where to look for them; type ./configure --help, this will give you the options to configure. If it's the naming problem, make a softlinks from your libs to the libs configure looks for. Good luck

---

### Post by mo_x on 2006-01-06
You are trying to compile 1.0pre5, the latest is 1.0pre7try2 (which I am running). Maybe you can give that one a try.

---

### Post by ggdhines on 2006-01-15
Alright, this post is slightly delayed but I figure it can't hurt.
Anyways, I was having the extact same problem (even after I included build-essentials). As the previous post suggested, going with 1.0pre7try2 is the way to fix the problem. As well, if you are using 5.10 (with gcc 4.x), you need to install 3.x (there is an option to override the configure error but if you do that than during make there is an error that pops up and can only be solved by using 3.x).

first time post - so hopefully everything I've said is correct
Greg

---

### Post by kerzane on 2006-12-04
I'm trying to program opengl on 6.10 and I think I need x-window-system-dev, but I can't find it under apt-get or synaptic. Story? Will a version for another distro do?

Thanks.

---

### Post by mo_x on 2006-12-04
Look in synaptic for xorg packages.

---

### Post by knair1 on 2007-02-15
I had the same error msg as no11pointguard:

Error: X11 support required for GUI compilation

I managed to fix it by installing the following packages

xorg-dev              (x windows devel kit)
libgtk2.0-dev      (gtk devel kit)

I'm new to Ubuntu, but I hope this helps someone.

Comedically, I don't really find myself using the GUI that much anyway.

Compiling from source makes me feel manly...

---

### Post by WaySensei on 2007-12-27
Before running ./configure, type sudo apt-get build-dep mplayer, this will install all the build dependencies.

---

