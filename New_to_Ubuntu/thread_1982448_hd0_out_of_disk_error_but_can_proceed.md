---
title: "hd0 out of disk error but can proceed"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by tkdncty2 on 2012-05-18
Hello!

I have installed Ubuntu 12.04 on a removable USB hard drive, while the internal hdd of the computer has win7 on it. I also installed the Grub on the removable, so if I want to use linux I select the usb drive from the bios boot menu.

When the Grub menu comes up and I press enter on the default entry to load ubuntu, the error message "hd0 out of disk press enter to continue" comes up. If I press enter the system proceeds loading without a problem.

 On the removable drive the primary partition is the swap partition and the logical is the ext4 ubuntu partition.

Do you know how to get rid of this error message?

---

### Post by BruntFCA on 2012-06-07
Hi,

I have the exact same problem.

Installed Ubuntu 12.04 to external USB. Using PLOP to boot the USB. Grub menu comes up, so I assume its correctly installed on the USB drive.

I select to boot Ubuntu. The error appears Error: hd0 out of disk
It asks me to press any key, I do, Ununtu loads with no problem.

The disk is 200GB Ext4, 8GB swap, and 700GB NTFS thats it.

What is Grub or the kernal doing for this error? In Gaprted the disks are labeled /dev/sda (my fixed windows drive).

The USB drive is /dev/sde, the partitions are sde1 (ext4 200MB), sde2 (8GB swap), and sde3 (700GB NTFS)

I checked fstab for swap and the uuid is correct and it shows swap being used in grub.
sde1 is labeled as boot. What is hd0, why does Grub/Kernal complain? Many thanks.

---

