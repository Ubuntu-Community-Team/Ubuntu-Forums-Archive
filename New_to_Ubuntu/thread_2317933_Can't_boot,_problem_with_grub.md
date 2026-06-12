---
title: "Can't boot, problem with grub"
date: 2016-03-21
forum: New to Ubuntu
---

### Post by nagy2 on 2016-03-21
Hi, I'm still new to ubuntu...I had problem with grub after using testdisk to retrieve lost data.
I still can't boot to ubuntu... here is there result of boot-repair... any help will be appreciated. 
[http://paste.ubuntu.com/15464840/](http://paste.ubuntu.com/15464840/)

---

### Post by yancek on 2016-03-21
The Ubuntu link below explains several method to re-install Grub from a broken system including with boot repair.  Read through it and make your choice.  Your problem shows on the first line of the boot repair output quoted below:

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

> Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of the same hard drive for core.img. core.img is at this location and looksfor (,msdos6)/boot/grub.

As you can see, it is looking for Grub files on sdb6 and as you can also see, you do not have an sdb6.  Not sure how that happened?

---

### Post by fantab on 2016-03-21
Yep, as suggested, you need to re-install Grub... If you have a Ubuntu on USB or DVD then [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd) could help... 
[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") is also an option.

---

### Post by oldfred on 2016-03-21
You also have MBR partitioning with two FAT32 partitions. And one is used as an ESP - efi system partition.
While you can boot in UEFI mode from MBR, the live installer is often configured that way, it is extremely rare to see an install with UEFI boot and MBR(msdos) partitions. UEFI uses gpt as its standard.

Was system BIOS boot before?
If so be sure to boot Boot-Repair in BIOS mode.
And see if then it can install grub.
If still not mounting partitions, they may also need fsck to repair issues after recovery.

run on all your ext4 partitions:
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

