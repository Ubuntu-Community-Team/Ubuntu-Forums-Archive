---
title: "Unmounting drives?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by NathanDC on 2008-11-04
I need to create a new partition and delete one I accidentally created. I can't delete it because I get a mount error. I am booted in the live cd. How do I unmount a partion? The options in gparted is greyed out. Do I need to do this outside in ubuntu itself outside of livecd?

---

### Post by taurus on 2008-11-04
You can unmount it from the LiveCD.  Assuming it's mounted to /media/disk, you can unmount it with

Applications -> Accessories -> Terminal
```
sudo umount /media/disk
```
Make sure you close gparted first before you run that command.

---

### Post by NathanDC on 2008-11-05
thanks :). I'll give it a shot.

---

### Post by NathanDC on 2008-11-05
hrmm...the terminal said that command is not found.

---

### Post by rakris on 2008-11-05
> **NathanDC said:**
> hrmm...the terminal said that command is not found.

You better use the device name (eg: /dev/[sh]da) instead of mount point for umounting. Or check the actual mount point

---

### Post by NathanDC on 2008-11-05
I had to turn the swap partition off on the drive I was manipulating. That solved the problem.

---

### Post by bodhi.zazen on 2008-11-05
The only partition automatically mounted by the live CD is swap.

So you can either unmount it from gparted (there is an option somewhere on the menu) or if the gui tools fail you, the command line :

```
sudo swapoff /dev/sdxy
```

Where sdxy = your swap partition (guessing sda5 ?).

---

