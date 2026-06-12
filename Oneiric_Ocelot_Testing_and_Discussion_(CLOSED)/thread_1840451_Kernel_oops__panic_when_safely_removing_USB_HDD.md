---
title: "Kernel oops / panic when safely removing USB HDD"
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by pressureman on 2011-09-07
My Thinkpad T500 has been exhibiting this problem for a couple of weeks now, where if I click the icon to eject a USB HDD, I get a kernel oops, or in some cases a panic.

It's being discussed on Linux Mint forums ([http://forums.linuxmint.com/viewtopic.php?f=141&t=75848&p=455982](http://forums.linuxmint.com/viewtopic.php?f=141&t=75848&p=455982)) and by the sounds of it, it's a kernel problem that affects several distros.

I was curious if anybody else had noticed this yet. The disks I'm using are:

Seagate 500 GB "Expansion Portable Drive" (only kernel oopses so far)
WD My Passport 1TB (several kernel panics)

It seems to be less likely to occur if I click the eject icon in Nautilus, which only unmounts the filesystem, without powering down the drive. If I click the eject icon from the "removable drives" systray icon (Gnome Shell, lower right corner), that appears to also attempt to power down the drive, and that seems to be where the problems start.

The Seagate is formatted with two partitions, one NTFS and one ext4/LUKS. The WD is so far just a single NTFS partition.

---

### Post by mc4man on 2011-09-07
Have seen some off & on issues for most of O w/ 3 usb hdd's here, 2 w/ their own power switch, 1 without. (mainly occasional desktop crashers previously
Haven't had a chance to ck. the others recently  but w/ a seagate I get a kernel panic when using safely remove about 40 % or so of the time on a newish Beta 1 updated install. 
Tried 5 times, 3 good, 2 panics, once a boot hang after the panic w/ the drive still connected and powered on
(the seagate has it's own power switch

---

### Post by mc4man on 2011-09-07
Sort of a follow up - (though should test other drives, lazy atm

Not sure about mint, ect. but never saw any Kp's with Sm in natty and none in O till fairly recently. So maybe it's some kernel deal but - 
At least here there seems to be some relationship of the Kp's to g-s-d and more specifically 'gnome-fallback-mount-helper'

So with the current g-s-d I seem to actually get a Kp almost 1/2 the time on Sm. If I prevent the gnome-fallback-mount-helper process from running I get a Kp when using Sm -  never.
Now without the process media has to be click mounted in nautilus after connecting  , maybe a factor, maybe not


Edit: same w/ another external (WD
This helper started showing up about 6 wk.s ago, don;t recollect any Kp's that far back

---

### Post by sonicb00m on 2011-09-08
I have the same problem ejecting USB disks when using NTFS partitions.

---

### Post by mc4man on 2011-09-11
Very obvious with today's daily in a live session - immediately get thrown to a Kp screen.
So while maybe not a defect in g-s-d, it's (the helper) adversely affected.
(filed against g-s-d, will see where that leads, if anywhere.

---

### Post by pressureman on 2011-09-11
Can you please post the bug ID?

---

### Post by mc4man on 2011-09-11
sure - 
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/844957](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/844957)

( I did go back aways with O's kernel packages, though not that far, see the same. I guess I may try another couple before dumping this install, it's just a bit of a pita with nvidia-current

---

### Post by lucazade on 2011-09-16
experienced this bug today with a lenove usb hdd. weird!

---

### Post by mc4man on 2011-10-12
The test kernel has fixed this here, testing on 3 drives

---

### Post by ventrical on 2011-10-12
All is well here with my USB2.0 to IDE&SATA Cable.

But I thought it kind of strange that the pop-up prompt said <eject> rather than <safely remove>.

---

### Post by suprman2020 on 2011-10-12
I've been having this problem since I started using Oneiric. I haven't tested to see if recent updates have fixed the problem.

---

### Post by mc4man on 2011-10-12
> **suprman2020 said:**
> I've been having this problem since I started using Oneiric. I haven't tested to see if recent updates have fixed the problem.
The new kernel that has fixed here is not yet in repos & won't be until after release.
Bug report & link to test kernels if interested (links in comment 20
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/844957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/844957)

---

### Post by suprman2020 on 2011-10-12
> **mc4man said:**
> The new kernel that has fixed here is not yet in repos & won't be until after release.
Bug report & link to test kernels if interested (links in comment 20
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/844957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/844957)

Thanks!

---

### Post by mc4man on 2011-10-12
> **suprman2020 said:**
> Thanks!If you find the new kernel doesn't help you then feel free to post a comment in that bug report

(has fixed on 3 different usb hdd's here

---

