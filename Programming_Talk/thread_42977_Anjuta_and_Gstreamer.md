---
title: "Anjuta and Gstreamer"
date: 2005-06-20
forum: Programming Talk
---

### Post by credo on 2005-06-20
I'm having real trouble getting Anjuta to include the Gstreamer 0.8 libraries. I am used to simply adding $(pkg-config --cflags --libs gstreamer-0.8) on the command line, since I haven't used an IDE in linux development before.

Can someone point me in the right direction? Cheers

---

### Post by Kimm on 2005-06-20
I'm not completely sure, but I think this might work:

Settings -> Compiler and Linker settings -> Options

Then set: Compiler flags (CFLAGS) to "'pkg-config --cflags --libs gstreamer-0.8'"

I think... :-P

---

