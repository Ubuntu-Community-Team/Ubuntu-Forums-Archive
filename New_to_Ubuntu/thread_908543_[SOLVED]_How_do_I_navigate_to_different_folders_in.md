---
title: "[SOLVED] How do I navigate to different folders in the Terminal?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by curiousnoob on 2008-09-02
I am trying to use this command: 
mencoder <filename.avi> -ovc xvid -oac mp3lame -o <output.avi>  
but I always get and error saying that it cannot find the file.  I assume that I must navigate in the Terminal to the proper folder but I do not know how.

---

### Post by Elfy on 2008-09-02
Using cd - when you start you terminal you are in your /home - to get to the desktop, ~ is a shorthand to home

```
cd Desktop
```

to get to for instance the X11 folder in etc

```
cd /etc/X11
```

Case is important, desktop is completely different to Desktop

So if the file is on the desktop you could run it without changing the directory

```
mencoder ~/Desktop/<filename.avi> -ovc xvid -oac mp3lame -o <output.avi>
```

---

### Post by WRDN on 2008-09-02
I would also add:

```
cd ..
```

This is used to change to the current directories parent directory. For example, the parent directory of the X11 folder is /etc.
You can also use:

```
cd ../..
```

This will go to the parent of the parent directory. You can place as many "../" directives here as you want, so it can be used as a long winded way to get back to the root of the partition. E.g. if you were in your users Desktop folder, you can get back to the root of the partition by typing:

```
cd ../../..
```

---

### Post by Nevyn on 2008-09-02
Also ```
cd ~
``` takes you to your Home folder

---

### Post by Elfy on 2008-09-02
To add further this might be wortha look

[https://help.ubuntu.com/7.04/basic-commands/C/ar01s03.html](https://help.ubuntu.com/7.04/basic-commands/C/ar01s03.html)

You can also get the man page for most things in terminal, it's a quick way to look at commands you might be running - 

man cd

---

### Post by kellemes on 2008-09-02
> **Nevyn said:**
> Also ```
cd ~
``` takes you to your Home folder

You can save 2 keys ;-)
```
cd
```

---

### Post by curiousnoob on 2008-09-02
Thanks for all the help and info.  I decided to move the file to my Desktop to be sure I could make it work but when I run Mencoder I get this error.  Does anyone know what the problem might be? 

mencoder ~/Desktop/Video1.avi -ovc xvid -oac mp3lame -o output.avi
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.93GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x2bc15000
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MP42]  480x360  24bpp  29.970 fps  921.6 kbps (112.5 kbyte/s)
[V] filefmt:3  fourcc:0x3234504D  size:480x360  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
xvid: using library version 1.1.2 (build xvid-1.1.2)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmp42] vfm: ffmpeg (FFmpeg M$ MPEG-4 v2)
==========================================================================
MP3 audio selected.
VDec: vo config request - 480 x 360 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: XviD (480x360 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=480x360, sampled=480x360
xvid: you must specify one or a valid combination of 'bitrate', 'pass', 'quantizer' settings
FATAL: Cannot initialize video driver.
VDec: vo config request - 480 x 360 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: XviD (480x360 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=480x360, sampled=480x360
xvid: you must specify one or a valid combination of 'bitrate', 'pass', 'quantizer' settings
FATAL: Cannot initialize video driver.

Exiting...

---

### Post by halitech on 2008-09-02
> mencoder ~/Desktop/Video1.avi -ovc xvid -oac mp3lame -o output.avi
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team

maybe I'm missing something but is there a reason why you are "converting" from .avi to .avi?

---

### Post by curiousnoob on 2008-09-02
> **halitech said:**
> maybe I'm missing something but is there a reason why you are "converting" from .avi to .avi?

It needs to be a format that my Xbox 360 can read.

---

### Post by t0p on 2008-09-02
I think this is your problem:

> xvid: you must specify one or a valid combination of 'bitrate', 'pass', 'quantizer' settings

I have to echo what halitech said: if you "convert" a file from .avi to .avi, you are left with an .avi file -which is what you started with, is it not?

Or maybe, like halitech, I am missing something?

---

### Post by curiousnoob on 2008-09-02
> **t0p said:**
> I think this is your problem:



I have to echo what halitech said: if you "convert" a file from .avi to .avi, you are left with an .avi file -which is what you started with, is it not?

Or maybe, like halitech, I am missing something?

Avi is the container but there are numerous codecs that fall under the "avi" umbrella.

---

### Post by tommynz1975 on 2008-09-02
> **curiousnoob said:**
> Avi is the container but there are numerous codecs that fall under the "avi" umbrella.

Quite true, what Codecs is the AVI in and What Codecs do you want to have the outputed AVI in??

This way the smarties can see where your syntax errors might be :)

---

### Post by curiousnoob on 2008-09-02
> **tommynz1975 said:**
> Quite true, what Codecs is the AVI in and What Codecs do you want to have the outputed AVI in??

This way the smarties can see where your syntax errors might be :)

This is the format the file is currently in: 
VIDEO
Duration: 1h 32m
Size: 700.1MB
Dimensions: 480 x 360
Codec: Microsoft MPEG-4 4.2
FPS: 30

AUDIO
Codec: MPEG 1 Audio, Layer 3 (MP3) 

And I want it in any format that will work on the Xbox 360.  I know for a fact that .mov will work and here is a link to all the specifics for other formats: 
[http://www.xbox.com/en-us/support/systemuse/xbox360/digitalmedia/videoplaybackfaq.htm](http://www.xbox.com/en-us/support/systemuse/xbox360/digitalmedia/videoplaybackfaq.htm)

---

### Post by curiousnoob on 2008-09-02
Since the original question has been answered I am creating a new post here: 
[http://ubuntuforums.org/showthread.php?p=5715908#post5715908](http://ubuntuforums.org/showthread.php?p=5715908#post5715908) 
Thanks for the help with the navigation problems.

---

