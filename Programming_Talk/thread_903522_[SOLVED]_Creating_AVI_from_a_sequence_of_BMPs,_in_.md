---
title: "[SOLVED] Creating AVI from a sequence of BMPs, in python?"
date: 2008-08-28
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-08-28
I was trying to find software with which I could create good animations fast, like pivot or flash mx.
But because pivot sucks and flash doesn't work on ubuntu, I decided to create my own software for making animations.

I started making it with python + pygame. Currently, there is a pen tool and working frame capture system.
It creates new bmp files for each frame. But I want to make animations, not just single frames.

[b]And so I have come to this problem. How can I make an AVI from a sequence of bitmaps, in python?
It doesn't have to be avi, all video formats are okay, just tell me how to do it.

External programs are okay too, it doesn't have to be 100% python.[/b]

Thanks.

---

### Post by Zugzwang on 2008-08-28
Note that your animation will be pixel graphics this way whereas the Flash animations are usually vector graphics.

Apart from that, there are a couple of libraries around. However these are not very easy to use and some may not have a Python wrapper yet. One easier way is to write all those .BMPs somewhere and then apply an external tool like Mencoder or ffmpeg to create the actual videos. You could call the external tool from your program.

---

### Post by crazyfuturamanoob on 2008-08-28
External programs are okay too.
But I can't find any software that could do it.

---

### Post by Zugzwang on 2008-08-28
> **crazyfuturamanoob said:**
> External programs are okay too.
But I can't find any software that could do it.

See here: [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html")

---

### Post by crazyfuturamanoob on 2008-08-28
Thanks, but how do I use it in python?

---

### Post by slavik on 2008-08-28
> **crazyfuturamanoob said:**
> Thanks, but how do I use it in python?
you don't need to use Python, you use it in a shell script or even directly, since the command will be one line anyway.

May I inquire how Python fits into the solution of your problem? (what are you trying to use Python for in this situation).

---

### Post by crazyfuturamanoob on 2008-08-28
> **slavik said:**
> you don't need to use Python, you use it in a shell script or even directly, since the command will be one line anyway.

May I inquire how Python fits into the solution of your problem? (what are you trying to use Python for in this situation).
I want to know how to run shell script in python, to make it easier to use.

---

### Post by slavik on 2008-08-28
> **crazyfuturamanoob said:**
> I want to know how to run shell script in python, to make it easier to use.
Could you elaborate more on that? (What do you mean by making the script easier to use?) are you writing a GUI in Python that will run a shell script with the options chosen in the GUI?

---

### Post by crazyfuturamanoob on 2008-08-28
> **slavik said:**
> Could you elaborate more on that? (What do you mean by making the script easier to use?) are you writing a GUI in Python that will run a shell script with the options chosen in the GUI?
Yeah, GUI in Python that will run a shell script with the options chosen in the GUI.
The options are stored in variables.

---

### Post by crazyfuturamanoob on 2008-08-28
I tried to run it in terminal, but it didn't work:
```

arho@ohra-laptop:~/Asiakirjat$ mencoder mf://*.jpg -mf w=800:h=600:fps=25:type=jpg -ovc lavc \
>     -lavcopts vcodec=mpeg4:mbd=2:trell -oac copy -o output.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: AMD Turion(tm) 64 X2 Mobile Technology TL-60 (Family: 15, Model: 104, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: *.jpg
[mf] number of files: 24 (96)
VIDEO:  [IJPG]  800x600  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x47504A49  size:800x600  fps:25.00  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
Pos:   0.0s      2f ( 7%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.0s      3f (12%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.1s      4f (17%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.1s      5f (20%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.2s      6f (25%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.2s      7f (30%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.2s      8f (34%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.3s      9f (38%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.3s     10f (43%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.4s     11f (46%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.4s     12f (51%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.4s     13f (56%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.5s     14f (60%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.5s     15f (64%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.6s     16f (68%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.6s     17f (73%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.6s     18f (77%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.7s     19f (81%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.7s     20f (86%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.8s     21f (91%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.8s     22f (94%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.8s     23f (100%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.9s     24f (100%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
Flushing video frames.
Filters have not been configured! Empty file?
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:    0.000 kbit/s  (0 B/s)  size: 0 bytes  0.880 secs  24 frames
Segmentation fault
arho@ohra-laptop:~/Asiakirjat$ 

```
Totem can't open output.avi. So, I got 24 frames, called "frameX.jpg". HELP!

---

### Post by Zugzwang on 2008-08-28
[LIST]
[*]Are all your JPEGs are *valid* JPEGs, i.e. not just renamed BMPs?
[*]Did you try one of the other methods on the web page, like motion-MPEG or
 "regular" codecs?
[*]Are your JPEGs different? There are a lot of complaints about "duplicate frames". Try "-vf harddup" in this case.
[/LIST]

---

### Post by crazyfuturamanoob on 2008-08-28
I don't know, I just use this command for creating a new frame:
pygame.image.save(screen, "frame" + str(frame_current) + ".jpg")
I can change the format by just changing the end ".jpg" to whatever I want to.
Then I'll remake the test animation and run the command, but doesn't work.
That command creates files frame0.jpg, frame1.jpg, frame2.jpg.

Edit: So how do I make ANY video file from ANY image files?
None of the commands work, all they give some kind of errors.
Always I get a video file, but I can't open it.

---

### Post by crazyfuturamanoob on 2008-08-28
Why the hell it keeps nagging about "duplicate frames"?!?!?
HELP! I don't get it, how to get it working? I have tried every command.

---

### Post by Zugzwang on 2008-08-29
So did you try "-vf harddup"? Have you tried opening the .JPG files in a web browser to check if they are valid .JPG files? Have you tried making the file extension uppercase (as the Pygame documentation always has these in upper case)?

---

### Post by crazyfuturamanoob on 2008-08-29
> **Zugzwang said:**
> So did you try "-vf harddup"? Have you tried opening the .JPG files in a web browser to check if they are valid .JPG files? Have you tried making the file extension uppercase (as the Pygame documentation always has these in upper case)?

They should be valid. At least I can view them with image viewer and I see the preview images correctly.

---

### Post by crazyfuturamanoob on 2008-08-29
Ok, the jpg files were NOT valid. But I got it working by saving the images as TGA.

But now the second problem:  
**How to run command *"mencoder mf://*.tga -mf w=800:h=600:fps=25:type=tga -ovc copy -oac copy -o output.avi"* from python file?**

Edit: I solved the problem all myself. The answer is: os.system()

---

