---
title: "Remove Windows and only keep Ubuntu"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by ajdrew06 on 2012-03-05
Hi All,

I currently have Ubuntu 10.04 and Windows 2000 on two separate hard drives. I never use the Windows hard drive, and I would like to physically take it out & use it elsewhere. The problem is that my GRUB menu is on the hard drive with Windows on it. Can someone provide step by step instructions of putting the GRUB menu on my Linux hard drive? I've researched forums & have gotten links that just get me sidetracked & don't give complete solutions. I'd appreciate it! The links also have multiple solutions. I'd appreciate one simple clean solution, so I don't get confused.

Thank you for your patience!
-Drew

---

### Post by cortman on 2012-03-05
First of all BACK UP your data! We cannot emphasize this enough. It will save you a lot of heartache if you make sure all your essential data is stored offline.

Next you can open up GParted and figure out the name of the Ubuntu HD. This will be in the little selector box in the upper right corner. It's probably /dev/sda or /dev/sda1. You can tell which is your Ubuntu and which is your Windows HD by looking for ext4 and linux-swap among the partitions listed for the drive. The Windows drive will likely just have a big FAT32 or NTFS partition.
Next open a terminal and enter

```
sudo grub-install hard_drive_path
```If your Ubuntu HD is /dev/sda, you would run

```
sudo grub-install /dev/sda
```This will install GRUB to the MBR of your Ubuntu HD. You can test to see if it worked by removing the Windows drive and booting up. Make sure it will boot with the Windows drive physically separated before you delete anything off of it. Good luck!

---

### Post by _0R10N on 2012-03-06
After you follow cortman's advice, you can use that very tool for formatting  your Windows (NTFS most likely) partition to make it ext4.

---

### Post by ajdrew06 on 2012-03-06
that was so easy... why do other forums make it so convoluted THANK YOU!!!

---

### Post by cortman on 2012-03-06
> **ajdrew06 said:**
> that was so easy... why do other forums make it so convoluted THANK YOU!!!

You're very welcome, and thanks for marking the thread [SOLVED]. Cheers!

---

### Post by Ghost_Mazal on 2012-03-07
> **cortman said:**
> First of all BACK UP your data! We cannot emphasize this enough. It will save you a lot of heartache if you make sure all your essential data is stored offline.

Next you can open up GParted and figure out the name of the Ubuntu HD. This will be in the little selector box in the upper right corner. It's probably /dev/sda or /dev/sda1. You can tell which is your Ubuntu and which is your Windows HD by looking for ext4 and linux-swap among the partitions listed for the drive. The Windows drive will likely just have a big FAT32 or NTFS partition.
Next open a terminal and enter

```
sudo grub-install hard_drive_path
```If your Ubuntu HD is /dev/sda, you would run

```
sudo grub-install /dev/sda
```This will install GRUB to the MBR of your Ubuntu HD. You can test to see if it worked by removing the Windows drive and booting up. Make sure it will boot with the Windows drive physically separated before you delete anything off of it. Good luck!

This doesn't work on my pc.
I get the error: "Cannot stat aufs"

---

### Post by cortman on 2012-03-07
> **Ghost_Mazal said:**
> This doesn't work on my pc.
I get the error: "Cannot stat aufs"

Since the OP's problem has been solved and this thread marked so, please start another thread.

---

