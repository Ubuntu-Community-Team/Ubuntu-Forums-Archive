---
title: "unetbootin help"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by Dominic_Bond on 2013-08-03
hi, I am trying to install Windows 7 Home Premium 64 bit along side Ubuntu 13.04 64 bit on my laptop. I am using unetbootin to do this, when I try to do this on my Ubuntu laptop it says there is no flash drive connected or it needs to be reformatted as fat32, my device is already formatted as fat32, so why wont it register it? when I try to use it on a Windows XP 32 bit notebook it can find the device and once unetbootin is complete the USB drive isn't bootable still as when I insert it into my laptop it starts up but goes in an endless loop saying starting installation in 10...9...8...etc...1...10...9... , you get the point. what can I do to make my USB drive bootable? please help!

---

### Post by meilin on 2013-08-03
Try to format your USB drive with the low speed option, then re-install the iso into it. :P

---

### Post by Dominic_Bond on 2013-08-03
how would i go about formatting it with a low speed option?

---

### Post by Vladlenin5000 on 2013-08-03
> **Dominic_Bond said:**
> how would i go about formatting it with a low speed option?

:lolflag: Ignore, it was a joke, probably.
Have you tried a different device? Maybe the one you're using has some problem. Also you can try to format if again or - even better - use gParted (or other similar tool) and first remove all partitions of that drive (probably just one) and create a new FAT32 one.

---

