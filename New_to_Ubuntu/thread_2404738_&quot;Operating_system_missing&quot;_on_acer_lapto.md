---
title: "&quot;Operating system missing&quot; on acer laptop. How can I restore hard drive?"
date: 2018-10-28
forum: New to Ubuntu
---

### Post by fulldeck44 on 2018-10-28
Hello I'm new to both Linux and this forum. I had Ubuntu 18.04 on my hard drive. I had another hard drive with windows that I was going to use a recovery disk with, and forgot to switch drives. Now my hard drive with Linux doesn't load. I get a message that says "operating system missing". How can I restore my drive?

---

### Post by bijayalaxmi1808 on 2018-10-28
I think if the Ubuntu is still installed on the hard drive then by fixing the master boot record using an Ubuntu Live Disk will help. (Someone please correct me if I am wrong)
You boot the system from an Ubuntu Live Disk and install the Grub2 in the MBR of the hard drive where the Ubuntu is already installed.

I am not sure if the Grub will be able to point to the boot image while installing or not.
If it does not, then probably you can find out where the Ubuntu boot image is residing on the hard drive and you can point it manually in the Grub otherwise.

Other alternative to recover your drive is:
- Use an Ubuntu Live disk and mount the hard drive which contains the earlier Ubuntu installation
- Copy all the important files from the earlier Ubuntu installed hard drive to another external hard drive or some USB drive etc.
- Then go for a clean Ubuntu installation

I hope this will help you. :)

---

### Post by Impavidus on 2018-10-28
First we have to find out what exactly went wrong. Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair), create a boot info summary and show us the link to the report. That should tell us if/where the OS and the boot loader are installed.

---

### Post by ajgreeny on 2018-10-28
You may have fallen foul of the Acer requirement to set Trust before you can use Linux on their new machines.

See the thread at [https://ubuntuforums.org/showthread.php?t=2384706](https://ubuntuforums.org/showthread.php?t=2384706) which hopefully will help you further.

---

### Post by fulldeck44 on 2018-10-29
> **Impavidus said:**
> First we have to find out what exactly went wrong. Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair), create a boot info summary and show us the link to the report. That should tell us if/where the OS and the boot loader are installed.[http://paste.ubuntu.com/p/pqjYpDpJS2/](http://paste.ubuntu.com/p/pqjYpDpJS2/)

---

### Post by oldfred on 2018-10-29
It looks like you have a newer UEFI system, but have installed Ubuntu in BIOS boot mode to MBR partitioned drive.
But still have an old Windows boot loader in MBR of drive. You need grub installed to MBR to be able to boot.
Just run the fix suggested by Boot-Repair to install grub to MBR of sda.
Make sure UEFI Secure Boot is off, CSM/BIOS/Legacy boot is on for BIOS boot to work.

Or since newer UEFI system, you may want to use UEFI but need to also have gpt partitioning. That would totally erase drive and separately require "trust" setting after install in UEFI.

---

### Post by fulldeck44 on 2018-10-29
> **oldfred said:**
> You need grub installed to MBR to be able to boot.Just run the fix suggested by Boot-Repair to install grub to MBR of sda.Will this delete files that I had saved on Ubuntu?

---

### Post by oldfred on 2018-10-29
You always should have good backups.
But installing grub to MBR, will just erase the old Windows boot loader in the MBR.

---

