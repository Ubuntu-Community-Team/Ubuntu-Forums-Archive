---
title: "libav tutorial, undefined reference to `img_convert'"
date: 2013-06-17
forum: Programming Talk
---

### Post by ras123 on 2013-06-17
Hi,
I am trying to compile the tutorial provided here, 

[http://dranger.com/ffmpeg/tutorial01.html](http://dranger.com/ffmpeg/tutorial01.html)

Since it is old, I make changes as required, but I coudn't solve the problem "undefined reference to `img_convert' ", when compiling, I used the following to compile it, 

gcc -o tutorial01 tutorial01.c -lavutil -lavformat -lavcodec

where library contains the img_convert ?

Thanking You,
Ras

---

### Post by FakeOutdoorsman on 2013-06-17
swscale API has replaced img_convert. See a version of the guide with [updated source code](https://github.com/chelyaev/ffmpeg-tutorial). May provide some clues.

---

