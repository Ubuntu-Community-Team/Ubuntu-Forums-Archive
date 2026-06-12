---
title: "stream class overhead"
date: 2011-02-07
forum: Programming Talk
---

### Post by worksofcraft on 2011-02-07
I'm writing an application that must rapidly process streams of binary data (used in images). I was thinking of coupling different decoder and compression elements together into pipes and wondering if the standard basic_stream classes of C++ would be appropriate?

Literature suggests that those incorporate a lot of overhead and unwanted fancy processing like translating characters for different locales when all I want is efficient transmission of my raw untrammeled binary data from one processing element to the next.

Has anyone got experience of existing practices and systems for handling binary data streams in C or C++ that they can share here?

---

### Post by PaulM1985 on 2011-02-08
I am currently looking into something similar with Java.  I have found that, so far, sending multiple frames of RGBA PNG files works ok, where only the changes are shown and the pixels which are the same are classed as white and transparent. (White and transparent instead of their normal colour and transparent to improve the compression)

If you can get a PNG lib, you could probably convert the data into a byte array and send that.

Paul

---

### Post by worksofcraft on 2011-02-08
> **PaulM1985 said:**
> I am currently looking into something similar with Java.  I have found that, so far, sending multiple frames of RGBA PNG files works ok, where only the changes are shown and the pixels which are the same are classed as white and transparent. (White and transparent instead of their normal colour and transparent to improve the compression)

If you can get a PNG lib, you could probably convert the data into a byte array and send that.

Paul

... thanks for that info, so the Java streams are not trying to translate your binary data into utf8 strings or anything annoying like that :)

After studying C++ streams at length I've concluded that they include a huge amount of bagage right in the very basic_istream and basic_ostream base classes. These streams are well and truly designed for the purpose of formatting text I/O in locale dependent ways.

I can bypass that with a binary mode but decided I'm better off cutting straight to the low level C file I/O and making a template based interface for creating conceptual "pipes" that can then mostly get optimized out by the compiler :)

[libjpeg]("http://www.ijg.org/") and [libpng]("http://www.libpng.org/pub/png/libpng.html") both work directly with the lower level C functions and so does [gstreamer]("http://gstreamer.freedesktop.org/documentation/") which I'm hoping to make some plugins for at some stage.

---

### Post by PaulM1985 on 2011-02-08
I guess you could try and manipulate a byte array into a char array and pass that, then have something on the other side which will convert it back to a byte array.

Paul

---

