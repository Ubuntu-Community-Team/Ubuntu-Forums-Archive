---
title: "HELP: efidisk read error"
date: 2014-08-18
forum: New to Ubuntu
---

### Post by mengmeng2 on 2014-08-18
Hi

My ubuntu got a mess now. now before the GRUB the screen shows six lines of "error: efidisk read error", but I can enter ubuntu (12.04), it seems to work fine, but I cannot get rid of this error message anyway. 
I only have ubuntu 12.04 on my machine, no others, no dual system. I googled but found most of the solutions are for dual system, especially windows, but my machine never has windows installed.
I used to have ubuntu 14.04 but for some reason I decided to use 12.04 instead, the error occured since the re-installation. 
Does anyone can help me?

great thanks!

Mengmeng

---

### Post by oldfred on 2014-08-18
Are you booting in UEFI or BIOS mode?
It almost sounds like it is progressing thru all the UEFI boot options, and then booting in BIOS mode.

Some UEFI/BIOS let you turn on a setting for both UEFI & BIOS and it then boots whatever it finds first. Uusally better then  to say UEFI only or BIOS only and make sure the first choice in the system boot menu is ubuntu or hard drive with Ubuntu installed.

---

### Post by mengmeng2 on 2014-08-19
> **oldfred said:**
> Are you booting in UEFI or BIOS mode?
It almost sounds like it is progressing thru all the UEFI boot options, and then booting in BIOS mode.

Some UEFI/BIOS let you turn on a setting for both UEFI & BIOS and it then boots whatever it finds first. Uusally better then  to say UEFI only or BIOS only and make sure the first choice in the system boot menu is ubuntu or hard drive with Ubuntu installed.

Hi, thanks for your quick response. 
I think I boot in BIOS mode (how to know this?), and the boot menu is ubuntu first for sure.
Could you give me some detailed explaination?
thanks

---

### Post by oldfred on 2014-08-19
You have to look into your UEFI/BIOS and see what settings it has. I do not know what those may be.

You can see all the details of how you have installed by posting the link from the Boot info report. Do not run the auto fix, while those with issues that may usually fix it, in a few cases it may make it more difficult to fix. Just create the report.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some others have posted screen shots of their UEFI.
With UEFI CSM is the name for BIOS, but some also call it legacy.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

