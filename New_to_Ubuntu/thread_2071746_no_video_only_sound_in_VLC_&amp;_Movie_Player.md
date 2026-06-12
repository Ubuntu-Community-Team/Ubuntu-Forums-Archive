---
title: "no video only sound in VLC &amp; Movie Player"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by TooFreppaT on 2012-10-16
I found these two:
[http://ubuntuforums.org/showthread.php?t=1655665](http://ubuntuforums.org/showthread.php?t=1655665)
[http://ubuntuforums.org/showthread.php?t=1187827](http://ubuntuforums.org/showthread.php?t=1187827)

but they are from ages ago...

anyway...from the first one I got:```
user@computer:~$ mplayer vids.mpg
mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vids.mpg.
File not found: 'vids.mpg'
Failed to open vids.mpg.


Exiting... (End of file)

``````
user@computer:~$ mplayer -vo gl vids.mpeg
mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vids.mpeg.
File not found: 'vids.mpeg'
Failed to open vids.mpeg.


Exiting... (End of file)

``````
user@computer:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1705
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9640
00:01.1 Audio device: ATI Technologies Inc Device 1714
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Device 1707
00:10.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB Controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:14.5 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Network controller: Atheros Communications Inc. AR9300 Wireless LAN adaptor (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
``````
user@computer:~$ mediainfo -f vids.mpg
mediainfo: command not found

```

---

### Post by TooFreppaT on 2012-10-16
okay so now I followed [http://learnedstuffs.wordpress.com/2011/05/18/playing-videos-inside-the-terminal-on-ubuntu-10-04/](http://learnedstuffs.wordpress.com/2011/05/18/playing-videos-inside-the-terminal-on-ubuntu-10-04/) to run an .avi file from inside the terminal:```
user@computer:~$ mplayer -vo caca ~/Sample.avi
mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/user/Sample.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x352  12bpp  29.970 fps  1499.7 kbps (183.1 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
mpg123: Can't rewind stream by 55 bits!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[mpeg4 @ 0x7f3e14203020]Invalid and inefficient vfw-avi packed B frames detected
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is 1.82:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f3e1364f620]using unscaled yuv420p -> bgr24 special converter
VO: [caca] 640x352 => 640x352 BGR 24-bit 
A:  57.4 V:  57.4 A-V: -0.001 ct:  0.001 1720/1720  9% 60%  0.7% 0 0 

Exiting... (End of file)
```so now I get something visual!
but it's kinda like playing an old game...except it's more like ascii art or something - all the characters are flashing and changing and also changing different colours (so there is some colour but the video it's self is mainly black and white)

---

### Post by TooFreppaT on 2012-10-16
and this doesn't change anything at all (still no video, only audio):```
user@computer:~$ vlc ~/Sample.avi
VLC media player 1.1.9 The Luggage (revision exported)
Warning: call to srand(1350383871)
Warning: call to rand()
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x1bd0120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1350383871)
Warning: call to rand()
Warning: call to srand(1350383871)
Warning: call to rand()
Warning: call to srand(1350383871)
Warning: call to rand()
Warning: call to srand(1350383871)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:5059): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")
[0x7f5a480009f0] signals interface error: signal 17 overriden (0x7f5a7af55400)
[0x7f5a480009f0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x7f5a480009f0] signals interface error: signal 17 overriden (0x7f5a7af55400)
[0x7f5a480009f0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]

** (<unknown>:5059): CRITICAL **: giop_thread_request_push: assertion `tdata != NULL' failed
```

---

### Post by TooFreppaT on 2012-10-16
right click

Open With > GNOME MPlayer

success!  :o

```
user@computer:~$ gnome-mplayer ~/Sample.avi
The volume on 'Default' is 1.000000

```

---

### Post by TooFreppaT on 2012-10-16
...short lived :(

restarted and now no video at anymore again (accept for Movie Player via Terminal but it's still the same quality)

---

### Post by TooFreppaT on 2012-10-16
okay, so for some reason I get both video and audio (like normal) by using MS WindowsXP with VirtualBox OSE thru (my only OS) Ubuntu... which means it a problem with Ubuntu, and not my new graphics card

this has me very puzzled me very indeed.......

---

