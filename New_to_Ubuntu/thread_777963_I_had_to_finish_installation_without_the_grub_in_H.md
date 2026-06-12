---
title: "I had to finish installation without the grub in Hardy"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by captgadget on 2008-05-01
Now how do I get it running? I reboot and get: no boot file name received Stike F1 to retry

---

### Post by nofrendo on 2008-05-01
Put in the liveCD, open a terminal and do:

sudo grub

root (hdX,Y)
setup (hd0)
quit


X,Y=the partition that you have Hardy on, GRUB recognized 0 as the first number, so for example you have Hardy on /dev/sda1, you would do root (hd0,0)

if you had Hardy on, say /dev/sdc4, then it would be root (hd2,3)

---

