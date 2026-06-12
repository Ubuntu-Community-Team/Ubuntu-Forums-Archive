---
title: "How to properly uninstall Ubuntu and reinstall a diffrent version."
date: 2019-02-03
forum: New to Ubuntu
---

### Post by vysero on 2019-02-03
My computer currently has a duel boot setup: Ubuntu 12.04 and 16.04. I want to remove 12.04 but the last time I tried removing Ubuntu it bricked my Grub GUI. The way I deleted it was by opening the 'Disks' menu and deleting the filesystem partitions. Is there a way of removing Ubuntu that wont cause me to have the need to run a program like Grub-repair again? I am going to reinstall 10.04 after I uninstall 12.04, yes I know it is EOL but I have some work to do on it.

---

### Post by TheFu on 2019-02-04
In general, 
* boot from a different OS. If the OS running is installed in the machine it is a little easier.
* delete the partition with the OS you don't want (or just remove all the files there)
* run **sudo update-grub** - this rebuilds the grub setup.  

If you want to pull the old disk out of the system, run sudo grub-install with the path to the disk that you wish to boot from before update-grub and rebooting.

If you boot from external media like an install flash or dvd, then grub-install and update-grub are a little more complicated, I believe. I'd have to look up whether setting up a chroot is needed or not.  I think it is.

---

### Post by yancek on 2019-02-04
Your post indicates you currently have two operating systems (ubuntu 12.04 and 16.04) on the machine.  If you installed 16.04 after 12.04 and accepted the defaults, the Grub code from 16.04 should be in the MBR on a Legacy install and you should be able to format the 12.04 partition and re-use it.  If you are not sure, boot 16.04 and install Grub to the MBR if it is a Legacy install.

The mostly likely scenario for your earlier problem was deleting the files on the partition which held the Grub boot files.

---

### Post by ajgreeny on 2019-02-04
Is this a UEFI or MBR/BIOS system as that can make a difference to how to best deal with this and make sure that grub from the required OS is still in change.

You are already aware that 10.04 is EOL so I presume you are also aware that it will be very risky to go online with that version.
What sort of work is it that you can only do using 10.04?  
It seems to me that there is little point in spending time and effort working on a system that no-one else will be using and for which there will be difficulties installing anything new.

---

### Post by Impavidus on 2019-02-04
> **yancek said:**
> Your post indicates you currently have two operating systems (ubuntu 12.04 and 16.04) on the machine.  If you installed 16.04 after 12.04 and accepted the defaults, the Grub code from 16.04 should be in the MBR on a Legacy install and you should be able to format the 12.04 partition and re-use it.  If you are not sure, boot 16.04 and install Grub to the MBR if it is a Legacy install.

The mostly likely scenario for your earlier problem was deleting the files on the partition which held the Grub boot files.

Normally the last system installed is the one in control of grub. But when an upgrade to grub is installed, the last system to install this upgrade takes over control, which usually is the least used system. In your case this shouldn't be much of a problem. 12.04 hasn't got any upgrades to grub in a long time, for the simple reason that it reached end-of-live two years ago. But you should check anyway, even if just to make sure kernel upgrades on 16.04 are detected by grub.

---

### Post by vysero on 2019-02-04
More information: 16.04 is actually the legacy OS on this computer. On my 1TB hard drive there are 5 partitions:

1) Microsoft reserved contents unknown: 135 MB
2) DATA 496 GB (just a place to store things)
3) BIOS Boot contents unknown 1.0 MB
4) Linux Filesystem (12.04) 487 GB
5) Linux Swap: Swap (version 1) -- Not Active

My copy of 16.04 exists on my static drive which has three partitions:

1) EFI System, FAT (32-bit version) -- Mounted at /boot/efi, 537 MB
2) Basic Data, Ext4 (version 1.0) -- Mounted at Filesystem Root (not sure why this isn't called a Linux system), 238 GB
3) Linux Swap, Sweap (version 1) -- Active, 17 GB

---

### Post by ajgreeny on 2019-02-04
> **vysero said:**
> More information: 16.04 is actually the legacy OS on this computer. On my 1TB hard drive there are 5 partitions:

1) Microsoft reserved contents unknown: 135 MB
2) DATA 496 GB (just a place to store things)
3) BIOS Boot contents unknown 1.0 MB
4) Linux Filesystem (12.04) 487 GB
5) Linux Swap: Swap (version 1) -- Not Active

My copy of 16.04 exists on my static drive which has three partitions:

1) EFI System, FAT (32-bit version) -- Mounted at /boot/efi, 537 MB
2) Basic Data, Ext4 (version 1.0) -- Mounted at Filesystem Root (not sure why this isn't called a Linux system), 238 GB
3) Linux Swap, Sweap (version 1) -- Active, 17 GB
I'm sory but I'm a bit confused; what you mean by "legacy OS" and your comment about "My copy of 16.04 exists on my static drive"
Please give us more detailed info, probably best using terminal command "sudo fdisk -l"

Is one of the disks external, both internal, and is one a HDD and the other an SDD?

---

### Post by TheFu on 2019-02-04
I think we need the output from a boot-info/**boot-repair** to help much more.  I'd assumed the hardware was older, non-UEFI and that legacy boot was being used. I see a boot-repair link in AJ's sig.

Facts (commands run) are better than interpretations/descriptions.  We are used to seeing the nitty-gritty details from shell commands here. Please post using "code tags" (Adv Reply #), so the columns line up.

BTW, 10.04 support for UEFI wasn't perfect.  Might just want to put that OS into a virtual machine and skip all the dangers of it not playing nice in a dual-triple-quad boot setup.

---

### Post by vysero on 2019-02-04
```
rob@linux038:~$ sudo fdisk -l
[sudo] password for murchrob: 
Disk /dev/loop0: 125 MiB, 131010560 bytes, 255880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 91 MiB, 95408128 bytes, 186344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 91.1 MiB, 95494144 bytes, 186512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 125 MiB, 131010560 bytes, 255880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 237.9 MiB, 249466880 bytes, 487240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 227.3 MiB, 238325760 bytes, 465480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 89.5 MiB, 93835264 bytes, 183272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 227.2 MiB, 238276608 bytes, 465384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 1566777A-1111-4D40-B952-346859E17E74

Device             Start       End   Sectors   Size Type
/dev/nvme0n1p1      2048   1050623   1048576   512M EFI System
/dev/nvme0n1p2   1050624 466722815 465672192 222.1G Microsoft basic data
/dev/nvme0n1p3 466722816 500117503  33394688  15.9G Linux swap




Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 563598A5-83C9-40CD-88F7-8974A7BD3ED4

Device          Start        End   Sectors   Size Type
/dev/sda1        2048     264191    262144   128M Microsoft reserved
/dev/sda2      264192  968232047 967967856 461.6G Microsoft basic data
/dev/sda3   968232960  968235007      2048     1M BIOS boot
/dev/sda4   968235008 1920131071 951896064 453.9G Linux filesystem
/dev/sda5  1920131072 1953523711  33392640  15.9G Linux swap

```

[Here]("http://paste.ubuntu.com/p/KcCH4MtCDT/") is the boot-repair output. [URL="http://paste.ubuntu.com/p/KcCH4MtCDT/"]
[/URL]

---

### Post by TheFu on 2019-02-04
FYI.

Googling .... looks like kernel v3.3 or later is needed for any NVMe support: [https://itpeernetwork.intel.com/upgrade-to-a-nvme-capable-linux-kernel/](https://itpeernetwork.intel.com/upgrade-to-a-nvme-capable-linux-kernel/)   & [https://www.smartmontools.org/wiki/NVMe_Support](https://www.smartmontools.org/wiki/NVMe_Support) 

[https://wiki.ubuntu.com/Kernel/Dev/KernelStableSupportMatrix](https://wiki.ubuntu.com/Kernel/Dev/KernelStableSupportMatrix) shows that 10.04 was based on 2.6.x kernels and added v3.0.x later.

My UEFI-fu is weak. Sorry.

---

### Post by oldrocker99 on 2019-02-04
It is a very good idea to install the new version rather than update in place, and I don't recommend it.

There is no reason to use 16.04 when 18.04 is improved over 16.04. 10.04 is no longer being supported, with no updates at all, and **could**
be hazardous if you go online. I change my system every 2 years, when the new LTS comes out. 12.04 will end support pretty soon, as well.

---

### Post by vysero on 2019-02-04
@[**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=27747") Just an update. A co-worked informed me that one of our build machines is in fact a 12.04 machine. So I am no longer going to be deleting 12.04 to replace it with 10.04. Instead, I will be working on the currently installed 12.04 distribution. I am sorry if I wasted anyone's time with this post. I do have a different semi-related question though. Not sure if I should create a new thread for it...:confused:. On Ubuntu, it seems like the user-space and the kernel space are separate entities. Will it be possible for me to access the user-space of the 16.04 OS inside of the 12.04 OS so that I don't have to go through the process of registering a new computer on our server and downloading all the repositories and such?

---

### Post by ajgreeny on 2019-02-06
By "user-space" I assume you mean all the filers and folders in the /home folder or partition, depending on your OS setup?

Certainly you can easily access all data files and folders of 16.04 from the 12.04 OS, though there may be changes needed to permissions to allow access as user.
We will need a great deal more detail to know exactly what you want to do; once we have that info we may be able to help further.

Please start a new thread with an appropriate title in order that this specific situation can be best discussed in the forum, hopefully giving you the answers you need without the extra confusion of this thread.

You should also think very carefully about continued use of 12.04 as that is, like 10.04, also out of support and thus risky to continue using, on a network in particular.

---

