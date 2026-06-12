---
title: "cinelerra codecs?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by rm2011 on 2008-11-07
Hi everyone,I am using xubuntu 8.10 and am creating a movie using cinelerra,   every single formad i try to render the file to says "this format does not support video"  so the only two that will work are "raw dv and wuicktime for linux.  Whenever i try to render to raw dv linux shuts down.  And when i render it to quicktime for linux, all of the colors are messed up!!  id there anyway I can render it to a .wmv or something like that? any way to install more codecs?  
--thanks

---

### Post by pekarna on 2012-07-10
Hi,  Cinelerra doesn't have much output formats. I personally didn't find a way to export 1024 x 780. So I have created YUV/MPEG Stream without audio (not supported), exported the track to wav, and then joined this together using VLC.

Right, it sucks.

---

### Post by mapes12 on 2012-07-10
Don't know much about that app you're using but Ubu 8.10 is no longer supported which means that as new video support is added to the Linux Kernel you won't be getting it. Therefore you may want to consider install Ubu 12.04. When you've done that then install the package **ubuntu-restricted-extras**, head over to the **Medibuntu** webiste and follow the instructions to install the media codecs, then install the **VLC** media player which should install any other codecs missed.

---

