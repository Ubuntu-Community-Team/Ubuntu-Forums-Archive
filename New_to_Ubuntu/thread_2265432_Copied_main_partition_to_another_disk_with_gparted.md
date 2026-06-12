---
title: "Copied main partition to another disk with gparted, but can't boot it"
date: 2015-02-15
forum: New to Ubuntu
---

### Post by guy50 on 2015-02-15
I'm trying to clone my disk to an external drive, which is smaller.  To do so, I shrunk my partition using gparted live disk, then copied it to the external drive.  However, I can't boot the external drive. It says no boot sector found during on usb device when I try to boot off usb.  I tried installing grub using `sudo grub-install /dev/sdb` where `sdb` is my external drive. The command finished without error but I still get the no boot sector message.  How can I boot my system off the external drive?  Thanks  (using lubuntu 14.04)

---

### Post by sudodus on 2015-02-15
Welcome to the Ubuntu Forums :-)

See this link (I think you need to point to the boot directory in the external drive when installing grub)

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

-o-

In BIOS mode:

An alternative is to use the [One Button Installer]("https://help.ubuntu.com/community/OBI")

 - make a tarball
- install the system from that tarball into the external drive

but if the partition is copied in a correct way, it should work by installing grub in a correct way. If a swap partition is referred to in /etc/fstab, you need to create one with the correct UUID in the external drive or to remove that reference (put a comment **#** character at the beginning of the line). There might be another complication, that the copy of the partition has the same UUID as the original partition, and Lubuntu will get confused what to use if the drives with both partitions are connected.

So if you have problems, it might be better to use a tool like the One Button Installer, or to

- create new partitions on the external drive, and
- copy all files of the root partition with ***rsync*** and
- fix the reference UUIDs in **/etc/fstab** and **/boot/grub/grub.cfg** and
- finally install the bootloader (grub-install).

In UEFI mode:

Maybe the following tip might help you
[URL="http://ubuntuforums.org/showthread.php?t=2265433"]
Repair - Restore or Reinstall Grub 2 with a Ubuntu Live CD or USB[/URL]

But it is often much more difficult to make things work in UEFI mode, and maybe you should make a ***fresh installation*** instead of trying to copy/clone a partition and make it work.

---

