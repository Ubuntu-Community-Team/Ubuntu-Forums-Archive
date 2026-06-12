---
title: "Problems booting from external USB drive"
date: 2014-06-17
forum: New to Ubuntu
---

### Post by ian49 on 2014-06-17
I thought I'd have a go at installing Ubuntu on an external 320Gb USB drive. It already had some data on and was formatted with NTFS. I shrunk the existing partition and created about 92Gb of free space. I then rebooted and successfully installed to the free space on the external drive, creating 3 partitions as follows:

/dev/sdb2/ extended
   /dev/sdb5 (ext4) bootable (c. 10Gb)
   /dev/sdb6  swap  (c. 4Gb)
   /dev/sdb7  (ext2)   (c. 80Gb)

Note the disk also has:

/dev/sdb1   ntfs

Anyway, I then rebooted again and selected to boot from the external drive but it appears to briefly access the external disk before returning me back to the Vista bootloader.  Any idea what I might have done wrong - it seems like I haven't made the external drive bootable?

---

### Post by ian49 on 2014-06-17
Sorry I should have made it clear that the laptop is running Vista.

---

### Post by yancek on 2014-06-17
If you set sdb with Ubuntu to first boot priority in the BIOS and still boot vista on sda, then you probably did not install the Grub bootloader to the master boot record of sdb, the Ubuntu drive.  You don't inidicate which option you selected during the install.  If you had selected the 'Something Else' option, you would have seen that you had a choice of where to install the bootloader and could have selected /dev/sdb.  I've not used the 'Alongside' or 'Erase' options so I don't know what you see there.

If you want to keep the vista and Ubuntu drives separate, then install the Grub bootloader from the Ubuntu install medium to the master boot record of sdb.  There are several methods explained at the site below:

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by ian49 on 2014-06-17
Thanks for responding. I tried:  sudo grub-install /dev/sdb and got the following error message:

grub-install failed to get canonical path of '/cow'

---

### Post by Bucky Ball on 2014-06-17
Try Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

Read the top of the page for a background of what it does.

---

