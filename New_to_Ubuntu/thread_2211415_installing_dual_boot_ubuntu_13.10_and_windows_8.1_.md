---
title: "installing dual boot ubuntu 13.10 and windows 8.1 on asus s400ca"
date: 2014-03-15
forum: New to Ubuntu
---

### Post by andrew99 on 2014-03-15
Hey my problem is that there is no option in ubuntu installer to dual boot windows there is however another choice to resize partitions.  I have the ultrabook asus s400ca with 6gb of ram and 24gb of ssd and i5.  When I go to computer my partitions are as follows on disc 0 there are 6: 300MB efi system partition, 600mb recovery partition, 185gb os c ntfs, 350 healthy recovery partition, 258gb data d: ntfs, and 20.01gb  recovery partition.  For disc 1 I have 6gb oem partition, 16.36gb primary partition.

Ok so I have only used 460mb of the 258gb data d: ntfs partition.  I would like to resize that one and use it for the ubuntu.  My c drive will be plenty for my use I have only used 70gb of the 185gb.  My question is I don't want to rush in to things and if someone can just give me a step by step so I don't mess up my computer I would greatly appreciate it.  Also I am able to boot into ubuntu 13.10 through my usb and it works fine I want to dual boot it with windows and partition it correctly.

---

### Post by Bashing-om on 2014-03-16
andrew99; Hi ! Welcome to the forum.


Be aware I am not conversant with Windows, not UEFI, but as a place to start ->
Show us what we are, in fact, working with;
Post back the output - between code tags - of terminal commands:
```

sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then a plan may be formulated in accordance with your desire.

[INDENT]it is 'buntu
[INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-03-16
Before with Ultrabooks with Intel SRT, we had to turn off SRT and remove RAID metadata from both drives. Now it seems to work to install, but grub may not install correctly. But then Boot-Repair can usually fix it.

Are you primarily a Windows user and want to keep the Intel SRT, or would you like a fast Ubuntu and install / (root) to the 24GB SSD but then not have SRT?

You need to turn off SRT, and fast boot with Windows. Often better to turn off secure boot also.

Also better to shrink Windows a bit more and have a separate shared NTFS data partition as read/write and only read from the Windows system or c: drive. You still need to keep fast boot off as in Windows there does not seem to be a way to unmount the d: drive which the data partition will be seen as.

Either way a 20 to 25GB / partition (on SSD or hard drive) and however large you want to make ext4 /home and a NTFS data partition on hard drive should be the minimum requirements.

Always resize partitions with Windows disk tools and immediately reboot to let it run chkdsk and make it repairs to its new size. Double check that fast boot is off and then install Ubuntu into unallocated space. If you are a new Ubuntu user just / (root) and swap as default install into unallocated would be fine. If a bit more advanced then the separate /home and/or data partitions would be suggested.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
  Ubuntu now installs with Intel SRT on, but when grub sees the RAID grub will not install. So you have to turn the SRT off and remove the RAID meta data from the drives. Some install Ubuntu to SSD, others install to hard drive and turn SRT back on and have had it work.
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)
Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Uses larger SSD for both Intel SRT & Ubuntu
[http://ubuntuforums.org/showthread.php?t=2129157&page=2](http://ubuntuforums.org/showthread.php?t=2129157&page=2)
Screenshots of SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

Above from links in my signature, more info also there.

---

