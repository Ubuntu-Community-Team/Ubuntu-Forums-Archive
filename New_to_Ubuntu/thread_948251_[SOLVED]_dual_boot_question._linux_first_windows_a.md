---
title: "[SOLVED] dual boot question. linux first windows after?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by e1ektrob0y on 2008-10-15
I have always installed windows first then linux after for a dual boot. i have been running ubuntu by itslef for quite a while now and i want to unstall vista on a spare hard disk that i have. i am wondering if i install windows after i have already installed linux will grub still work etc?? thanks :)

---

### Post by SunnyRabbiera on 2008-10-15
Windows installation after installing ubuntu is a big issue, it will want to wipe out grub and take over the entire drive.
Its much easier to install linux after windows then to install windows after linux.

---

### Post by e1ektrob0y on 2008-10-15
> **SunnyRabbiera said:**
> Windows installation after installing ubuntu is a big issue, it will want to wipe out grub and take over the entire drive.
Its much easier to install linux after windows then to install windows after linux.
yes i know this. but it is on a second hard drive. the hard disk with ubuntu on it will remain un-touched *crosses fingers*

---

### Post by louistan3 on 2008-10-15
windows after linux can be done though, most of the time grub will be overwritten by ntldr.. but you can easily fix this with a live cd.. 

just do a search on google for fixing grub with live cd or something like that..

hope that helps :)

---

### Post by SunnyRabbiera on 2008-10-15
> **e1ektrob0y said:**
> yes i know this. but it is on a second hard drive. the hard disk with ubuntu on it will remain un-touched *crosses fingers*

you still may have to play around with grub though

---

### Post by louistan3 on 2008-10-15
i just read your reply, if your installing it on another hd, then it should be fine..

all you have to do after is add the windows drive into grub and should boot right up..

---

### Post by e1ektrob0y on 2008-10-15
> **SunnyRabbiera said:**
> you still may have to play around with grub though

Yea ok that makes sense. thanks...so more than likely windows will work but i wont be able to boot to linux until grub is fixed yes?

---

### Post by hyper_ch on 2008-10-15
if you want to install vista on a seperate drive I think that's the "safest" way:

(1) unplug your linux drive(s)
(2) install vista - it will write its bootloader to its own drive and not touch the linux drives
(3) attach the linux drive again, make sure bios boots from it
(4) when back in linux open a terminal and issue
```

sudo fdisk -l

```
to find out what your vista drive is... probably /dev/sdb is the drive and the vista install partition is /dev/sdb1
(5) then go to /boot and copy the vista bootloader over
```

cd /boot
sudo dd if=/dev/sdb of=/boot/vistambr bs=512 count=1

```
make sure you don't enter a partition but a drive as if!
(6) edit grub and add
```

title        Windows Vista
root         (hd1,0) # count here starts at "0", so drive sdb --> 1 (as sda --> 0) and as it's in the first partition of sdb it "0")
savedefault
makeactive
chainloader  (hd0,0)/boot/vistambr # this time you have to enter drive and partition and path of your /boot folder. If you don't have a seperate /boot partition it's very likely to be 0,0 and /boot/

```

---

### Post by e1ektrob0y on 2008-10-20
> ben@ben-desktop:/boot$ sudo dd if=/dev/sdb of=/boot/vistambr bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000275233 s, 1.9 MB/s

have i done this correctly?
also how do i edit grub? sorry i really don't want to mess it up and not be able to boot to anything :) thanks

---

### Post by e1ektrob0y on 2008-10-20
ok no worries i just edited /boot/grub/menu.lst and it works :D thanks heaps much appreciated...

---

