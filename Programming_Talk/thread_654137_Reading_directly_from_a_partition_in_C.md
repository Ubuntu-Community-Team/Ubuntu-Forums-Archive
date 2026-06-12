---
title: "Reading directly from a partition in C"
date: 2007-12-30
forum: Programming Talk
---

### Post by MikeBenza on 2007-12-30
I'm trying to read directly from a partition, /dev/sda1.  When I try to read though, I get different data than I see at the beginning of the partition in hexedit.  Any clues on how to read byte for byte from a partition?

- Mike

---

### Post by yabbadabbadont on 2007-12-30
Look at the source code for hexedit and see how they do it.  ;)

You should probably post the code that you are using to open the device and read from it.

---

### Post by MikeBenza on 2007-12-31
The problem I was having was that I wasn't running the resulting application with sudo, so it was reading (I suppose) the first user-accessible part of the partition, rather than the first super-user accessible part.

---

