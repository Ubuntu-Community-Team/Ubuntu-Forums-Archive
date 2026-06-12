---
title: "USB Headset does not work,  Ubuntu 11.10"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by greenerone on 2012-07-26
Hi,

   My USB head set does not work, It is a freeTalk everyman(r) Head set, commonly distributed by skype, in my 11.10 installation. 

I have been to sound settings and i don't  see the head set there. I have restarted the computer and also tried in pure administrator mode.  I have read posts about changing the loader.conf (5) file but i do not know where that is , what is the true full path to that file or what else can i do.

---

### Post by NikTh on 2012-07-26
Hi , 
you can do some diagnostics.. 
plug in your usb headset and the open a terminal and write ```
dmesg | tail -n 30
``` 
what are the messages ?

Thanks

---

