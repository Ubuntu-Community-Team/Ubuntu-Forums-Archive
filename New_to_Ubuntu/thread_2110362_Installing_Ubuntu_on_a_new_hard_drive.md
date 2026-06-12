---
title: "Installing Ubuntu on a new hard drive"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by dolphin194 on 2013-01-30
So I have this computer with Windows 7 on a 256GB SATA hard drive. If I install a new hard drive into the machine and install Ubuntu on it, will I lose the ability to boot my Windows 7 from the other hard drive, or will the boot loader automatically find Windows 7 if it's on a different disk?

---

### Post by mapes12 on 2013-01-30
The short answer is yes Ubu will detect your windoze OS.

You will need to select the advanced option when you get to the partitioning section of the installation and tell the installer where you want to install Ubu. Personally, I would set up my partitions ahead of the installation to make the process easier. The installer will detect your windoze installation no matter what drive it's on (Linux detects "devices").

I'm not sure where Grub ends up being installed so I'll leave that one to others if it's a concern for you.

---

### Post by deadflowr on 2013-01-30
If everything is correctly attached, then grub should have no problem probing the windows hard drive and then when booting giving you the option to boot win7.

I prefer having windows and Ubuntu on separate hard drives, so I don't mess either up if I decide to fiddle around.

The great thing about having them on separate drive is that if the grub bootloader fails, simply removing the Ubuntu disk should let you still run the windows disk, as grub chainloads into the windows bootloader.

But, remembering the question at hand, run sudo update-grub, and look over whether or not windows shows up in the generated list.
It most likely should, but if it doesn't look at the /etc/default/grub file to see if any settings for os probing are  set.
I think that was at one time a setting in that file, but I'm not sure.

---

### Post by sudodus on 2013-01-30
Disconnect the windows drive while installing Ubuntu, if you want to be sure that grub is installed on the Ubuntu drive. 

After installation, connect it again and do what is necessary to make the Ubuntu drive selected for boot. This will be different on different computers: switching sata ports, changing boot order in the BIOS menu (or equivalent for non-bios systems).

Then when booted into Ubuntu, run the terminal window command ```
sudo update-grub
```
It should find Windows, and make a boot entry for it. After reboot you will find a line to choose in the grub menu also for Windows.

---

### Post by dolphin194 on 2013-01-30
It really doesn't matter where GRUB gets installed to, I just want to be able to have each OS on a different disk. Anyway, thanks for the quick responses everyone, I shall be installing Ubuntu.

---

### Post by furything on 2013-01-30
Follow what sudous is saying.

I sort of do similar when I create dual boot. 

If you write grub to the windows drive, removing the linux drive will cause it to fail to boot into windows. For windows you require the MS master boot record (MBR) and would have to rewrite the MBR to get it to work.

If you leave windows intact with the MBR, then remove linux drive, it still boots. The easiest way to leave the windows MBR alone is do what sudous suggests.

You don't have to remove the windows drive from the case just disconnect the data cable or power cable, or in the BIOS tell it the IDE or sata connection that refers to the windows drive is disabled.

---

