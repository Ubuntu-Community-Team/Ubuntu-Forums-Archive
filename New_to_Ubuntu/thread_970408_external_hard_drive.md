---
title: "external hard drive"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by skiddly on 2008-11-04
When i turn my external hard drive on it shows as drive same as c drive in windows, so why can i not install ubuntu on an external hard drive and run it from there, or can i, i do hope to get another internal hard drive installed later and put it on there so ill be back to ask how to do that later colcol

---

### Post by skiddly on 2008-11-04
as an after thought if i just have ubuntu on existing drive can i put another distro on external hard drive to boot from there

---

### Post by Peter09 on 2008-11-04
Well any easy way to test would be to run up the liveCD and see if your external drive is accepted as a target. 

I suggest you do not actually install until someone comments who has done this. The risk would be that grub would get confused about using the external drive as a boot target and you would not be able to boot anything.

This situation would be recoverable - but it is worth getting more comments.

---

### Post by wizard10000 on 2008-11-04
If your computer will boot from an external drive you certainly can install Ubuntu on it - or even if it won't  :)

If the machine will boot from the external HD then put grub on the external drive - if it won't then you'll need to put grub on the internal drive or configure the machine to use a Windows bootloader (which would be my first choice if it won't boot from the external drive).

One thing to watch - it's getting a lot better now but a lot of older motherboards' USB ports only ran at USB 1.1 until the OS loaded a USB 2.0 driver - if yours is an older PC the thing might be painfully slow booting.

---

