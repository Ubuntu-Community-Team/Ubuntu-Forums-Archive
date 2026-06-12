---
title: "xserver hangs up after installing self-compiled evtouch"
date: 2010-02-11
forum: Packaging and Compiling Programs
---

### Post by dyonisos on 2010-02-11
Hello,

I have some problems using xserver-xorg-input-evtouch when compiling it from sources with Ubuntu 8.04.

To compile I have first installed build dependencies via
*sudo apt-get build-dep xserver-xorg-input-evtouch* .
After that I have installed sources by
*apt-get source xserver-xorg-input-evtouch* .
When trying to compile via
[I]./configure
make[/I]
I got a compile error because a debug instruction in evtouch.c seems to be corrupted, so I commented out the affected line. After that compiling worked.

If I now try to use the so compiled driver - without having done any changes except this debugging line - xserver hangs up. I get a black screen and when doing a restart I even only get a black screen after the ubuntu splash-screen after booting.

Using the driver directly from the debian package works. But unfortunately I have to do some changes on it so I have to get the driver even running if I compile it from source.

Does anybody have an idea how to do further debugging or just better have a solution for my problem?

---

