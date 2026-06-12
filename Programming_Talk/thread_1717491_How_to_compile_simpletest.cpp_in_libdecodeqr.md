---
title: "How to compile simpletest.cpp in libdecodeqr"
date: 2011-03-29
forum: Programming Talk
---

### Post by ras123 on 2011-03-29
Hi,
I need to write a program to decode qr code images, so I installed the libdecodeqr libraries. I got an example file from the website

[https://github.com/josephholsten/libdecodeqr/blob/master/examples/simple/simpletest.cpp](https://github.com/josephholsten/libdecodeqr/blob/master/examples/simple/simpletest.cpp)

I installed opencv and compiled using 

g++ `pkg-config --libs --cflags opencv` simpletest.cpp 

but I got the following errors,
> /tmp/ccB9Crr9.o: In function `main':
simpletest.cpp:(.text+0x4e): undefined reference to `qr_decoder_open'
simpletest.cpp:(.text+0x76): undefined reference to `qr_decoder_decode_image'
simpletest.cpp:(.text+0xa4): undefined reference to `qr_decoder_get_header'
simpletest.cpp:(.text+0xdf): undefined reference to `qr_decoder_get_body'
simpletest.cpp:(.text+0xf7): undefined reference to `qr_decoder_close'
collect2: ld returned 1 exit status


Now I manage this problem by
gcc `pkg-config --libs --cflags opencv` simpletest.cpp /usr/lib/libdecodeqr.a 

But I couldn't get the expected results. It doesn't decode anything. The messages are
> libdecodeqr version 0.9.3 ($Rev: 42 $)
STATUS=2089


Hit any key to end.

Ras

---

