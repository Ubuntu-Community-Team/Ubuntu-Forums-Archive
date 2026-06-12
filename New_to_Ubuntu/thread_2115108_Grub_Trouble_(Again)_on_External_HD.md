---
title: "Grub Trouble (Again) on External HD"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by sarahr on 2013-02-11
Howdy - 

I've got a lovely installation of Ubuntu 12.10 running on my Lenovo i5 mostly swimmingly and have been enjoying it without complaint for the last month or so. This machine initially came with a Windows install that I turned into a Linux Mint install, before deciding to go Ubuntu for my main Linux needs and computing pleasure. I purchased a new, larger-capacity HD for that purpose, swapped it into place and got Ubuntu up and running (with a few issues a long the way, as evinced by my previous postings in this most heplful and amicable forum - thank you for reading, as always). 
 
It has come to my attention that I need to boot into Windows for something, so I dusted off the formerly internal HD that now lives in an external and shares its disk with the Linux Mint install and the Windows 8 install. I recall these things working just fine in the past; I tested everything and was able to get into all OSes at will in various swaps and configurations. So I didn't expect to encounter any trouble at all after all this time. Of course, that was naive, at best.

I plugged in the external, hit the BIOS to select the disk and got an error immediately upon boot, the famed GRUB REPAIR> .
 
So, what's my best course of action here? Do I need to reinstall grub from my Ubuntu install, the primary (only) OS on this machine's internal HD? Do I need to do something with this external? Is the issue that I need to invoke grub from the Ubuntu disk and by selecing to boot off the external in the BIOS I bypassed that process?
 
Looking for ideas. I've not messed around under the hood in over a month and I feel like I'm fuzzy on what I had going on before. Thanks so much.

---

### Post by sarahr on 2013-02-12
Any thoughts on my best course of action? Thank you!

---

### Post by Cheesemill on 2013-02-12
If your goal is to boot Windows then you will have to put the Windows drive back in the machine it came from, you can't boot Windows from an external drive.

---

### Post by oldfred on 2013-02-12
Was Windows UEFI? 
As Cheesemill says Windows only boots from internal drives. It is licensed for one computer only, so does not support external drives. 

If Windows was pre-installed it was UEFI with secure boot. But if you did a separate install of Ubuntu you may have installed in BIOS or UEFI mode. How you boot install media is how it installs. And in UEFI/BIOS you set whether in UEFI or BIOS and from UEFI you still may get the option to boot in UEFI or BIOS mode. Starts to get complex.

Best to see details. From either a working install or the liveCD/DVD/Flash run the BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

