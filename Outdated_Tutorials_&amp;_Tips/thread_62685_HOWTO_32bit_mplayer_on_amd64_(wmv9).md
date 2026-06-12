---
title: "HOWTO: 32bit mplayer on amd64 (wmv9)"
date: 2005-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Conq on 2005-09-05
[COLOR=Red]UPDATE: I Have now made a package for Dapper Drake as well. See [http://ubuntuforums.org/showthread.php?t=62685](http://ubuntuforums.org/showthread.php?t=62685)[/COLOR]

I quick search through the forum suggested that there is quite a lot of confusion around the issue
of playing wmv9 files on amd64. I'll try to clarify and give you a way to play wmv9 on amd64 without resorting
to a chroot.

WMV9 is a closed format. There are no open source decoders available. Mplayer uses the closed source 32 bits
windows dll's to get around this issue. But a 64 bit mplayer cannot use 32 bit dll's. 

So - to get 32 bits dll's to work you need a 32 bit mplayer. But mplayer requires a lot of extra libraries, and they too have to be made 32 bits.

I have made a package that contains all the libraries and binaries (with the exception of the win32 codecs)

What you need to do to get things too work:

1. Download the essential codec package from "http://www.mplayerhq.hu/homepage/design7/dload.html"
2. Untar contents into /usr/lib/win32
3. Get the .deb from my website: 
    wget [http://www.stud.ntnu.no/~grannas/debs/mplayer32_1.0pre6-1_amd64.deb](http://www.stud.ntnu.no/~grannas/debs/mplayer32_1.0pre6-1_amd64.deb)
4. Install it:
    sudo dpkg -i mplayer32_1.0pre6-1_amd64.deb
5. Update ldconfig to make sure it gets the new libraries
    sudo ldconfig
6. Run mplayer32

The binary is called mplayer32 too avoid collisions with the binary from the "official" mplayer package.

NOTE: The package is a kludge, it has a lot of binaries and libraries from all over the place, it should 
be split up in many packages, but it's put in a single place
NOTE: The -vo:gl might break, I have nvidia on my system, this might break yours.
NOTE: If you are getting missing libraries, please make sure that you have installed the 32 bit compability
libraries 
[COLOR=Red]UPDATE[/COLOR]: The libraries are called  "ia32-libs-gtk" and "ia32-libs".
[COLOR=Red]UPDATE2:[/COLOR] If you want realmedia support - grab the "all" w32codecs instead of the essential package in step 1.
[COLOR=Red]UPDATE3:[/COLOR] In addition, you need "ia32-libs-openoffice.org"
[COLOR=Red]UPDATE4:[/COLOR] If you are using this package on Breezy, and experience no sound, you might want to try "ln -s /tmp/.esd-1000 /tmp/.esd"

---

### Post by tseliot on 2005-09-05
I can't try it right now (several problems with my RAM) but if this really solves the lack of wmv9 support in 64 bit systems you're GREAT.

---

### Post by tseliot on 2005-09-05
This thing happens to me:

alberto@ubuntu:~$ mplayer32 /home/alberto/daniel.wmv
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/alberto/daniel.wmv.
File not found: '/home/alberto/daniel.wmv'
Failed to open /home/alberto/daniel.wmv


And the file does exist. Any ideas?

---

### Post by Conq on 2005-09-06
Thats strange, do you have the same problem with all files?

---

### Post by tseliot on 2005-09-06
[QUOTE=Conq]Thats strange, do you have the same problem with all files?[/QUOTE]
Yes, I do. And I have the same problem with mplayer 64bit (I installed it after yours so as to see if one of them worked)

---

### Post by Conq on 2005-09-06
Try to cat the file directly into mplayer like this:

cat foo.wmv | mplayer - 

and see if that helps.

---

### Post by tseliot on 2005-09-06
I got this

cat: daniel.wmv: No such file or directory
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
Cannot test OS support for SSE, disabling to be safe.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing -.
Reading from stdin...
Cache fill:  0.00% (0 bytes)    XMMS: found plugin: libmpg123.so (MPEG Layer 1/2/3 Player 1.2.10)
XMMS: found plugin: libwav.so (Wave Player 1.2.10)
XMMS: found plugin: libmikmod.so (MikMod Player 1.2.10)
XMMS: found plugin: libcdaudio.so (CD Audio Player 1.2.10)
XMMS: found plugin: libtonegen.so (Tone Generator 1.2.10)
XMMS: found plugin: libvorbis.so (Ogg Vorbis Player 1.2.10)
XMMS: found plugin: libxmms-flac.so (Reference FLAC Player v1.1.1)
XMMS: found plugin: libxmmsmad.so (MAD MPEG Decoder plugin 0.7)
XMMS: found plugin: libmpg123-ja.so (MPEG Layer 1/2/3 Player 1.2.10j_20040302)
XMMS: Closing plugin /usr/lib/xmms/Input/libmpg123-ja.so
XMMS: Closing plugin /usr/lib/xmms/Input/libxmmsmad.so
XMMS: Closing plugin /usr/lib/xmms/Input/libxmms-flac.so
XMMS: Closing plugin /usr/lib/xmms/Input/libvorbis.so
XMMS: Closing plugin /usr/lib/xmms/Input/libtonegen.so
XMMS: Closing plugin /usr/lib/xmms/Input/libcdaudio.so
XMMS: Closing plugin /usr/lib/xmms/Input/libmikmod.so
XMMS: Closing plugin /usr/lib/xmms/Input/libwav.so
XMMS: Closing plugin /usr/lib/xmms/Input/libmpg123.so


Exiting... (End of file)

---

### Post by Conq on 2005-09-06
This is not a problem with the mplayer32 binary. You can't even cat the file. See if your filesystem
is corrupted or try another file.

---

### Post by tseliot on 2005-09-06
I agree with you. I'll try to solve the problem.

---

### Post by zupermanz on 2005-09-12
it works!...thanks!
Only one problem audio sync on live stream.... any ideas?

---

### Post by mlomker on 2005-09-13
Seen this one before?

```

root@mlomkernote:/home/mlomker/downloads # mplayer32
mplayer32: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

I've seen the error before but the file is there.

```

root@mlomkernote:/home/mlomker/downloads # locate libstdc++.so.5
/usr/lib/libstdc++.so.5
/usr/lib/vmware/lib/libstdc++.so.5
/usr/lib/vmware/lib/libstdc++.so.5/libstdc++.so.5
/usr/lib/libstdc++.so.5.0.7
/home/src/vmware-wk5/lib/lib/libstdc++.so.5
/home/src/vmware-wk5/lib/lib/libstdc++.so.5/libstdc++.so.5
root@mlomkernote:/home/mlomker/downloads #    

```

I wonder if it is related to the VMware install?  Could someone that has it working give me the output from:

```

root@mlomkernote:/home/mlomker/downloads # ls -l /usr/lib/libstdc++.so.5
lrwxrwxrwx  1 root root 18 2005-09-08 13:46 /usr/lib/libstdc++.so.5 -> libstdc++.so.5.0.7
root@mlomkernote:/home/mlomker/downloads # ls -l /usr/lib/libstdc++.so.5.0.7
-rw-r--r--  1 root root 832872 2005-02-10 17:14 /usr/lib/libstdc++.so.5.0.

```

---

### Post by Conq on 2005-09-13
Ahh, I forgot a dependancy, you need to
"sudo apt-get install ia32-libs-openoffice.org"

The other libs there are 64-bit libs, the 32-bit libs reside in either /lib32 or in /usr/lib32 :-)
I'll update the howto.

---

### Post by mlomker on 2005-09-14
[QUOTE=Conq]Ahh, I forgot a dependancy, you need to
"sudo apt-get install ia32-libs-openoffice.org"
[/QUOTE]

That changed the error message to a different file, which is progress.

```

root@mlomkernote:/etc/init.d # mplayer32
mplayer32: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

That file also exists and (according to apt-file) was included in ia32-libs.  The openoffice problem is because I removed it...wonder if the others are because I run Kubuntu?

**EDIT:**  Nevermind.  I had to do an **apt-get install --reinstall ia32-libs** for some reason.

---

### Post by gk_jam on 2005-11-08
Followed the howto, but when I tried to run mplayer32 I got this error:

```

mplayer32: error while loading shared libraries: libdrm.so.1: cannot open shared object file: No such file or directory

```

I did make sure to install the libs that were detailed. Any idea what this error is about and how to fix?

---

### Post by Conq on 2005-11-20
Have you tried to simply install the library libdrm1 (apt-get install libdrm1)?

---

### Post by domenic on 2005-12-01
hi, i'm a complete newbie, and would really like to play some sort of media files on my new ubuntu sys!!

I've a few questions. firstly if i install mplayer32 using dpkg should it appear in a menu somewhere?

since i couldn't find it anywhere else i had a look in synaptic for it, and it said it was installed.  i tried to reinstall it but it came up with an error saying it couldn't find the .deb file in file:///home/./

now it is possible that i may have moved the file since i first installed it.

Any suggestions?  If i wanted to uninstall and try again could i use synaptic or would i have to use dpkg and if so how??

any help would be greatly appreciated!!

---

### Post by chihuahuaskowbo on 2005-12-31
[QUOTE=Conq]Have you tried to simply install the library libdrm1 (apt-get install libdrm1)?[/QUOTE]

I've got the same problem, but libdrm1 was already installed.
I also noticed that I don't have a /usr/lib/win32 folder.  Could be connected somehow?
Any help appreciated.

---

### Post by Buenaventura Durruti on 2006-01-03
root@stallman:/home/fmmarzoa# mplayer32
mplayer32: error while loading shared libraries: libpng12.so.0: cannot open shared object file: No such file or directory
root@stallman:/home/fmmarzoa# ls -la /usr/lib/libpng12.so.*
lrwxrwxrwx  1 root root     19 2006-01-02 23:45 /usr/lib/libpng12.so.0 -> libpng12.so.0.1.2.8
-rw-r--r--  1 root root 161032 2005-08-22 18:52 /usr/lib/libpng12.so.0.1.2.8
root@stallman:/home/fmmarzoa# ldconfig
root@stallman:/home/fmmarzoa# mplayer32
mplayer32: error while loading shared libraries: libpng12.so.0: cannot open shared object file: No such file or directory 

The libraries seems to be right there. Unfortunatly, I cannot use ltrace over mplayer32 due architecture incompatiblities to do a deeper debug, but if someone knows what's happen without further information...

---

### Post by Buenaventura Durruti on 2006-01-03
The previous problem was solved just installing ia32-libs-gtk, for some reason I didn't see that package before but it appear after an apt update and then I could install it. Anyway I've another library missing problem now:

root@stallman:/etc# mplayer32
mplayer32: error while loading shared libraries: libdrm.so.1: cannot open shared object file: No such file or directory

I think I've now installed everything, so I do not figure out what's the problem.

---

### Post by Buenaventura Durruti on 2006-01-03
Ok, things can be done this way ([I got these ideas from this thread on skype]("http://www.ubuntuforums.org/showthread.php?p=475023#post475023")):

Download a 32bit version of libdrm, such as this:

[libdrm1_1.0.3-2_i386.deb]("http://packages.ubuntu.com/breezy/libs/libdrm1")

Extract its files, this can be done with dpkg like:

dpkg -x libdrm1_1.0.3-2_i386.deb .

(The last dot means that files will be extracted in current directory).

After that, you should have an 'usr' subdirectory below your current one. So if you do:

#ls usr/lib/

from your current directory, it should show:

libdrm.so.1  libdrm.so.1.0.0

Ok, now we'll move these files to our /usr/lib32 directory, in which mplayer32 expects find them, to do that:

mv usr/lib/* /usr/lib32

Now if you do a:

ls -l /usr/lib32/libdrm*

You should get:

lrwxrwxrwx  1 root root    15 2006-01-03 23:37 /usr/lib32/libdrm.so.1 -> libdrm.so.1.0.0
-rw-r--r--  1 root root 23032 2005-08-24 12:18 /usr/lib32/libdrm.so.1.0.0

Now just run ldconfig to update library cache:

ldconfig

And the problem with libdrm should be history. 

(Of course, the majority of these actions needs root priviledges, so you should need to log as root or use sudo in each step.)

---

### Post by Josef K. on 2006-02-11
great works!!! \\:D/

---

### Post by Mitush on 2006-02-21
ok, it looks like my mplayer32 does work in my amd64 Ubuntu. It plays wmv files, which are (most likely) wm9 encoding.

Now I am trying to watch movie trailers from yahoo.com using firefox-1.0.7. (I do have mplayer firefox plug-in installed.) I assume that the streaming movie clips there are in some form of WM9 encoding. The window which pops up shows mplayer plug-in loaded, but does not play the video, only the sound. I can guees that the plug-in is still 64 bit mplayer, and I could only make it to switch to use mplayer32 stuff...

What do I need to do to watch the trailers?

---

### Post by Conq on 2006-02-22
You don't have to guess to see if it plays a wmv9, while playing mplayer/mplayer32
outputs something like this:
Selected video codec: [wmv9dmo] vfm:dmo (Windows Media Video 9 DMO)

As for mplayerplug-in, I don't use it, but I'm guessing it is hardwired to the
/usr/bin/mplayer binary. Perhaps this is a configuration option? Or you could 
use a sledge and simply rename the two - eg mplayer and mplayer64.

---

### Post by Mitush on 2006-02-22
Thanks for replying. I did try renaming the executable but it didn't help. I guess one of the things which could help me is to understand what is a plug-in and/or how to manage them.

---

### Post by Mitush on 2006-02-22
It works as a plug-in after all. I opened a movie traler from yahoo and looked for processes running. Sure enough there was mplayer with a very long list of options. Deleted window id from the command line and, running from xterm with mplayer32, it shows me the streaming trailer in a separate window, both video and sound. Renamed the files and it worked inside the yahoo popup also! I guess I did something wrong with renaming the first time.

---

### Post by rastamufasta on 2006-03-29
I get this error when trying to install the openoffice.org libs.  I get the same error when I try to install mplayer32 after installing these libs.  


Unpacking ia32-libs-openoffice.org (from .../ia32-libs-openoffice.org_9_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs-openoffice.org_9_amd64.deb (--unpack):
 trying to overwrite `/usr/lib32/libgssapi_krb5.so.2.2', which is also in package mplayer32
dpkg-deb: subprocess paste killed by signal (Broken pipe)


Anyone know what I can do?  Thanks

---

### Post by Surfels on 2006-04-08
It works good. Thank you for the mplayer32. But I have a problem with wmv files from onlinetvrecorder.com. How can I watch these files in fullscreen?

---

### Post by Cashel on 2006-04-10
Hey! This package worked flawlessly for me on Breezy, in Dapper I'm getting:

# dpkg --force-all -i mplayer32_1.0pre6-1_amd64.deb
(Reading database ... 65557 files and directories currently installed.)
Unpacking mplayer32 (from mplayer32_1.0pre6-1_amd64.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/lib32/libcom_err.so.2.1', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libgssapi_krb5.so.2.2', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libk5crypto.so.3.0', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libkrb5.so.3.2', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/liblber.so.2.0.130', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libldap.so.2.0.130', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libsasl2.so.2.0.19', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/lib32/libcom_err.so.2', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libgcrypt.so.11', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libgpg-error.so.0', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libgssapi_krb5.so.2', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libk5crypto.so.3', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libkrb5.so.3', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/liblber.so.2', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libldap.so.2', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libsasl2.so.2', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libtasn1.so.2', which is also in package ia32-libs-openoffice.org
Setting up mplayer32 (1.0pre6-1) ...

# ldconfig
# mplayer32
mplayer32: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory

You said the openoffice libs were dependecies, so why should it want to overwrite them? 

At any rate, checking against breezy, it doesnt seem as if libncurses have been moved... 

I'll keep working on it tho... any help appreciated..

---

### Post by Spini on 2006-04-12
I guess I have the same problem with tseliot. When I try to open a wmv-file I get this:

mplayer32 video.wmv
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing video.wmv.
ASF file format detected.
VIDEO:  [WMV3]  640x480  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 8001->192000 (64.0 kbit)
Selected audio codec: [ffwmav2] afm:ffmpeg (DivX audio v2 (ffmpeg))
==========================================================================
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:921600  align:1
StreamCount r=0x0  1  1
Decoder supports the following YUV formats: YV12 YUY2 UYVY YVYU   
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 640 x 480 (preferred csp: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [3dfx] 640x480 => 640x480 Planar YV12
Couldn't open /dev/3dfx

After that the terminal crashes.

I'm a total newbie with linux so I have no idea where to start with this problem.


64-bit Ubuntu 5.10
AMD64 
NVIDIA geforce 6800le

Edit: Maybe this problem has something to do with that this HOWTO was written for Hoary Hedgehog 5.04 =)

ps. sorry about my bad English

---

### Post by smite on 2006-04-21
[QUOTE=Cashel]Hey! This package worked flawlessly for me on Breezy, in Dapper I'm getting:

# dpkg --force-all -i mplayer32_1.0pre6-1_amd64.deb
(Reading database ... 65557 files and directories currently installed.)
Unpacking mplayer32 (from mplayer32_1.0pre6-1_amd64.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/lib32/libcom_err.so.2.1', which is also in package ia32-libs-openoffice.org
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/lib32/libgssapi_krb5.so.2.2', which is also in package ia32-libs-openoffice.org
...
[/quote]
I wish someone with the required know-how made a dapper-specific version of the mplayer32 package, without this overlap with ia32-libs-openoffice.org.

> 
# ldconfig
# mplayer32
mplayer32: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory

This is fixed with
```
sudo apt-get install lib32ncurses5
```
only to get
```

mplayer32: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```
](*,)

---

### Post by richardjones on 2006-04-27
I'm stuck at the gtk-1.2 part too. I'm also running Dapper. 

It looks like the IA32 OpenOffice stuff has upgraded to using gtk-2.0 instead. So we'll be needing a whole new IA32 build of mplayer now :(

---

### Post by Conq on 2006-04-29
I'm probably going to make one once Dapper is officially released. 
Hopefully a less hackish version than the one i made previously ;-)

---

### Post by richardjones on 2006-04-29
I've ended up just reinstalling a 32-bit version of Dapper. It's just easier at this time :)

---

### Post by DancingSun on 2006-06-05
[QUOTE=Conq]I'm probably going to make one once Dapper is officially released. 
Hopefully a less hackish version than the one i made previously ;-)[/QUOTE]
Please do make a new one!  I'll be greatful for sure!

---

### Post by superm1 on 2006-06-05
I can definately say I miss my mplayer-bin ebuild from my gentoo days.  A dapper version of this would make me a happy panda :)

---

### Post by Conq on 2006-06-05
I made one yesterday, look at the dapper HOWTO's :-).

---

### Post by biker3 on 2006-06-25
Hi, I have a problem with openoffice.org:

```
root@giant:/home/dayer/Desktop# dpkg -i mplayer32_1.0pre6-1_amd64.deb
Seleccionando el paquete mplayer32 previamente no seleccionado.
(Leyendo la base de datos ...
100652 ficheros y directorios instalados actualmente.)
Desempaquetando mplayer32 (de mplayer32_1.0pre6-1_amd64.deb) ...
dpkg: error al procesar mplayer32_1.0pre6-1_amd64.deb (--install):
 intentando sobreescribir `/lib32/libcom_err.so.2.1', que está también en el paquete ia32-libs-openoffice.org
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar:
 mplayer32_1.0pre6-1_amd64.deb

```

I do them

```
dpkg -i --force-all mplayer32_1.0pre6-1_amd64.deb
```

But when I try run "mplayer32" the program not run.```
mplayer32: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory

```

](*,)

---

### Post by amd-64 on 2006-07-02
[QUOTE=biker3]

But when I try run "mplayer32" the program not run.```
mplayer32: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory

```

[/QUOTE]


You are missing some of the lib32 libraries. Check if the following packages are installed

```

sudo apt-get install ia32-libs-sdl lib32ncurses5
```

I am using the mplayer package from [www.stud.ntnu.no/~grannas/debs/mplayer32_1.0pre7-1_amd64.deb](www.stud.ntnu.no/~grannas/debs/mplayer32_1.0pre7-1_amd64.deb)

---

### Post by biker3 on 2006-07-02
Hi, thanks.

But now there's other problem :oops:. When I run "mplayer32", don't start and in console i see:

```
mplayer32: error while loading shared libraries: libgssapi_krb5.so.2: cannot open shared object file: No such file or directory

```

I have installed ia32-libs-sdl lib32ncurses5 and your .deb, and also libgssapi4-heimdal libgssapi1 but the problem continue:?

---

### Post by Conq on 2006-07-09
> **biker3 said:**
> Hi, thanks.

But now there's other problem :oops:. When I run "mplayer32", don't start and in console i see:

```
mplayer32: error while loading shared libraries: libgssapi_krb5.so.2: cannot open shared object file: No such file or directory

```

I have installed ia32-libs-sdl lib32ncurses5 and your .deb, and also libgssapi4-heimdal libgssapi1 but the problem continue:?

You probably need to reinstall the ia32-libs-openoffice.org package:
```

sudo apt-get install ia32-libs-openoffice.org

```

---

### Post by biker3 on 2006-07-09
Thank's Conq, but now... :oops: the error is:

```
mplayer32: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

[-o<

---

### Post by Conq on 2006-07-10
> **biker3 said:**
> Thank's Conq, but now... :oops: the error is:

```
mplayer32: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

[-o<

sudo apt-get install ia32-libs-gtk ia32-libs. It's in the HOWTO.
Maybe i should make it a point in the list, rather than just text at the bottom, there seems to be a lot of people who have this problem.

---

### Post by Iesos on 2006-07-10
I get the same libgtk1.2 error, but I've got the libgtk installed, i.e. 
$ sudo apt-get install ia32-libs-gtk ia32-libs
Isn't enough to get this working.

---

### Post by Conq on 2006-07-11
> **Iesos said:**
> I get the same libgtk1.2 error, but I've got the libgtk installed, i.e. 
$ sudo apt-get install ia32-libs-gtk ia32-libs
Isn't enough to get this working.

Hmm, I don't use Hoary/Breezy anymore, so I can't check what package contains that library. Try going to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and search for the file it is complaining about.

---

### Post by Iesos on 2006-07-11
I'm on Dapper, and as I said, I allready got the needed package and it doesn't work, and I have updated the libs with $ldconfig.

---

### Post by Conq on 2006-07-12
> **Iesos said:**
> I'm on Dapper, and as I said, I allready got the needed package and it doesn't work, and I have updated the libs with $ldconfig.

Then you are on the wrong thread. This package only works for hoary/breezy.
Look at [http://ubuntuforums.org/showthread.php?t=188974](http://ubuntuforums.org/showthread.php?t=188974) instead.

---

### Post by drunken_sapo on 2006-11-26
Hi, 
 In the first place I want to thank you for your great work. I'm tryin to make it work on ubuntu edgy but without luck. Here's the error I get when I try to install your package. Any clue about it?
Thanks in advance,
                  Juan
-------------------
Unpacking mplayer32 (from .../mplayer32_1.0pre6-1_amd64.deb) ...
dpkg: error processing /home/juan/downloads/mplayer32_1.0pre6-1_amd64.deb (--install):
 trying to overwrite `/lib32/libcom_err.so.2.1', which is also in package ia32-libs-openoffice.org
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/juan/downloads/mplayer32_1.0pre6-1_amd64.deb

---

### Post by forger on 2008-07-02
Sorry for the bump, but I have a problem as well on ubuntu hardy heron amd64 / 64-bit, any suggestions?

```

$ mplayer file.wmv 
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing file.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  640x480  24bpp  1000.000 fps  1500.0 kbps (183.1 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[wmv3 @ 0xf43220]Reserved RES_SM=2 is forbidden
Could not open codec.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x33564D57.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 48.0 kbit/3.40% (ratio: 6003->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   5.1 (05.0) of 2103.0 (35:03.0)  0.3% 

MPlayer interrupted by signal 2 in module: play_audio
```


I tried mplayer32 with the newest mplayer32 ([http://folk.ntnu.no/grannas/debs/mplayer32_20070130-1_amd64.deb](http://folk.ntnu.no/grannas/debs/mplayer32_20070130-1_amd64.deb))
but it results to this:

> $ mplayer32 file.wmv 
mplayer32: error while loading shared libraries: libldap_r.so.2: cannot open shared object file: No such file or directory

And I have ldap-r!
lrwxrwxrwx 1 root root     18 2008-05-17 21:01 /usr/lib32/libldap-2.4.so.2 -> libldap_r-2.4.so.2
lrwxrwxrwx 1 root root     22 2008-05-17 21:01 /usr/lib32/libldap_r-2.4.so.2 -> libldap_r-2.4.so.2.0.3
-rw-r--r-- 1 root root 249924 2008-04-29 10:47 /usr/lib32/libldap_r-2.4.so.2.0.3

---

### Post by forger on 2008-07-02
fixed:
```

sudo ln -s /usr/lib32/libldap_r-2.4.so.2 /usr/lib32/libldap_r.so.2
sudo ln -s /usr/lib32/liblber-2.4.so.2 /usr/lib32/liblber.so.2

```

---

### Post by XxsydenxX on 2008-10-01
xxsydenxx@xxsydenxx-pc:~$ sudo dpkg -i mplayer32_1.0pre6-1_amd64.deb
(Reading database ... 121352 files and directories currently installed.)
Unpacking mplayer32 (from mplayer32_1.0pre6-1_amd64.deb) ...
dpkg: error processing mplayer32_1.0pre6-1_amd64.deb (--install):
 trying to overwrite `/lib32/libcom_err.so.2.1', which is also in package ia32-libs
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 mplayer32_1.0pre6-1_amd64.deb



thats the error i get, please anyone wanna help??

---

### Post by ouija on 2009-02-08
Hi there,

I am trying to get HD WMV (audio) playback in Ubuntu Hardy AMD64 version and read about how installing the w32codecs and mplayer 32 bit package could do it.

So I looked into my synaptic package manager and found the following packages: 

ia32-libs -> installed to allow support of 32 bit on amd64; No errors.
ia32-w32codecs -> installed 32bit codecs; No errors.
ia32-mplayer -> tried to install; failed with the following error: 
[B]
ia32-mplayer:
 Depends: ia32-lib-generic  but it is not installable[/B]

I've looked high and low for this "ia32-lib-generic" and to no avail; Apparently it doesn't exist or maybe it is no longer supported under Hardy AMD64?  -- Anyone have any suggestions?

---

