---
title: "[C/C++] Restart Network Interface using ioctl() calls"
date: 2011-05-14
forum: Programming Talk
---

### Post by akora on 2011-05-14
Hi, Im looking into some network programming stuff and am stuck trying to figure how to restart a system's network interface just by using ioctl() calls. 

It is similar to using the command 'ifconfig <dev> <up/down>. I just want to understand how the command works. 

I have looked through ifconfig's source code and have narrowed down to setting device flags. But I am still very much confused as which part of the source code actually brings the device interface down and up. I hope someone can help me out here.

Thanks

---

