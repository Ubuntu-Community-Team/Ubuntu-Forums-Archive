---
title: "[SOLVED] Terminal + Python + Mencoder help!"
date: 2008-08-29
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-08-29
I have a folder called frames, which is filled with tga images, and their names are "frame0", "frame1", "frame2" and so on. I may have tons of these files.

Then I have a python app, which creates an AVI from all those files. I use this command:
```

os.system("mencoder mf://frames/*.tga -mf w=800:h=600:fps=10:type=tga -ovc copy -oac copy -o output.avi")
```

But that command doesn't seem to create the avi of the files in the correct order. I want it to first add "frame0", then "frame1", and finally "frame2". 
But How can I do it when I may have 200 frames? I need help with this.

---

### Post by days_of_ruin on 2008-08-29
> **crazyfuturamanoob said:**
> I have a folder called frames, which is filled with tga images, and their names are "frame0", "frame1", "frame2" and so on. I may have tons of these files.

Then I have a python app, which creates an AVI from all those files. I use this command:
```

os.system("mencoder mf://frames/*.tga -mf w=800:h=600:fps=10:type=tga -ovc copy -oac copy -o output.avi")
```

But that command doesn't seem to create the avi of the files in the correct order. I want it to first add "frame0", then "frame1", and finally "frame2". 
But How can I do it when I may have 200 frames? I need help with this.

So you only want to run this command with three files?
I don't understand how mencoder works but you could try something like
this:```
import os
frames = ['frame0','frame1','frame2']
iter = os.walk("pathtothedirectory")
for i in a:
    for file in i[2]:
        if file.split('/')[-1] in frames:
            #Do your mencoder thing
       
```

---

### Post by crazyfuturamanoob on 2008-08-30
OK, I got the files in folder called "frames": frame0.tga, frame1.tga, frame2.tga.
Then, I use some string manipulating to get this command:
```
mencoder mf://frames/frame0.tga, frame1.tga, frame2.tga, frame3.tga -mf w=800:h=600:fps=1:type=tga -ovc copy -oac copy -o output.avi
```
But that command doesn't work, it gives me an error message:
```
arho@ohra-laptop:~/Asiakirjat/anim$ mencoder mf://frames/frame0.tga, frame1.tga, frame2.tga -mf w=800:h=600:fps=1:type=tga -ovc copy -oac copy -o output.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: AMD Turion(tm) 64 X2 Mobile Technology TL-60 (Family: 15, Model: 104, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] filelist: frames/frame0.tga,
[mf] number of files: 1
[demux_mf] file type was not set! trying 'type=tga'...
VIDEO:  [MTGA]  0x0  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x4147544D  size:0x0  fps:25.00  ftime:=0.0400
videocodec: framecopy (0x0 24bpp fourcc=4147544d)
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
File not found: 'frame1.tga,'00fps Trem:   0min   0mb  A-V:0.000 [0:0]
Failed to open frame1.tga,.
Cannot open file/device.

Exiting...
arho@ohra-laptop:~/Asiakirjat/anim$
```

---

### Post by crazyfuturamanoob on 2008-08-30
I also tried it without .tga in front of each filename:
```
arho@ohra-laptop:~/Asiakirjat/anim$ mencoder mf://frames/frame0, frame1, frame2 -mf w=800:h=600:fps=1:type=tga -ovc copy -oac copy -o output.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: AMD Turion(tm) 64 X2 Mobile Technology TL-60 (Family: 15, Model: 104, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] filelist: frames/frame0,
[mf] number of files: 0
Segmentation fault
arho@ohra-laptop:~/Asiakirjat/anim$
```

---

### Post by crazyfuturamanoob on 2008-08-30
I got it working, no need to help anymore.

---

