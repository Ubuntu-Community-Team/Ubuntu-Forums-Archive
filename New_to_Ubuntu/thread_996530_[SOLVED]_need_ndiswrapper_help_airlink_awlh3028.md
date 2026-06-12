---
title: "[SOLVED] need ndiswrapper help airlink awlh3028"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by lincoln32 on 2008-11-28
I tried to follow guides but to no avail. hh 8.04 and had this card and 
hate to waste card and want to learn. I tried ndiswrapper and windows wireless drivers. card is seen in hardware and ndiswrapper file and boot log
and win 98-xp drivers loaded rtl 8185 chipset

---

### Post by Bölvaður on 2008-11-28
Have you tried booting into a different kernel?

You can do it from grub, just pick older version of the kernel from there and see if it works then.

I had similar problem where my wireless broke because of a kernel update and when the next kernel update after that came... I was back in business.

---

### Post by lincoln32 on 2008-11-28
still inop and this is a fresh duel boot install and build for relitive
vista and 8.04

---

### Post by Bölvaður on 2008-11-30
ndiswrapper is fairly simple in use, as you will know if it is trying to be used or not. So if  you find your self in the situation that ndiswrapper is claiming it is using the correct driver and everything looks like it should technically work... check if you can boot into different kernel.

That can be done either by picking old or new kernel from grub.
Or you can try install newer or older ubuntu.

8.10 had improved support fore wireless cards, I suggest you take a look at it before giving up. Not everyone win in the hardware support lottery, but that group is getting smaller and smaller and for me it looks like in less than 5 years all hardware manufacturers would see it in their interest to supply linux with their drivers.

---

### Post by lincoln32 on 2008-12-01
OK you won! I tried 8.10 before and had glitches-failed install so I tryed a
usb 8 gig with 8.10 and card started working so I did the network update
and all seems to work perfect Thanks

---

