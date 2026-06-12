---
title: "Ubuntu does not detect Windows 7"
date: 2014-07-21
forum: New to Ubuntu
---

### Post by Muhammad_Ahmad_Mujtaba on 2014-07-21
hello,

I have two operating systems one is ubuntu 14.04LTS which is on /dev/sda1 and other is Windows 7 Ultimate which is on /dev/sda2.
When my machine boots, it boots into directly Ubuntu 14.04LTS without detecting my Windows 7.
I have freshly installed Ubuntu 14.04LTS. I want a menu through i can decide the desired OS.
Windows 7 have files over /dev/sda2.
I ran os-prober through command prompt using ubuntu installed.
It displays nothing.
How can i recover windows 7 back?

---

### Post by kc1di on 2014-07-21
you can try running boot-repair found [here.]("https://help.ubuntu.com/community/Boot-Repair")

if it does not find it there is a webpage it will give you with a text file out put post it here so we can find the problem.

---

### Post by Vladlenin5000 on 2014-07-21
When you installed Ubuntu your already installed Windows 7 wasn't by any chance hibernated?

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-07-21
> **Vladlenin5000 said:**
> When you installed Ubuntu your already installed Windows 7 wasn't by any chance hibernated?

no it wasn't. I used it 5hours ago & I properly shut it down!

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-07-21
[I]GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.[/I]

upon running boot-repair it prompted.

---

### Post by oldfred on 2014-07-21
Is your system a new UEFI hardware based system?
And did you reinstall Windows 7 in BIOS mode or UEFI mode?

It looks like you booted Boot-Repair in BIOS mode and it is trying to install grub to the MBR of a gpt partitioned drive. But in BIOS mode grub has to have a bios_grub partition, in UEFI mode it has to have the efi partition. Boot-Repair does not auto create partitions so it gives the error. But you probably do not want that anyway.

Post link to BootInfo report. Do not run the auto fix.

---

### Post by Mark Phelps on 2014-07-21
> I have freshly installed Ubuntu 14.04LTS. I

Oh oh! DId you "reinstall" using the option to Replace the existing Ubuntu installation?  IF so, you might have erased the former Windows install -- as Replace causes the entire drive to be reformatted.

Best for us to see if Win7 is still there before you start into any Repair/Restore operations.

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-07-21
No I have no UEFI based machine. I am using simple EFI based machine.
I had Windows 7 from a month and Ubuntu 14.04LTS from 3 months. I just went for LXLE and on my another partition for tri-boot and all messed up! I deleted boot partition because after installing LXLE boot auto gets corrupted.
When i freshly installed Ubuntu 14.04LTS, I went for "something else" on partition menu, I feel it the most safe way! I always go for it.
Windows 7 is still there on /dev/sda2 and Ubuntu 14.04 LTS on /dev/sda1. I can see them using Ubuntu 14.04LTS live cd or parted magic live cd. I used grub-doctor given in parted magic CD but of no use! I have also Hiren's Boot CD. Will it help?
I can tell you right now! I have following four partitions:
/dev/sda1 : Ubuntu 14.04 LTS
/dev/sda2 : Windows 7 Ultimate [It's not deleted accidently, I can see files]
/dev/sda3 : Swap
/dev/sda4 : My Drive for my stuff.
/dev/sda5 : 670MB as raw/untyped partition with flags as bios_grub [as given by Gparted Software]

---

### Post by oldfred on 2014-07-21
We need to see details. 
Install into the Ubuntu installer or if your Ubuntu is working you can run it from that.

Do not run the auto fix, just post link from BootInfo report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

