---
title: "Using GStreamer from Anjuta"
date: 2007-09-07
forum: Programming Talk
---

### Post by Violaine on 2007-09-07
I'm trying to make a simple program that just initializes GStreamer, but I can't get that far.  How do I use the GStreamer library from Anjuta?  I've tried using 'pkg-config --cflags --libs gstreamer-0.10' as compiler flags, but I just get the response "pkg-config --cflags --libs gstreamer-0.10: No such file or directory".

Please help.

---

### Post by Violaine on 2007-09-07
LOL, solved my own problem :)   I didn't think that was going to happen.

Anyway, using what I did for compiler flags was almost correct, except instead of surrounding it with single quotes ('), it had to be surrounded with backticks (`).  Weird.

---

### Post by mlinuxy on 2012-05-10
There is something wrong with libxml2 , 
the lastest version contains some bugs , 
downgrade it,and then  everything will be ok .

---

