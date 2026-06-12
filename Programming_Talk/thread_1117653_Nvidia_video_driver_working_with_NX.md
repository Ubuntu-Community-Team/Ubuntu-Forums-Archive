---
title: "Nvidia video driver working with NX"
date: 2009-04-06
forum: Programming Talk
---

### Post by bdmw1 on 2009-04-06
I need to write a program which will make use of the new Nvidia driver for H.264 video decoding. I want to setup a NX server where 3 developers will share it as the development machine and to execute the program on. Now, my questions are as follow:

1) Assuming that I installed the Nvidia video card on the server and three of us can time-share the video card. Would this setup work well under NX? i.e. Could the video be seen on the client machine?

2) Assuming that I installed 3 Nvidia video card on each of the client machines, can I make use the video card on the client to do the decoding while the program is executed on the server?

When I tried 1) above, and execute my program on the NX Client, I got the following error msg:

>>> Xlib: extension "NV-GLX" missing on display ":1008.0".
>>> after vdp_device_create,vdp_st=1
>>> Segmentation fault (core dumped)

When I type "xvinfo" on the terminal, it outputs

>>> X-Video Extension version 2.2
>>> screen #0
>>> no adaptors present

Any help is greatly appreciated.

---

