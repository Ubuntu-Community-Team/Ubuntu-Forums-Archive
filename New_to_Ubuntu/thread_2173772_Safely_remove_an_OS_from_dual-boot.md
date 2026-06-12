---
title: "Safely remove an OS from dual-boot"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by twsLeGR on 2013-09-11
I am dual-booting Ubuntu 13.04 and Elementary OS. Could anyone tell me how i might safely remove Elementary OS and get Ubuntu to reclaim the hard drive. Thanks in advance.

---

### Post by carl4926 on 2013-09-11
Post a screen of your HD as seen in Gparted
Tell us which OS uses which space

---

### Post by ajgreeny on 2013-09-11
You will need to make sure that ubuntu is the OS which provides grub before you remove EOS, or you will have to restore grub afterwards, so boot to ubuntu and run ```
sudo grub-install /dev/sda
``` assuming you have only one hard disk.  Then we can look at the gparted screenshot that carl4926 has asked for and tell you which partition(s) to delete.

---

### Post by twsLeGR on 2013-09-11
Right! Ubuntu 13.04 is on (/dev/sda1) and Elementary OS is on (/dev/sda6). You can see the dual-boot set up at [http://www.freewebs.com/diarco/screenshot.png](http://www.freewebs.com/diarco/screenshot.png)
Big thanks as always for any and all help.

---

### Post by carl4926 on 2013-09-11
> **twsLeGR said:**
> Right! Ubuntu 13.04 is on (/dev/sda1) and Elementary OS is on (/dev/sda6). You can see the dual-boot set up at [http://www.freewebs.com/diarco/screenshot.png](http://www.freewebs.com/diarco/screenshot.png)
Big thanks as always for any and all help.
As already said, make sure Ubuntu is controlling booting with grub
If you do it from the installed Ubuntu you'd have to swap off
I recommend Ubuntu Live CD and Gparted
You can delete all but sda1, then expand sda1 to use all the free space except the last 8GB which you should create a swap as sda2 primary

You may have to edit fstab

---

### Post by twsLeGR on 2013-09-11
I want to keep my Ubuntu partition on /dev/sda1, plus the swap. So couldn't just delete all the other partitions and then enlarge the Ubuntu partition to reclaim all unallocated space?

---

### Post by ajgreeny on 2013-09-11
Thanks for the pic.

If you have already run the **grub-install **command with no errors, and backed up your personal files from your home, you are safe to continue and remove the partition  sda6 and then once you've done that shrink sda2, the extended partition, to just contain your swap partition.

That will leave you with the 225.11GB of unallocated space which you can either leave as a separate partition, or you could enlarge your current sda1 by grabbing its right hand edge and resizing it to the right, or you could even turn it into a separate ext4 /home partition by copying everything from your current home into that partition, including all hidden files and folders, then shrinking sda1 to a more appropriate size (20GB) and enlarging the new /home partition to fill the space, and finally editing /etc/fstab to make that partition mount at boot as the new /home.  This would make any re-installs or upgrades of distro easier, and if you want to find out more or do this, come back again and we can talk you through how to do it.

---

