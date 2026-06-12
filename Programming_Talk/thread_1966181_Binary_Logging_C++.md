---
title: "Binary Logging C++"
date: 2012-04-26
forum: Programming Talk
---

### Post by Kentucky88 on 2012-04-26
I need to log a lot of data to a file.  I achieved good compression by logging in binary instead of ASCII, but I am currently logging each piece of data in a multiple of bytes.  In some cases, I do not need a full byte to encode a field and in other cases, I need a little more than a byte, but less than 2 bytes.  I could gain extra compression if I use bits instead of bytes as my lowest common denominator storage unit.  I know how to do this using bit shifting and masking (C++), but I figured that maybe someone knows of a good open source binary encoder / decoder for C++.  Or is there a better way to do this?  I think there is a way to feed the binary output stream into a zip compressor, but I figure that an intelligently-designed binary encoding stream can do just as well with lower CPU overhead.

---

### Post by 11jmb on 2012-04-26
Why re-invent the wheel? Unless you have an academic interest in data compression algorithms, just use gzip or bzip2.

EDIT: Now that I think of it, even if you do have an academic interest in data compression algorithms, the gz and bz2 source code might be good starting points :)

---

