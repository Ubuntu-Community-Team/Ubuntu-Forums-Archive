---
title: "Problem with dual boot on second drive"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by mbeyer on 2012-07-19
I am having difficulties getting my new computer to dual boot.  After installing Ubuntu, my computer directly boots to Windows rather than providing me the option to alternatively boot to Ubuntu.

I have Windows 7 on my primary drive, which is relatively small (128 GB SSD drive).
I did the custom partitioning to keep the primary drive as my boot drive, but designated the second drive to mount "/".     

My computer has 64 GB of RAM, so also configured a third drive with a 64 GB swap partition.  Is this really necessary?  The documentation I read indicated 1 to 2 times the amount of memory to be allocated to swap.

Thank you in advance for your help.

Attached are the results that I have from a bootinfoscript that was listed on a previous thread:

---

### Post by sandyd on 2012-07-19
> **mbeyer said:**
> I am having difficulties getting my new computer to dual boot.  After installing Ubuntu, my computer directly boots to Windows rather than providing me the option to alternatively boot to Ubuntu.

I have Windows 7 on my primary drive, which is relatively small (128 GB SSD drive).
I did the custom partitioning to keep the primary drive as my boot drive, but designated the second drive to mount "/".     

My computer has 64 GB of RAM, so also configured a third drive with a 64 GB swap partition.  Is this really necessary?  The documentation I read indicated 1 to 2 times the amount of memory to be allocated to swap.

Thank you in advance for your help.

Attached are the results that I have from a bootinfoscript that was listed on a previous thread:
The memory allocated to swap is needed for hibernation.

The problem right now is that Grub (the bootloader) is installed on the secondary drive, not the primary drive.

When doing the install, you should set "Device for bootloader installation" to the primary drive.

---

### Post by SLRober1 on 2012-10-08
I'm having the same problem (when I use the BIOS to boot to my secondary hard drive, THEN I get the bootloader).  Is the easiest resolution simply to re-install Ubuntu and select the primary drive for the bootloader, or can it be moved manually?  I'm tech-savy (was a software trainer in my last job) but new to Linux/Ubuntu.

---

### Post by mips on 2012-10-08
> **SLRober1 said:**
> I'm having the same problem (when I use the BIOS to boot to my secondary hard drive, THEN I get the bootloader).  Is the easiest resolution simply to re-install Ubuntu and select the primary drive for the bootloader, or can it be moved manually?  I'm tech-savy (was a software trainer in my last job) but new to Linux/Ubuntu.

Boot into ubuntu and simply reinstall grub but this time to the primary drive the bios selects at boot up.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

