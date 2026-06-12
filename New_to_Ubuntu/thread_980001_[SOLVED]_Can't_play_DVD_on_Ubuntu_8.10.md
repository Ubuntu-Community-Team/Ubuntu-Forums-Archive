---
title: "[SOLVED] Can't play DVD on Ubuntu 8.10"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Frenske on 2008-11-12
I can't play DVDs on my Ubuntu 8.10. VLC player does absolutely nothing and Totem player give the following error:

```
An error occurred
Could not open location; you might not have permission to open the file.
```

These are legal CDs borrowed from the local library and play in my dual boot Windows XP fine with normal software. What is wrong?

---

### Post by Ryadt on 2008-11-12
Try ```
sudo apt-get install ubuntu-restricted-extras
```
And also add the medibuntu repos
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Asem on 2008-11-12
try opening your media player from the terminal using gksudo

---

### Post by Keen101 on 2008-11-12
It might be an 8.10 regression.... (a bug)

---

### Post by Frenske on 2008-11-12
Just tested if I could play an audio CD but I can't either play audio CDs, but I can browse them. What's going on.

---

### Post by terry_gardener on 2008-11-12
are these errors when it trys to autorun. if what happens when you open the software first ie vlc and then play the disc manually (using the file menu) 

just asking because vlc doesn't work for me either when it use to autorun, it would open and stop responding when trying load the media, (this can be fixed however changing the command in the edit menus app by removing the switches). 

also find this thread very useful 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Frenske on 2008-11-12
> **Ryadt said:**
> Try ```
sudo apt-get install ubuntu-restricted-extras
```
And also add the medibuntu repos
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

That did it well medibuntu repos did it! Odd that all the media software is included but not the right repos to play it.

---

### Post by elanning on 2008-11-18
I ran the get restricted extras command, and a lot of stuff downloaded and installed itself, but when I right click on the dvd from the desktop and choose "open with movie player", totem starts up and gives me the exact error mentioned above "you might not have permission to open the file" 

dont suppose anyone has any other ideas?

---

### Post by johnm64118 on 2008-11-30
I'm having an issue watching DVDs on Ubuntu 8.10 (kernel 2.6.27-9).  I've been through all of the how-to's and have installed restricted formats from the following:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%208.10%20(i386](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%208.10%20(i386))

I installed VLC too.

When I insert a DVD, i.e. Stuart Little, I see the STUART_LITTLE icon appear on the desktop and the CDROM 0 window opens with the options to Open VLC media player or Open Autorun prompt.  

When I click the Open VLC media player option music begins to play, VLC opens for a second or two but then it shuts down.

It does a similar thing if you open VLC and do Media, Open Disc, Play.

I can repeat this every time.  I've rebooted, added and removed various packages, etc... with the same issues.  A similar thing happens with the GNOME default video player.  That's why I installed VLC.

The hardware is a Toshiba Satellite A215-S5829 laptop.

I'm still new to Linux, but have worked in the Windows world for a long time now.

Any help would be greatly appreciated!

Thank you in advance.

**Edit:**

I went to the terminal and started VLC from the command line.  Here is what I got:

vlc

VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000381] access_http access error: error: HTTP/1.0 404 Not Found
[00000381] access_http access error: error: HTTP/1.0 404 Not Found
[00000381] access_mms access error: error: HTTP/1.0 404 Not Found
[00000367] main playlist error: no suitable access module for `[http://i28.tinypic.com/f374f8.png](http://i28.tinypic.com/f374f8.png)'
[00000378] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86

(process:14347): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(process:14347): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(process:14347): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(process:14347): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


I Googled the error message - "x11 video output error: X11 request 140.19 failed with error code 11" and came up with the following:

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/281743](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/281743) and
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=938894](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=938894)

Changing the output to X11 seems to have resolved the issue for me.  I'm going to try some of the other output modes also to see what they do.

---

### Post by djinn1973 on 2008-12-08
I was having the same problem earlier today on my sisters laptop try running ```
 sudo /usr/share/doc/libdvdread3/install-css.sh
```again thats what finally took care of it for me.

---

