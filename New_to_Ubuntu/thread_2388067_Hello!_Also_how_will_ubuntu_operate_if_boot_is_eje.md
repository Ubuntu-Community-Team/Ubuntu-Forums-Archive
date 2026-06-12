---
title: "Hello! Also how will ubuntu operate if /boot is ejected from the system?"
date: 2018-03-28
forum: New to Ubuntu
---

### Post by krypt1c on 2018-03-28
Hello ubuntu forums! I recently got a surface book 2, and I plan on upgrading the 128 GB with with a 512 GB Samsung 960 evo M.2. I want to dual-boot windows 10 and ubuntu and I was wondering how the system would react if the /boot partition was on a sd card plugged in via the keyboard base and once booted, and I eject the screen, which has the cpu, memory, graphics, sound, / and /home partitions. The reason I ask is, I recently read that it is possible to store the /boot partition on a usb drive, so the system could not be booted unless the drive was connected. I would imagine the /boot partition would only be needed, after booting, for updating kernels or modifying the initramfs. Just curious if anyone knew if it was documented somewhere, google didn't help.

edit: I've been using ubuntu for probably 8 years, the past 2 have been the most active. Still consider myself new, but familiar.

---

### Post by cruzer001 on 2018-03-28
Untried by me, but looks like "BootRepair" would do this.  Your SD card would have to show at the beginning of the boot process for this to work.

[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

---

### Post by C.S.Cameron on 2018-03-29
What use is it to put / on anything but the SSD?
My wife's computer has / on the SSD and /home on a USB HDD.
This boots and opens programs quickly.
I would think that /boot also works fastest on SSD.
Not sure why you would want to remove /boot after booting.
A persistent drive can be unplugged after booting as long as the toram option is used.

---

### Post by 9cddz&amp;mK07%F@ on 2018-03-30
The system can boot fine, if you still have an /boot directory in the root of your hard disk.

---

### Post by C.S.Cameron on 2018-03-30
Just tried a HDD boot with grub on persistent USB drive.
Worked OK.
Once booted was able to remove USB boot drive "safely" without shutting down.
Was able to shut down without problem without /boot drive. 

Don't think this adds much security, many Live USB versions offer to boot hard drive in the boot menu.

---

