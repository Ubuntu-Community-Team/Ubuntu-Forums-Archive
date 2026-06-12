---
title: "ubuntu install problems"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by kpiper1993 on 2008-08-27
Hi,
I am trying to install ubuntu 8.04 on my pc for the first time and am having some problems.  The installation worked fine but when I booted up my system to use it for the first time, the logon screen was messed up.  It was freaking out.  there were like duplicates of everything and it was shaking.  Why is it doing it?
Thanks

---

### Post by niccholaspage on 2008-08-27
We Can't help you unless you tell us your Computer Specs.We Need them if were gonna go somewhere.

---

### Post by Thelasko on 2008-08-27
Your video card likely needs it's driver setup.  What kind of video card is it?

---

### Post by OffAxis on 2008-08-27
Did the liveCD do that?
Does it do it in 'Safe-Mode'?
It could be a mis-configured video card, monitor, etc.

try
```
sudo displayconfig-gtk
```

---

### Post by kpiper1993 on 2008-08-27
Wow, thanks for replying so fast.  My video card is ATI RADEON® Xpress1150 256MB HyperMemory.  I think it was actually the alternate desktop iso I used.

---

### Post by kpiper1993 on 2008-08-27
OK, I tried it with the Live CD Desktop version and even in the try without affecting your info thing it still was freaking out.

---

### Post by falcon61102 on 2008-08-27
Sounds like Ubuntu is having an issue with your video card.  It may just mean that you need to install new drivers for it.  Normally when you first start it up and see the GRUB, the second option in the GRUB is to start up in Recovery Mode.  Try booting that and seeing if you can't get a stable screen there and then you can work with adjusting your settings to work.

---

