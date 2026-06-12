---
title: "New Z87 Will Not Boot Non-UEFI Disk"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by sml on 2013-06-29
I had a Gigabyte Z87 and was using two different operating systems installed on:
a) a SSD with UEFI linux Ubuntu
b) another SSD with non-UEFI linux Ubuntu

I then bought a new Asus Z87 motherboard and I can boot the UEFI operating system but cannot boot the non-UEFI operating system.

I can see the non-UEFI disk in the UEFI ... P1: Samsung SSD etc and it is set as the priority boot disk and also tried the shortcut boot options. It doesn't seem to recognise that it is a bootable disk. Just goes back to UEFI.

If I boot the UEFI ubuntu, I can access the other disk and see all the files.

Settings:
CSM &#8211; enabled
Boot Device Control = UEFI and Legacy OPROM
Boot from Network Device = Ignore
Boot from Storage Device = Both, Legacy OPROM first (also tried 'Both, UEFI first')
Secure Boot = Other OS

Are there any other settings/installation issues that might be causing the non-UEFI operating system not to boot?

---

### Post by oldfred on 2013-06-30
There are so many settings on new motherboards now that it can be difficult to know what is correct.

But if you have a BIOS install, you need CSM/BIOS/Legacy as the boot mode. Some just turn that on and then UEFI is off. Others have to separately turn UEFI off. 

You can use Boot-Repair to convert a BIOS install to UEFI, but also have to convert to gpt partitioning first.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

      
 
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by sml on 2013-06-30
> **oldfred said:**
> There are so many settings on new motherboards now that it can be difficult to know what is correct.
But if you have a BIOS install, you need CSM/BIOS/Legacy as the boot mode. Some just turn that on and then UEFI is off. Others have to separately turn UEFI off. 


yes, tell me about it! there are so many settings, it is probably just a simple UEFI option that needs to be changed .. but I spent a few hours and didnt have much luck.

on my Z77 Asus, I think there was an option for the Boot Mode: BIOS/Legacy ... however the Z87 Asus, I couldn't seem to find that option .. maybe it was labelled something else like the OPROM thing setting.

thanks... ended-up using boot-repair with success! :)

---

