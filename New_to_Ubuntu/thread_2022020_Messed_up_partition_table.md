---
title: "Messed up partition table"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by John789 on 2012-07-10
Hi! Recently, I made the switch to just ubuntu instead of dual booting with win7. So i wiped the hdd and made partitions with a Gparted live cd. I then tried to boot up the live usb, but then comes the problem. While booting is see many partitions (up to 150 partitions!). Then kernel panics due to `out of memory´ error. I tried to boot gparted in failsafe mode but it still fails to boot (out of memory issue). Any advice on this matter? The hdd is completely empty, no os installed.

---

### Post by Ubun2to on 2012-07-10
If you have another computer, attach your hard drive to it via USB and wipe it a second time.
Also, you might want to burn a new CD or USB.

---

### Post by Double.J on 2012-07-10
Hi there!

As ubun2to says you can connect the hdd to another pc, or remove it completely from your current pc's sata connector, boot the live image and then reconnect it. Ideally you would do this externally such as USB/Firewire/eSata.. if you have to reconnect it internally (no other pc or external connections), best to make sure you are grounded to prevent shocks - not too much of a problem on a laptop; you can just push the drive back onto the sata connector usually, but if it's a desktop double check that there's no other way to do it, then only disconnect/reconnect the sata connector, not the power one;)

Out of interest what partition table (MBR/GUID) did u use, and how many partitions did you make?

---

### Post by SlugSlug on 2012-07-10
you could use something like killdisk to wipe the hard drive

[http://download.cnet.com/Active-Kill-Disk-Hard-Drive-Eraser/3000-2092_4-10073508.html](http://download.cnet.com/Active-Kill-Disk-Hard-Drive-Eraser/3000-2092_4-10073508.html)

---

### Post by John789 on 2012-07-10
> **gnu/mirow said:**
> 
Out of interest what partition table (MBR/GUID) did u use, and how many partitions did you make?

MBR, I made 3 primary partitions and an extended containin 3 more logical partitions.

Thanks for the replies! I will try to boot up the pc with the live usb without the hdd conected. I might try killdisk aswell. I will let you guys know whether is was a succes or not. :D

---

