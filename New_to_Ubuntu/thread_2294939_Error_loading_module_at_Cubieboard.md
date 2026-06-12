---
title: "Error loading module at Cubieboard"
date: 2015-09-14
forum: New to Ubuntu
---

### Post by Leonardo_David on 2015-09-14
Hi
I am having a hard time to load this driver on cubieboard. What happens is that I'm compiling the driver sources in Cross using Ubuntu 15.04 x64 with Tool Chain arm-linux-gnueabihf, which returns me a file .ko that is the module to be loaded into Cubieboard v1 (A10).
I followed all the steps of this procedure;


[http://hs8jcv.blogspot.com.br/2014/05/build-kernel-linux-sunxi-for-cubieboard.html](http://hs8jcv.blogspot.com.br/2014/05/build-kernel-linux-sunxi-for-cubieboard.html)


Cubieboard image: Fedora-18-a10-armhfp-r1.img
Kernel: 3.4.29.sun4i
Kernel-devel direct on Cubie generates a 3.10.14-100.fc18.armv7hl kernel that does not work to build the driver on the board. The only kernel that works to compile the driver is sunxi from Ubuntu x64.


The driver is from a biometric sensor. The Makefile asks the kernel directory and the cross compile.


The driver build occurs normally and the .ko file is generated. But whenever I give the command **sudo modprobe fortscancam **at the cubieboard, I get the message: **ERROR: could not insert ****fortscancam****: Exec format error.**


I am very grateful for any help.

---

