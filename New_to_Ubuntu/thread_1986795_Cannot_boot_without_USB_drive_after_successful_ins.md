---
title: "Cannot boot without USB drive after successful install"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by gmer on 2012-05-25
Hello,

First, apologies for the cross-post, but I have also asked about this problem on "askubuntu.com" [here]("http://askubuntu.com/questions/142004/cannot-boot-without-usb-stick-after-successful-install").

I have installed Ubuntu recently via a bootable USB drive, created with unetbootin. Everything went very well, but now the computer does not boot unless the USB drive is plugged in. If it's not, then when the computer boots, the boot sequence screen just appears and if I select the hard drive, it will just reboot and go back to this boot sequence screen, until I plug in the USB drive.

Having some valuable data on the machine, I would prefer a solution that doesn't involve reinstalling, but I guess this may be what I have to do eventually.

If you go on the link above, you will see the output of a "sudo fdisk -l", and I also have the output of a bootinfo here: [http://paste.ubuntu.com/1006423](http://paste.ubuntu.com/1006423)

Any ideas? Thanks a lot for your help!

G.M.

---

### Post by oklokl on 2012-05-25
[ATTACH]218693[/ATTACH]
mistake

 /dev/sdc
 Or
 / dev / sdb
 You have selected ..

 Automatic / dev / sdc is chosen as the ...

 It
 /dev/sda will need to change.

[http://askubuntu.com/questions/81613/ubuntu-option-disappear-from-grub-11-10-after-update-on-a-dual-partition](http://askubuntu.com/questions/81613/ubuntu-option-disappear-from-grub-11-10-after-update-on-a-dual-partition)
[https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair)
[INDENT]   sudo add-apt-repository ppa:yannubuntu/boot-repair
      sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
 [/INDENT]

---

### Post by gmer on 2012-05-25
Thanks for your reply. 

Sorry I don't think I get what you want to say, but I don't think I have a Windows partition. Anyway, my goal was to install ubuntu on only 1 partition of the hard drive.

Also, I already did a boot-repair/info thing, and the output is there: [http://paste.ubuntu.com/1006423](http://paste.ubuntu.com/1006423)

Thanks!


> **oklokl said:**
> [ATTACH]218693[/ATTACH]
mistake

 /dev/sdc
 Or
 / dev / sdb
 You have selected ..

 Automatic / dev / sdc is chosen as the ...

 It
 /dev/sda will need to change.

[http://askubuntu.com/questions/81613/ubuntu-option-disappear-from-grub-11-10-after-update-on-a-dual-partition](http://askubuntu.com/questions/81613/ubuntu-option-disappear-from-grub-11-10-after-update-on-a-dual-partition)
[https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair)
[INDENT]   sudo add-apt-repository ppa:yannubuntu/boot-repair
      sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
 [/INDENT]

---

### Post by oklokl on 2012-05-25
The image is described.
 Check the red box

Normal position
Grub2
/dev/sda
/dev/sda1


You do not have Grub2.
 Probably / dev / sdc

/dev/sda1
 / 
Ext4
 Ubuntu system, and
 Do not confuse ...


Grub2
 To build a new

---

### Post by oldfred on 2012-05-25
Boot-Info looks normal. You have grub2 booting to sda1.

There was (is) a bug in grub2 that when / (root) partition is very large it gets lost finding files. You do have some files at beginning of partition and some at end.
```

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 532.239356995 = 571.487657984  boot/grub/core.img                             1
 532.239364624 = 571.487666176  boot/grub/grub.cfg                             1
   0.515132904 = 0.553119744    boot/initrd.img-3.2.0-23-generic               2
   2.261756897 = 2.428542976    boot/initrd.img-3.2.0-24-generic               2
 320.134506226 = 343.741808640  boot/vmlinuz-3.2.0-23-generic                  1
   1.411853790 = 1.515966464    boot/vmlinuz-3.2.0-24-generic                  2
   2.261756897 = 2.428542976    initrd.img                                     2
   0.515132904 = 0.553119744    initrd.img.old                                 2
   1.411853790 = 1.515966464    vmlinuz                                        2
 320.134506226 = 343.741808640  vmlinuz.old                                    1

```I have suggested to several users to make / smaller and use a separate /home or separate /data for the rest of the drive. My normal suggestion is only 25GB for / when you have all you data in separate /home or /data partitions.

I also find it interesting that it works with flash drive plugged in. Does that slow down booting so that  hard drive then has time to find files?

Some old BIOS only could boot from the first 137GB and it seems some new systems behave the same. It may be a IDE setting in BIOS or something else in BIOS.

Some have posted these as BIOS issues:

BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Old BIOS, new drive 137GB max boot size
Disable Quickboot in BIOS
turning off UDMA in the BIOS my problem has gone away.(old system & may make system slower)
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues

Sometimes specific issues by motherboard like this:
[Natty] Marvell 88SE9120 IDE-Part not working 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325)
External drive needed separate power supply
Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.

---

### Post by lindsay7 on 2012-05-25
From the boot-repair application. Select advanced options and run the reinstall grub option. Make sure that the usb in not plugged in.

---

### Post by wilee-nilee on 2012-05-25
Have you tweaked grub with the grub customizer, or in another way, perchance?

Have you tried a purge and reinstall? The boot repair has a purge in the advanced.

What I'm noticing here is that helpers who are good at this who have been on line are silent, not sure why, I know I was hesitant as the script looks good.

Might be where grub is on the HD and the 137 gig limit, might be the no boot flag very unusual but saw this two days ago.

---

### Post by oldfred on 2012-05-25
+1 on wilee-nilee's suggestion of boot flag if Intel motherboard/BIOS and maybe a few other systems. 

Grub does not use boot flag, but some BIOS will not let you even start to boot without a boot flag (seems to assume Windows?).

---

### Post by wilee-nilee on 2012-05-25
Hehe, we all posted at the same time. So OP to set the boot flag use gparted, may need to be installed, and right click sda1-flags then boot.

---

### Post by gmer on 2012-05-30
First, sorry for my delay in replying.

I did a boot-repair, ticking "reinstall grub" as well as "purge and reinstall". When I had to reboot, the screen froze and I had to use the power button. But now it boots fine on the hard drive.  I didn't have to make another partition.

To answer one of the question: I didn't seem to see that the boot was slower with this usb problem. As a matter of fact, it seems slower now. The machine has decent specs so maybe I just didn't notice.

Thanks a lot to all of you, it was super helpful and informative.

For info, log of boot-repair: [http://paste.ubuntu.com/1014810/](http://paste.ubuntu.com/1014810/)

PS: <troll> You guys were much more efficient and helpful than those on askubuntu.com!</troll> ;-)

---

