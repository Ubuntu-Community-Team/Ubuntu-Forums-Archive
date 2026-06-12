---
title: "streams, C"
date: 2007-03-31
forum: Programming Talk
---

### Post by Louis de Broglie on 2007-03-31
Hi,

I am a bit confused:confused:  about what streams(used for file I/O in C && C++) are. Can anybody clarify it to me?

---

### Post by Jmccaffrey on 2007-03-31
Computers are limited, in common programming you are only allowed to read and write data one "chunk" at a time. Due to this severe limitation, files, and pretty much any other data source, can only really be operated on in small pieces.  To make any logical sense out of a data source, it needs to be processed in order so the designers of the standard template library, for C++, decided to encapsulate the file reading mechanism into the paradigm of a stream.  The stream allows you to read data from a file or other supported data source in order, one piece at a time, and process those pieces in your own program easily and with high portably.

---

### Post by lnostdal on 2007-03-31
try [http://en.wikipedia.org/wiki/Stream_%28computer%29](http://en.wikipedia.org/wiki/Stream_%28computer%29)

---

### Post by Louis de Broglie on 2007-04-03
thanks for your help guys.

---

