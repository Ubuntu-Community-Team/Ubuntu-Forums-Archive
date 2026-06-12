---
title: "video player problem"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-08-06
Hey guys. 
I'm not exactly sure what the problem is ... but; I installed VLC v1.1.9 [like this]("http://ubuntuforums.org/showthread.php?t=2034244&page=2")-  and since I re-installed the program, as I accidentally updated VLC; the players I use; SMPlayer, the default movie player, VLC (which only seems to work on streams) and gxine (which for some reason, randomly appeared - as I haven't consciously installed it) don't work properly. 
VLC just opens up a blank window, which refuses to close taking up a **lot** of CPU memory. SMPlayer reproduces *some* videos, but for the rest, the audio is completely off sync and with a very laggy image. The default player just opens up a black window. And gxine opens fine, but after a few minutes crashes my panels and all my applications forcing me to restart. 

Any thoughts or help would be hugely appreciated! Thank you.

---

### Post by llamabr on 2012-08-06
No idea.  Run the thing in a terminal, and then copy any errors here.

In the meantime, I prefer mplayer for both movies and music.  It's overkill, they'll say, but so what?

---

### Post by z3nhakr on 2012-08-06
what are your specs? try running it from the terminal so that when it crashes you will see the error message. if all else fails try running it as root. i had to do this with banshee once.

---

### Post by kabukiM0n0 on 2012-08-07
My specs are - Intel Atom N2600 1.6GHz / 1Gb but they should be irrelevant, as I've run all these programs beforehand with no issue whatsoever.

```
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[mpeg4 @ 0xb63e3e20]Invalid and inefficient vfw-avi packed B frames detected
Movie-Aspect is 1.80:1 - prescaling to correct movie aspect.
VO: [x11] 720x400 => 720x400 Planar YV12 
[swscaler @ 0xb6b95a20]using unscaled yuv420p -> bgra special converter
A:  67.7 V:  67.2 A-V:  0.499 ct:  0.019 2015/2015 21% 74%  1.0% 914 0
```
Then a line pops up saying my system is too slow to play this. 
That's where it gets all weird, because they all used to work perfectly fine, until I built vlc :/

---

### Post by kabukiM0n0 on 2012-08-07
This is the response for vlc 


```
(vlc:3052): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(vlc:3052): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(vlc:3052): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(vlc:3052): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
[mpeg4 @ 0xb531a620] Invalid and inefficient vfw-avi packed B frames detected
[0xacc00cd8] xcb_xv vout display error: no available XVideo adaptor
[0xb5300d68] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)

```

---

### Post by kabukiM0n0 on 2012-08-07
```
(smplayer:3159): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(smplayer:3159): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(smplayer:3159): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(smplayer:3159): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
This is SMPlayer v. 0.7.0 (SVN r3809) running on Linux

```
This one opens but stays on a black screen.

---

### Post by kabukiM0n0 on 2012-08-07
```
(gxine:3170): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gxine:3170): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gxine:3170): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gxine:3170): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gxine:3170): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gxine:3170): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gxine:3170): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gxine:3170): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
warning: configuration item media.audio_cd.device points to a non-existent location /dev/cdrom
warning: configuration item media.audio_cd.cddb_cachedir points to a non-existent location /home/km/.xine/cddbcache
warning: configuration item media.capture.save_dir points to a non-existent location 
warning: configuration item media.dvb.channels_conf points to a non-existent location /home/km/.xine/channels.conf
warning: configuration item media.dvd.device points to a non-existent location /dev/dvd
warning: configuration item media.vcd.device points to a non-existent location /dev/cdrom
warning: configuration item decoder.external.real_codecs_path points to a non-existent location 
warning: configuration item decoder.external.win32_codecs_path points to a non-existent location /usr/lib/codecs
warning: configuration item subtitles.separate.font_freetype points to a non-existent location 
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
WARN: Can't get file status for /dev/cdrom:
No such file or directory
WARN: could not retrieve file info for `/dev/cdrom': No such file or directory
WARN: can't open nrg image file /dev/cdrom for reading
[mpeg4 @ 0xac00c480] Invalid and inefficient vfw-avi packed B frames detected

** (gxine:3170): CRITICAL **: dbus_set_g_error: assertion `gerror == NULL || *gerror == NULL' failed
gtkvideo: problem when inhibiting the GNOME screensaver: Method "Inhibit" with signature "ss" on interface "org.gnome.ScreenSaver" doesn't exist
```

That's the last one. And again I must stress - they used to work perfectly fine with all the video files I own up until v.1.1.9 of vlc was built.

---

### Post by z3nhakr on 2012-08-07
have you considered installing the latest release of vlc (2.0.3) ? It should be more compatible with precise and you can install it via software center.
[https://apps.ubuntu.com/cat/applications/vlc/](https://apps.ubuntu.com/cat/applications/vlc/)

---

### Post by kabukiM0n0 on 2012-08-07
I have yes, I was using v.1.1.9 to stream off a specific site - but I'm trying to figure out if the vlc built may have had something to do with the loss of speed and video player functionality, before removing anything.

---

