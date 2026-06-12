---
title: "USB install of Ubuntu can't see Windows drive anymore?"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by aonghus2 on 2014-04-17
Hey everybody!

Sorry to be asking for help on my first ever post. I'm a brand-new Ubuntu user with a bit of a problem.

I have a  Dell Inspiron 15 laptop with Windows Vista 64x installed; there's a problem with Windows that won't let me log in, and can't be fixed by a repair install.

I installed Ubuntu 12.05 LTS on USB, and booted the computer from the USB. It loaded fine, and I ws able to see all my files on the C drive for the first time in a year!

However, when I turned the computer off and turned it on again later, the C drive wasn't showing up in the Home folder. I turned it off and on again several imes, with no change


The only things I noticed were:
Ubuntu seemed to hit some sort of error the first time I turned it off, so I did a hard turn-off with the power switch (probably a bad idea.)
When I turned it on the second time, I had plugged in my phone, which showed up as a hard drive when I first noticed the drive with Windows on it was missing.

Any ideas on how I can get access to my Windows drive again? Would it be enough to format the USB stick and put a different build of Ubuntu on it? 

Any help greatly appreciated!

Aonghus

---

### Post by Double.J on 2014-04-17
Hi there!

Welcome to the forums!

Don't worry, we're here to help, and you can to the right place! (You got further than me; my first install of linux 12 years ago had me asking how to partition my drive)

You're absolutely correct; you can try re downloading ubuntu in case there was an issue (it happens; I've installed hundreds of times over the years and every now and then you just get an error that was caused by creating the usb stick.) but ubuntu has had windows support as long as I've used it!

failing that, the next step would be to see if ubuntu can see the windows partition you need. From the live usb, select 'try' and then open a program called gparted; this should show you all the partitions on the disk.

you can also see all the partitions on your disk by opening a terminal with ctrl+alt+t, then typing 
```
sudo fdisk -l[CODE]
 
you can also make ubuntu mount the partition with
[CODE]sudo mount -t ntfs /dev/sdaX /mount
```(X is the partition number, a is the drive letter. This should be shown in gparted or fdisk

Now the last part is important. If you still can't access it, we could be looking at a drive issue and it would be best to move along to data recovery and hardware testing steps than continue to attempt access.

All the best!

Jj

---

