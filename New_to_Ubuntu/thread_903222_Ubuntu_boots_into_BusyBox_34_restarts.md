---
title: "Ubuntu boots into BusyBox 3/4 restarts"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by csk1007 on 2008-08-28
So, I installed Ubuntu 8.04 x64, my setup is as follows.

Intel E8400
nVidia 8800GT
4GB Ram
400GB WD HDD

So, whenever I restart my computer, Ubuntu start up logo comes up, and hangs for maybe a minute or two, then BusyBox 1.1.3 starts up. I hit the power button and restart the computer, and I have to do this 4 or 5 times for Ubuntu to actually load. Any hints as to why this is happening?

I successfully (I think) installed nVidia drivers using Envy (after about 10 or so unsuccessful attempts with different methods). But anyways, I think Ubuntu recognizes the card. It lets me boot into native resolution for my screen (1680 x 1050) when it does start. But I have a feeling it might still be because of the video driver issue.

Any help is appreciated!

Thanks!

---

### Post by Titan8990 on 2008-08-28
Dropping into the Busy Box shell usually has to do with a motherboard BIOS that is not fully compatible with Linux.

Are you booting to the live CD or an installation?

---

