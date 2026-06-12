---
title: "Boot Error 15"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Frunkis on 2008-04-28
I downloaded and burned Hardy, and ran it with the live disk. I have an ATI graphics card and I suspect that it was causing me some display issues in Live, where it only shows some of the screen in a very low resolution. I run XP on 1024X768, and when I went to set it to that, I couldn't apply the settings because I couldn't get to the button. So I restarted and got pulled away from the computer by my 4 month old, came back, and it was installing the full version, which I wasn't really ready for, but oh well. After that was finished and I rebooted I get this:

Booting 'Ubuntu 8.04, kernel 2.6.24-16-generic'
Filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.24-26-generic root=UUIS=36F46D29F46CED15 loop=/ubuntu/disks/root.disk ro quiet splash 

Error 15: File not found

Any Ideas???

---

### Post by zvacet on 2008-04-28
Maybe [this?]("http://easylinux.info/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD")

---

### Post by Frunkis on 2008-05-02
I uninstalled Ubuntu and reinstalled it trying to run just the live disk, and it did the full install on its own and did the same thing when I went to log it. There are severeal options for logging into Ubuntu, recovery mode I think, sorry, typing this from work. Any other ideas?

---

### Post by Xiong Chiamiov on 2008-05-02
Just to make sure that it isn't a grub problem, you can boot off the [Super GRUB disk]("http://www.supergrubdisk.org/") and list the partitions there and see if you can boot off of one.

---

