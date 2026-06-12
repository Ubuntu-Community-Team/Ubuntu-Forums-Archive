---
title: "Unable to access Ubuntu"
date: 2017-05-20
forum: New to Ubuntu
---

### Post by dayashridhar on 2017-05-20
Have both windows and Ubuntu on my desktop, using only Ubuntu and not accessing Windows.  All of a sudden am unable to access Ubuntu, it takes me to the grub terminal.  If I command boot it asks me to load the kernel. When I follow examples online involving loading the kernel, it tells me it has an error reading certain sectors of hd0. What do I do? I know my ubuntu's partition is on sda3. Anyone have an idea?

---

### Post by ajgreeny on 2017-05-20
More information is needed for us to be able to help you.

Versions of both Ubuntu and Windows please?
BIOS or UEFI machine?
Secure boot enabled or disabled?

If using Win 10 an update of that can cause huge problems for dual boot users as it can turn on secure boot even if you had it off, and can also re-enable faststart or whatever it's called in Windows.

---

### Post by Impavidus on 2017-05-20
Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). Don't run the recommended repair, but create a BootInfo summary and post the link here.

---

### Post by dayashridhar on 2017-05-20
16.04.1 Ubuntu and Windows 7 proff

How do I tell if it's a BIOS of UEFI machine? When I start up, and hit F12 for config it's a BIOS config, but in that config it tells me that Windows is UEFI. 
Secure boot is disabled

---

### Post by dayashridhar on 2017-05-20
Did that 

[http://paste.ubuntu.com/24612290](http://paste.ubuntu.com/24612290)

---

### Post by RobGoss on 2017-05-21
> **dayashridhar said:**
> 16.04.1 Ubuntu and Windows 7 proff

How do I tell if it's a BIOS of UEFI machine? When I start up, and hit F12 for config it's a BIOS config, but in that config it tells me that Windows is UEFI. 
Secure boot is disabled

You can see if your machine is **UEFI **by accessing your setup configurations most machines you can us **F-2 **to access it.  If you look at your **Boot Info Summary, ** on ** sda1 **It indicates your system is in fact a **UEFI**  system.

Did you make any changes before this issues started? and was your system booting normally before this

---

### Post by dayashridhar on 2017-05-21
> **RobGoss said:**
> You can see if your machine is **UEFI **by accessing your setup configurations most machines you can us **F-2 **to access it.  If you look at your **Boot Info Summary, ** on ** sda1 **It indicates your system is in fact a **UEFI**  system.

Did you make any changes before this issues started? and was your system booting normally before this


The power box was replaced and after that this issue started.  The system was booting normally, in Ubuntu, before that.

---

### Post by RobGoss on 2017-05-21
Well if Windows is booting OK I don't think it's the power supply box, trying to figure what may have changed before that

---

### Post by dayashridhar on 2017-05-21
> **Impavidus said:**
> Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). Don't run the recommended repair, but create a BootInfo summary and post the link here.

[COLOR=#000000]Did that [/COLOR]

[http://paste.ubuntu.com/24612290](http://paste.ubuntu.com/24612290)

---

### Post by oldfred on 2017-05-21
You show grub installed for BIOS Boot in protective MBR and in ESP - efi system partition for UEFI boot.
You have gpt partitioning which with Windows can only be UEFI. Ubuntu could work with either BIOS or UEFI, but you always have to boot from UEFI menu as UEFI & BIOS are not compatible or grub only can boot systems in same boot mode.

But you show no Linux partitions? And drive is fully partitioned. Or was sda4 which is shown as NTFS really an ext4 partition. Not sure how you could have changed that without totally reformatting it and erasing Ubuntu.

Does Windows boot ok?
Most Windows 7 installs are BIOS on MBR partitioned drives, but you do have Windows UEFI boot files in ESP.

---

### Post by oldfred on 2017-05-21
(Jailed post on saying you should not have FAT32 and must have NTFS). It was just confusing the issue.

FAT32 is required for UEFI boot, both Windows & Linux.

And OP has NTFS as sda3.

---

