---
title: "Can't play DVDs"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Peter_8487 on 2008-05-29
Hello all,

I can't seem to play DVDs properly on any of the players I've tried: Totem, VLC and mplayer.  When I first insert the DVD, I get the following error message:

Failed to mount "[dvd_title]"

mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0.

Then, when Totem starts up, it tells me "An error occurred: Location not found".

If I instead try to play the disc using mplayer, (by selecting dvd -> open disc) I get nothing. However, if I skip forward to another title I can get some very choppy playback and an error message about the audio

"Could not open/initialize audio device -> no sound".

VLC player doesn't play at all.

So then I tried playing the DVD on MPlayer through the terminal, had no luck, and got the following output:

peter@peter:~$ mplayer dvd://
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(TM) CPU                1066MHz (Family: 6, Model: 11, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
There are 6 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.
number of audio channels on disk: 0.
number of subtitles on disk: 0
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
V:   0.3  12/ 12 ??% ??% ??,?% 0 0 

Exiting... (End of file)

It could just be that my computer isn't up to it: it's a pentium 1066 with only 256MB of RAM.  Back before I liberated myself from Microsoft I was able to play DVDs, though not very smoothly.

Any help would be much appreciated.

Peter

---

### Post by lostlinuxkiwi on 2008-05-29
have you got the codecs from medibuntu repository?

---

### Post by lostlinuxkiwi on 2008-05-29
If you haven't then go here 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Peter_8487 on 2008-05-29
That solved it!  Thank you very much.

---

