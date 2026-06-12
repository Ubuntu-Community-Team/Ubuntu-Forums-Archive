---
title: "Broadcom Drivers Ubuntu 12.04"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by zzdawg1 on 2012-08-22
I did the code chili555 told me to (You know what i'm talking about ;) )
And it now says > Proprietary Drivers are being used to make your computer work properly But wireless isn't available????

Help?

---

### Post by anewguy on 2012-08-23
I'm a little confused - you say chili555 told you do something, but yet the only post for your userid is this post.

So, why don't you tell us where the problems initially started, what you have done, and also post back the output of lspci, and we can see if we can go from there.

---

### Post by chili555 on 2012-08-23
Please post:```
iwconfig
lsmod | grep -e b43 -e wl
```I wonder if you also incorrectly installed the STA driver. If wl appears in lsmod, also do:```
sudo apt get remove --purge bcmwl-kernel-source
```Then a reboot should have you going.

---

