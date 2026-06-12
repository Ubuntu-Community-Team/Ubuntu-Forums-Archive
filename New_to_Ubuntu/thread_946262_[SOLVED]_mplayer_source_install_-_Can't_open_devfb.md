---
title: "[SOLVED] mplayer source install - Can't open /dev/fb0"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by susiriss on 2008-10-13
Hello there,
             I tried installing mplayer from source as the binary package in Ubuntu does not come with Mencoder. I successfully compiled and installed the package. However, when I try to play a video, it only gives sound with no video output. I get a list of errors when starting playback.

However, if I install the binary from Ubuntu repositories, it successfully plays videos without a problem. So I wonder what is happening with the source install. Complete output of mplayer is shown below. ( this particular clip does not have audio in it)

```
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing rip.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
VIDEO:  [FMP4]  720x480  24bpp  29.970 fps  2560.1 kbps (312.5 kbyte/s)
Clip info:
 Software: Lavf52.22.1
Can't open /dev/fb0: No such file or directory
[fbdev2] Can't open /dev/fb0: No such file or directory
VO: [v4l2] No such file or directory
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
[cyberblade] Error occurred during pci scan: Operation not permitted
[mach64] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[nvidia_vid] Error occurred during pci scan: Operation not permitted
[pm3] Error occurred during pci scan: Operation not permitted
[radeon] Error occurred during pci scan: Operation not permitted
[rage128] Error occurred during pci scan: Operation not permitted
[savage_vid] Error occurred during pci scan: Operation not permitted
[SiS] Error occurred during pci scan: Operation not permitted
[unichrome] Error occurred during pci scan: Operation not permitted
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [null] 720x480 => 854x480 Planar YV12 
V:  27.6 829/829  5%  0%  0.0% 0 0      
```

Thank You

---

### Post by andrew.46 on 2008-10-13
Hi,

MPlayer is a fairly complex beast to compile from source in Ubuntu. If you want to install a more modern version you could try this guide:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

which has already done all of the hard work for you :-).

  Andrew

---

### Post by susiriss on 2008-10-13
Hello andrew,
             Thanks for your link. I am looking into it.

---

### Post by susiriss on 2008-10-22
Hi, 
                 The issue is due to unavailability of some X11 development packages. I installed those dev packages and reinstalled mplayer, and now it successfully plays videos. 

Wonder why it is unable to complain about those missing pieces ???

Thanks

---

### Post by michelek on 2009-09-29
and what were those missing packages?

---

### Post by andrew.46 on 2009-09-29
Hi michelek,

> **michelek said:**
> and what were those missing packages?

A slightly *blunt* method of doing this is to use build-dep:

```
sudo apt-get build-dep mplayer
```

which will pull in the development packages used by the Ubuntu developers to create the repository version of MPlayer. This pulls in a few packages not relevant to the svn MPlayer but it is an easy way to get started. Best to build a 'mplayer-nogui' package though....

Andrew

---

### Post by duphenix on 2012-03-23
I had this error, and fixed it with a permission change:

```
sudo chmod 666 /dev/fb0
```

---

### Post by Perfect Storm on 2012-03-23
Necromancing.

Thread closed.

---

