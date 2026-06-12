---
title: "GIMP GAP help"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by bsharp on 2008-10-18
Hey all, I'm doing a Shakespeare video project and I've used the GAP plugin for The GIMP and when I try to encode my frames to a video file, it's not detecting any of my video encoders (ffmpeg, mencoder, etc.).  Has anyone else had this problem and how did you fix it?

---

### Post by bsharp on 2008-10-18
Anyone?  I've tried the setup with mpeg_encode but it is only available as a .rpm and I can't get alien to work with it.  Compiling mpeg_encode from source doesn't work either, I get a segmentation fault when trying to use it.

---

### Post by bsharp on 2008-10-18
> dorch wrote:
ffmpeg has been already installed with synaptic.


The GAP does not use a shared FFMPEG library, regardless of whether or not one is installed. The source for GAP includes the source for FFMPEG and should be compiled with that snapshot of FFMPEG as a static library.

dorch wrote:
Does anyone know why ffmpeg is not present in the gap's video encoder ?

The Ubuntu maintainer for the GAP package must not have compiled the package with FFMPEG enabled. You would have to ask that maintainer what his reasoning was.


from [http://www.gimptalk.com/forum/gimp-gap-on-ubuntu-hardy-t32844s25.html](http://www.gimptalk.com/forum/gimp-gap-on-ubuntu-hardy-t32844s25.html)


It seems that the Ubuntu package maintainer who compiled it did it without ffmpeg support so I'll (attempt to) compile it myself.

---

### Post by bsharp on 2008-10-18
Well, after several hours of scouring the web, I still cannot get the GAP to compile from source, so I had to result to mencoder. It did the job, but I would have liked to get this working.

---

