---
title: "C++ and Audio CD access?"
date: 2007-03-20
forum: Programming Talk
---

### Post by Will May on 2007-03-20
I'm currently trying to write a small program which will rip an audio cd, get the freedb info and get the cover art (mainly to help get me familiar with C++, but also as I intend to re-rip my CDs to FLAC at some point).

The trouble is that I can't seem to find any library that provides audio cd access (I have found libcdio, but attempts to compile the examples are met with a load of "tracks.c: (.text+0x12): undefined reference to `cdio_init'" for all of the methods libcdio is supposed to provide). Can anyone point me to either a better library? Or even better tutorial for libcdio. Hell, I'd take someone pointing out why the examples refuse to compile

---

### Post by slavik on 2007-03-20
you're supposed to link against a library (-lname, where it is a dash, followed by a lowercase 'L' and 'name' is the name of the library)

for your library, the option to g++ is msot likely  '-lcdio'

---

