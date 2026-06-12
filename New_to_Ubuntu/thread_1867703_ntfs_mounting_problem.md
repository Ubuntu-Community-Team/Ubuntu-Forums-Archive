---
title: "ntfs mounting problem"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by Arendyl on 2011-10-23
Im trying to install windows 7, I don't know how to make a NTFS partition. I have a large space set aside for windows 7. Any help is appreciated

---

### Post by Mark Phelps on 2011-10-23
Don't format the partition; instead, when you boot from the Win7 DVD, select the unformatted space.  It will then format it during the installation.

---

### Post by Arendyl on 2011-10-23
> **Mark Phelps said:**
> Don't format the partition; instead, when you boot from the Win7 DVD, select the unformatted space.  It will then format it during the installation.

It won't let me begin the installation. It say the partition must be NTFS.

---

### Post by coffeecat on 2011-10-23
> **Arendyl said:**
> It say the partition must be NTFS.

It must also be a primary partition. What other partitions do you have on the drive and in what layout? You don't say whether you have another OS already installed. Assuming it's Ubuntu, post the output of this terminal command:

```
sudo fdisk -lu
```

Also, if you are trying to install Windows after Ubuntu or any other Linux distro, you need to be aware of two big gotchas. You will need to re-install grub after installing Windows to get a dual-boot menu, and if you have logical partitions and fewer than the full complement of primary/extended partitions, the Windows installer sometimes corrupts the partition table.

---

### Post by Arendyl on 2011-10-23
> **coffeecat said:**
> It must also be a primary partition. What other partitions do you have on the drive and in what layout? You don't say whether you have another OS already installed. Assuming it's Ubuntu, post the output of this terminal command:

```
sudo fdisk -lu
```

Also, if you are trying to install Windows after Ubuntu or any other Linux distro, you need to be aware of two big gotchas. You will need to re-install grub after installing Windows to get a dual-boot menu, and if you have logical partitions and fewer than the full complement of primary/extended partitions, the Windows installer sometimes corrupts the partition table.

Disk /dev/sda: 16.1 GB, 16139681792 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d4db4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    29474815    14736384   83  Linux
/dev/sda2        29474816    31522815     1024000   82  Linux swap / Solaris

Disk /dev/sdb: 989 MB, 989855744 bytes
32 heads, 31 sectors/track, 1948 cylinders, total 1933312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             135     1933311      966588+   6  FAT16

---

### Post by coffeecat on 2011-10-23
Your sda drive is only 16GB which, even if you reserved the whole lot for Windows, is not nearly enough for installing Windows 7 to. Apart from that, there is no free space on it. Your Linux partitions are taking up the whole drive.

What do you mean by a large space set aside for Windows?

---

### Post by Arendyl on 2011-10-23
> **coffeecat said:**
> Your sda drive is only 16GB which, even if you reserved the whole lot for Windows, is not nearly enough for installing Windows 7 to. Apart from that, there is no free space on it. Your Linux partitions are taking up the whole drive.

What do you mean by a large space set aside for Windows?

I'm sorry. I wasn't thinking at all. I was reading the forums on my netbook, and the problem is on my desktop. Sorry. Here are the results for my desktop

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00081761

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   163842047    81920000   83  Linux
/dev/sda2       484339710   488396799     2028545    5  Extended
/dev/sda3       163842048   484337663   160247808    b  W95 FAT32
/dev/sda5       484339712   488396799     2028544   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc334

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15625215     7812592    b  W95 FAT32

---

### Post by coffeecat on 2011-10-23
> **Arendyl said:**
> I'm sorry. I wasn't thinking at all. I was reading the forums on my netbook, and the problem is on my desktop. Sorry. Here are the results for my desktop

:) I'm relieved!

I believe the problem is that the space you've reserved is formatted FAT32, which Windows 7 won't install to. Your partitions are slightly out of order, and this is how they are as they appear on the disk:

sda1 - Linux - 84GB
sda3 - FAT32 - 164GB
sda2 extended partition containing your logical sda5 swap partition - 2GB

I suggest you reformat sda3 to NTFS using Gparted and also use Gparted to set the boot flag on sda3 - Windows needs it; Linux doesn't. By the way, I don't foresee a problem using Gparted to create a NTFS partition for Windows. I've successfully installed (and used) Windows XP, Vista and 7 to NTFS partitions I've created with Gparted. Hopefully the Windows installer will then be happy to install Windows to your 164GB partition.

Bear in mind what I said about the two gotchas. The boot loader is easily dealt with. The Windows installer may try to turn your swap partition into a primary one residing inside the extended partition - a partition table illegality - or it may simply decide to wipe out the swap partition altogether without telling you! Depends what mood it's in. :wink: As it's only the swap partition, this is also fairly simply fixed. If you do manage to install Windows, post again if you need help with the gotchas.

---

### Post by Arendyl on 2011-10-23
When i go to reformat the windows partition, ntfs is not an option. What am I doing wrong?

---

### Post by Arendyl on 2011-10-23
scratch that. I figured it out. thanks

---

### Post by Arendyl on 2011-10-23
Ok. could you explain the "gotchas"? How do I reinstall grub?

---

### Post by coffeecat on 2011-10-23
> **Arendyl said:**
> Ok. could you explain the "gotchas"? How do I reinstall grub?

Boot up with the Ubuntu live CD - same version as you have installed to the hard drive - and choose "try Ubuntu" to get to the live desktop. First, from a terminal:

```
sudo fdisk -lu
```

To make sure you still have a Linux partition at sda1. If you have any doubt, stop there and post the fdisk output, and save it anyway. If you are happy to go ahead:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That will re-install grub to the mbr. But there are a couple of things to do first. As above - save the fdisk output so that you can post it. Then, reboot. Your grub menu will not yet show a Windows entry, so when you are booted into your permanent Ubuntu installation, open a terminal, and:

```
sudo update-grub
```

The second gotcha: to be sure that the Windows installer hasn't interfered with the partitition table, post the output of fdisk that you got from the live session, or simply run "sudo fdisk -lu" from your permanent Ubuntu and post the output.

---

### Post by Arendyl on 2011-10-23
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00081761

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   163842047    81920000   83  Linux
/dev/sda2   *   163842048   484337663   160247808    7  HPFS/NTFS/exFAT
/dev/sda3       484339710   488396799     2028545    5  Extended
/dev/sda5       484339712   488396799     2028544   82  Linux swap / Solaris

Disk /dev/sdb: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc334

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15625215     7812592    b  W95 FAT32

---

### Post by coffeecat on 2011-10-23
That looks good to me. Is everything working as it should?

---

### Post by Arendyl on 2011-10-23
not quite. It wont run the last line, sudo update-grub, and when I boot, ubuntu is coming up. However, I did have one problem with the instructions. My computer is running 11.04 and the live CD is 11.10.

---

### Post by coffeecat on 2011-10-23
> **Arendyl said:**
> not quite. It wont run the last line, sudo update-grub, and when I boot, ubuntu is coming up. However, I did have one problem with the instructions. My computer is running 11.04 and the live CD is 11.10.

If you're able to boot into Ubuntu, using the 11.10 CD *may* not have been a problem. The reason I suggest using the same version of Ubuntu in the live CD is that although every Ubuntu release since Karmic has used grub2, they have different point releases. You are using the live CD to write grub code to the mbr, whereas the rest of the grub code is in the root partition. It's best to keep to the same point version to be sure there are no incompatibilities.

What happens when you run "sudo update-grub"? Post the output.

---

### Post by Arendyl on 2011-10-23
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$

---

### Post by coffeecat on 2011-10-23
You're running update-grub from the live CD. You need to run it from your permanent installation - see my earlier post. Now that you've installed grub to the mbr from the live session, reboot into Ubuntu on your hard drive and run "sudo update-grub" there. That should put a Windows entry into your grub menu.

---

### Post by Arendyl on 2011-10-23
Works great. A thousand thanks coffeecat. This is the second time you've helped me out. I swear I will become an ubuntu expert and help as many people as I can.

---

### Post by coffeecat on 2011-10-24
Good luck!

---

