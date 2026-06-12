---
title: "Ubuntu 12.04 RTL8192cu keeps loading after blacklisting"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by jeffrey123 on 2012-10-21
Hello again!

I switched from xubuntu to ubuntu, but somehow the rtl8192cu keeps loading.

I followed the exact same steps as i did in xubuntu,
[http://ubuntuforums.org/showthread.php?t=2058669](http://ubuntuforums.org/showthread.php?t=2058669)

When i type: sudo lshw -c network
I see driver=rtl8192cu

While i got the rtl8188cus. 

i tried blacklisting:
blacklist rtl8192cu
blacklist 8192cu
blacklist rtl8192cu_usb

But none of that works somehow.
What am i doing wrong??

---

