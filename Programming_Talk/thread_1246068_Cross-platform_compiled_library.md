---
title: "Cross-platform compiled library?"
date: 2009-08-21
forum: Programming Talk
---

### Post by djbushido on 2009-08-21
I was developing an app that was going to use a lot of compiled libraries (dll or so) but didn't want to have to get dll's working in Linux, and .so's working in windows. I didn't know if there was a way around this. Cygwin I believe comes with g++, so I might be able to include dlfcn.h from that, but I didn't know if there was a better way. Thanks for the help!

EDIT: Stupid question, but can I just use g++ with Cygwin and use the "-lwhatever" flags and just put those in a directory with the executable? I was planning on putting it in a sub-folder, so I don't know how I would tell the program that they would be located there. Also, extending the program to use extra libraries it didn't know about at compile time would be an absolute pain.

---

