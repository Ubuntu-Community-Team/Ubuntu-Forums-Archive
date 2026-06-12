---
title: "Mplayer - compilation problem"
date: 2005-01-06
forum: Packaging and Compiling Programs
---

### Post by NEtX on 2005-01-06
Hi,

today i tried to compile mplayer with the install script ([http://ubuntuforums.org/showthread.php?p=41911&highlight=Checking+cc+version#post41911](http://ubuntuforums.org/showthread.php?p=41911&highlight=Checking+cc+version#post41911)) , but i've had an error i couldn't solve by myself.

```

(after ./configure --enable-gui)

Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 3.3.4, ok
Checking for host cc ... cc
Checking for CPU vendor ... AuthenticAMD (6:10:0)
Checking for CPU type ...  AMD Athlon(tm) XP 3200+
Checking for GCC & CPU optimization abilities ... athlon-4
Checking for kernel support of mmx ... yes
Checking for kernel support of mmx2 ... yes
Checking for kernel support of 3dnow ... yes
Checking for kernel support of 3dnowex ... yes
Checking for kernel support of sse ... yes
Checking for mtrr support ... yes
Checking for assembler support of -pipe option ... yes
Checking for assembler (as 2.14.90.0.7) ... ok
Checking for Linux kernel version ... 2.6.8.1-3-386, ok
Checking for mplayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for -lposix ... no
Checking for -lm ... yes
Checking for i18n ... yes
Checking for setlocale() ... yes
Checking for iconv ... yes
Checking for langinfo ... yes
Checking for language ... using en (man pages:  en)
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... __restrict
Checking for __builtin_expect ... yes
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
Checking for termcap ... no
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
Checking for posix select() ... yes
Checking for gettimeofday() ... yes
Checking for glob() ... yes
Checking for sys/sysinfo.h ... yes
Checking for Mac OS X APIs ... no
Checking for Mac OS X Finder Support ... no
Checking for Samba support (libsmbclient) ... no
Checking for 3dfx ... no
Checking for tdfxfb ... no
Checking for tdfxvid ... no
Checking for tga ... yes
Checking for DirectFB headers presence ... not found
Checking for DirectFB ... no
Checking for X11 headers presence ... not found (check if the dev(el) packages are installed)
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
Checking for AA ... no
Checking for CACA ... no
Checking for SVGAlib ... no
Checking for FBDev ... no
Checking for DVB ... no (specify path to DVB/ost/include with --with-dvbincdir=DIR)
Checking for DVB HEAD ... yes
Checking for PNG support ... no
Checking for JPEG support ... no
Checking for PNM support ... yes
Checking for md5sum support ... yes
Checking for GIF support ... no
Checking for VESA support ... yes
Checking for SDL ... no
Checking for Windows waveout ... no
Checking for Directx ... no
Checking for NAS ... no
Checking for DXR2 ... no
Checking for DXR3/H+ ... no
Checking for libmp1e ... no
Checking for libfame ... no
Checking for OSS Audio ... yes
Checking for aRts ... no
Checking for EsounD ... no
Checking for Polyp ... no
Checking for JACK ... no
Checking for ALSA audio ... no
Checking for Sun audio ... no
Checking for Sun mediaLib ... no
Checking for SGI audio ... no
Checking for VCD support ... ok
Checking for DVD support (libmpdvdkit) ... yes
Checking for DVD support (libdvdread) ... disabled by libmpdvdkit2
Checking for cdparanoia ... no
Checking for freetype >= 2.0.9 ... no
Checking for fontconfig ... no
Checking for fribidi with charsets ... no
Checking for ENCA ... no
Checking for zlib ... no
Checking for RTC ... yes
Checking for external liblzo support ... no
Checking for mad support ... no
Checking for Toolame ... no
Checking for OggVorbis support ... no
Checking for OggTheora support (only the CVS version!) ... no
Checking for mp3lib support ... yes
Checking for liba52 support ... yes
Checking for libdts support ... no
Checking for libmpeg2 support ... yes
Checking for Matroska support ... yes
Checking for internal FAAD2 (AAC) support ... yes
Checking for external FAAD2 (AAC) support ... no
Checking for FAAD2 version ... 2.1 beta
Checking for LADSPA plugin support ... no
Checking for Win32 codec DLL support ... yes (using /usr/local/lib/codecs)
Checking for Win32 loader support ... yes
Checking for DirectShow ... yes
Checking for XAnim DLL ... yes (using /usr/local/lib/codecs)
Checking for RealPlayer DLL ... yes (using /usr/local/lib/codecs)
Checking for LIVE.COM Streaming Media libraries ... no
Checking for FFmpeg libavcodec (static) ... yes
Checking for FFmpeg libavformat (static) ... yes
Checking for libdv-0.9.5+ ... no
Checking for zr ... no
Checking for bl ... no
Checking for XviD ... no
Checking for x264 ... no
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
Checking for byte order ... little-endian
Checking for shared postprocess lib ... no
Checking for OSD menu ... no
Checking for QTX codecs ... yes
Checking for Subtitles sorting ... yes
Checking for XMMS inputplugin support ... no
Checking for inet6 ... yes
Checking for gethostbyname2 ... yes
Checking for GUI ... yes

Error: PNG support required for GUI compilation, please install libpng and libpng-dev packages.


```

I tried to install the missing packages, but they are not availiable at apt-get.

Thanks for helping,
Nikolaus

---

### Post by tiiim on 2005-01-06
[QUOTE=NEtX]Hi,

today i tried to compile mplayer with the install script ([http://ubuntuforums.org/showthread.php?p=41911&highlight=Checking+cc+version#post41911](http://ubuntuforums.org/showthread.php?p=41911&highlight=Checking+cc+version#post41911)) , but i've had an error i couldn't solve by myself.

```

(after ./configure --enable-gui)

Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 3.3.4, ok
Checking for host cc ... cc
Checking for CPU vendor ... AuthenticAMD (6:10:0)
Checking for CPU type ...  AMD Athlon(tm) XP 3200+
Checking for GCC & CPU optimization abilities ... athlon-4
Checking for kernel support of mmx ... yes
Checking for kernel support of mmx2 ... yes
Checking for kernel support of 3dnow ... yes
Checking for kernel support of 3dnowex ... yes
Checking for kernel support of sse ... yes
Checking for mtrr support ... yes
Checking for assembler support of -pipe option ... yes
Checking for assembler (as 2.14.90.0.7) ... ok
Checking for Linux kernel version ... 2.6.8.1-3-386, ok
Checking for mplayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for -lposix ... no
Checking for -lm ... yes
Checking for i18n ... yes
Checking for setlocale() ... yes
Checking for iconv ... yes
Checking for langinfo ... yes
Checking for language ... using en (man pages:  en)
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... __restrict
Checking for __builtin_expect ... yes
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
Checking for termcap ... no
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
Checking for posix select() ... yes
Checking for gettimeofday() ... yes
Checking for glob() ... yes
Checking for sys/sysinfo.h ... yes
Checking for Mac OS X APIs ... no
Checking for Mac OS X Finder Support ... no
Checking for Samba support (libsmbclient) ... no
Checking for 3dfx ... no
Checking for tdfxfb ... no
Checking for tdfxvid ... no
Checking for tga ... yes
Checking for DirectFB headers presence ... not found
Checking for DirectFB ... no
Checking for X11 headers presence ... not found (check if the dev(el) packages are installed)
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
Checking for AA ... no
Checking for CACA ... no
Checking for SVGAlib ... no
Checking for FBDev ... no
Checking for DVB ... no (specify path to DVB/ost/include with --with-dvbincdir=DIR)
Checking for DVB HEAD ... yes
Checking for PNG support ... no
Checking for JPEG support ... no
Checking for PNM support ... yes
Checking for md5sum support ... yes
Checking for GIF support ... no
Checking for VESA support ... yes
Checking for SDL ... no
Checking for Windows waveout ... no
Checking for Directx ... no
Checking for NAS ... no
Checking for DXR2 ... no
Checking for DXR3/H+ ... no
Checking for libmp1e ... no
Checking for libfame ... no
Checking for OSS Audio ... yes
Checking for aRts ... no
Checking for EsounD ... no
Checking for Polyp ... no
Checking for JACK ... no
Checking for ALSA audio ... no
Checking for Sun audio ... no
Checking for Sun mediaLib ... no
Checking for SGI audio ... no
Checking for VCD support ... ok
Checking for DVD support (libmpdvdkit) ... yes
Checking for DVD support (libdvdread) ... disabled by libmpdvdkit2
Checking for cdparanoia ... no
Checking for freetype >= 2.0.9 ... no
Checking for fontconfig ... no
Checking for fribidi with charsets ... no
Checking for ENCA ... no
Checking for zlib ... no
Checking for RTC ... yes
Checking for external liblzo support ... no
Checking for mad support ... no
Checking for Toolame ... no
Checking for OggVorbis support ... no
Checking for OggTheora support (only the CVS version!) ... no
Checking for mp3lib support ... yes
Checking for liba52 support ... yes
Checking for libdts support ... no
Checking for libmpeg2 support ... yes
Checking for Matroska support ... yes
Checking for internal FAAD2 (AAC) support ... yes
Checking for external FAAD2 (AAC) support ... no
Checking for FAAD2 version ... 2.1 beta
Checking for LADSPA plugin support ... no
Checking for Win32 codec DLL support ... yes (using /usr/local/lib/codecs)
Checking for Win32 loader support ... yes
Checking for DirectShow ... yes
Checking for XAnim DLL ... yes (using /usr/local/lib/codecs)
Checking for RealPlayer DLL ... yes (using /usr/local/lib/codecs)
Checking for LIVE.COM Streaming Media libraries ... no
Checking for FFmpeg libavcodec (static) ... yes
Checking for FFmpeg libavformat (static) ... yes
Checking for libdv-0.9.5+ ... no
Checking for zr ... no
Checking for bl ... no
Checking for XviD ... no
Checking for x264 ... no
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
Checking for byte order ... little-endian
Checking for shared postprocess lib ... no
Checking for OSD menu ... no
Checking for QTX codecs ... yes
Checking for Subtitles sorting ... yes
Checking for XMMS inputplugin support ... no
Checking for inet6 ... yes
Checking for gethostbyname2 ... yes
Checking for GUI ... yes

Error: PNG support required for GUI compilation, please install libpng and libpng-dev packages.


```

I tried to install the missing packages, but they are not availiable at apt-get.

Thanks for helping,
Nikolaus[/QUOTE]
 have you got the universe sources under /etc/apt/sources.list?

if not as root open that file.

ie. sudo nano /etc/apt/sources.list 

scroll down the page and decomment the two sources links that have been comment out by the Ubuntu team. save file.

Then apt-get update or whatever it is or spm refresh buttom then the files should be there to download.

---

### Post by NEtX on 2005-01-06
Thanks for the tip, but I've already done this. Instead I wouldn't have been able to install the other depolver tools with apt-get.

Thats my sources.list

```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://archive.ubuntu.com/ubuntu warty main restricted
# deb-src http://archive.ubuntu.com/ubuntu warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu warty universe
deb-src http://archive.ubuntu.com/ubuntu warty universe

deb http://security.ubuntu.com/ubuntu warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu warty-security main restricted
```

do I've to add some sources?

---

### Post by tiiim on 2005-01-06
[QUOTE=NEtX]Thanks for the tip, but I've already done this. Instead I wouldn't have been able to install the other depolver tools with apt-get.

Thats my sources.list

```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://archive.ubuntu.com/ubuntu warty main restricted
# deb-src http://archive.ubuntu.com/ubuntu warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu warty universe
deb-src http://archive.ubuntu.com/ubuntu warty universe

deb http://security.ubuntu.com/ubuntu warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu warty-security main restricted
```

do I've to add some sources?[/QUOTE]
 why the top 2 comment lines commented i think you can uncomment those sources as well cos they are standard

---

### Post by fng on 2005-01-06
```
fng@butters:~ $ sudo apt-cache search libpng
libpng-dylan - Support for PNG display in Gwydion Dylan (Native)
libpng-sixlegs-java - Java package to read and display PNG images
gdk-imlib1 - imaging library for use with gtk (using libpng2)
gdk-imlib1-dev - Header files needed for Gdk-Imlib development (using libpng2)
imlib1 - imaging library for X and X11 (using libpng2)
imlib1-dev - Header files needed for Imlib development (using libpng2)
libpng10-0 - PNG library, older version - runtime
libpng10-dev - PNG library, older version - development
libpng12-0 - PNG library - runtime
libpng12-dev - PNG library - development
libpng2-dev - PNG library, older version - development
libpng3-dev - PNG library - development, compatibility package
libpng2 - PNG library, older version - runtime
libpng3 - PNG library - runtime
fng@butters:~ $

``` 

I would go for  : 
libpng12-0 - PNG library - runtime
libpng12-dev - PNG library - development

They are in wart/main, so you really need to uncomment those 2 lines tiim said

---

### Post by tiiim on 2005-01-06
[QUOTE=fng]```
fng@butters:~ $ sudo apt-cache search libpng
libpng-dylan - Support for PNG display in Gwydion Dylan (Native)
libpng-sixlegs-java - Java package to read and display PNG images
gdk-imlib1 - imaging library for use with gtk (using libpng2)
gdk-imlib1-dev - Header files needed for Gdk-Imlib development (using libpng2)
imlib1 - imaging library for X and X11 (using libpng2)
imlib1-dev - Header files needed for Imlib development (using libpng2)
libpng10-0 - PNG library, older version - runtime
libpng10-dev - PNG library, older version - development
libpng12-0 - PNG library - runtime
libpng12-dev - PNG library - development
libpng2-dev - PNG library, older version - development
libpng3-dev - PNG library - development, compatibility package
libpng2 - PNG library, older version - runtime
libpng3 - PNG library - runtime
fng@butters:~ $

``` 

I would go for  : 
libpng12-0 - PNG library - runtime
libpng12-dev - PNG library - development

They are in wart/main, so you really need to uncomment those 2 lines tiim said[/QUOTE]
 try uncomment those other sources see if you can download it then if not if you look on Debians side under their pool you can download them packages indiviual there.

---

### Post by kleeman on 2005-01-06
Looks like you don't have the libpng and libpng-devel packages installed. I opened up synaptic and searched for these and found they were called actually called linpng10-0 and libpng12-0 so this might explain why apt-get failed. If this is so just follow my steps with synaptic and install all the packages including the devel ones.

---

### Post by NEtX on 2005-01-06
I just had to comment the sources out and it worked. Very stupid mistake. I just didn't see them.

Thanks for helping!

---

### Post by dikki on 2005-02-01
I read this, and the HOWTO, too. I installed the libpng12-0 and linpng12-dev packages _for sure_ , but I get the error message again.

I tried to install the libpng from source before apt-get (I didn't know that their name is libpng12-0 etc) maybe that's the problem?

I'm gettin annoyed, I can't install that mplayer with GUI-support. And xchat, neither.

---

### Post by dikki on 2005-02-02
Well, I got it: the installing from source was the problem. I deleted everything in /usr called libpng*, and after an apt-get install libpng12-0 libpng12-dev --reinstall everything works fine. Thanks!

---

### Post by bingo11 on 2005-02-22
Thans y'all for the great tips.

I am fairly new to linux and i had the same problem. It took me 5 hours to find this thread and 1 hour to understand it..... still dosen't work.

here is the message i get when trying "sudo apt-get install libpng12-dev"

The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libpng12-dev: Depends: libpng12-0 (= 1.2.5.0-7) but 1.2.5.0-7ubuntu1 is to be installed
E: Broken packages


my /etc/apt/sources.list looks like this 

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ uns$

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

Any help would be highly appreciated

PS: I am a starter so please don't ask me to re-compile a kernel ou reinstall a Glibc :)

Madi

---

### Post by gasparov on 2005-02-24
[QUOTE=bingo11]Thans y'all for the great tips.

I am fairly new to linux and i had the same problem. It took me 5 hours to find this thread and 1 hour to understand it..... still dosen't work.

here is the message i get when trying "sudo apt-get install libpng12-dev"

The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libpng12-dev: Depends: libpng12-0 (= 1.2.5.0-7) but 1.2.5.0-7ubuntu1 is to be installed


Madi[/QUOTE]
 Hi,
   apt-get doesn't work even for me for the same reason, however mplayer folks suggest to install it by end, even if it takes long is much better .
If you'll do this way I'd suggest you to take a look on configure option, in this how-to is suggested to run ./configure --enable-gui, other things could be added to prevent later "ball breaking" situations, for example --enable-alsa, --enable-lame.....
Right now I cannot use alsa cause i didn't do the trick above , I was advised at the end of "make" that alsa output was ignored, I haven't figure out how to enable it without rebuilding yet...

P.S. ./configure,make,sudo make install are the only things to get used to, considering the kernel you have to add a text editor and lilo/grub in you knowledge :), is not so diffcult using linux....

---

### Post by gila on 2005-02-25
Hi,

I compiled mplayer in the following way.

First i added the deb-src from the universe and multiverse. (note i'm running the beta!!)

Afther that make apt do all the work for you :) Long live the pkg manager.

apt-get build-dep mplayer

apt-get source mplauyer

Then i trided to build the .deb file which did not work, so I editted the rules file thats in mplayer-VERSION/debian. (Had the rip out the 3dfx stuff)

Then its time to build the dep with 

apt-get -b source mplayer.


When all is done you will have several .deb's. Install the onces you like with

dpkg -i  PACKAGE_NAME.

The advantage with this is that you keep apt consistent.

---

