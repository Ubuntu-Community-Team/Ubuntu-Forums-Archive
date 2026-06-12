---
title: "'Windows 7' boot option disappeared from GRUB"
date: 2016-01-19
forum: New to Ubuntu
---

### Post by timex1251 on 2016-01-19
Hi all,

I'm really new to Linux and just installed Ubuntu to dual boot on my laptop a week ago. I tried to restore from a previous save point on Windows and also played around with Grub Customizer. I don't know exactly what I did but Windows 7 doesn't show up as a boot option on GRUB anymore. The Windows partition is still there and I can access the files from Ubuntu but can't boot Windows anymore. Any help on booting from Windows again?

---

### Post by Mark Phelps on 2016-01-19
If you're asking about restoring the capability to boot into Windows from GRUB, then you can recreate the default GRUB configuration files by booting into Ubuntu, opening a terminal window and entering "sudo update-grub" (without the quotes).

---

### Post by timex1251 on 2016-01-19
Thanks for the reply Mark. 

I gave it a shot and rebooted my computer but I'm still only getting Ubuntu options. Any other suggestions?

---

### Post by oldfred on 2016-01-19
Best then to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Geoffrey_Arndt on 2016-01-19
Maybe you could provide more info on exactly what you did and why (especially the "why") . . . . since as a new Ubuntu user, why would you be doing Windows restore points (which has NO effect on Ubuntu) or modifying Grub at all (assuming your original install worked and you had the normal grub bootloader screen at startup).    

IF you were having problems with the original install,  . . . . at that point, it would have been better to ask about fixes or if any grub updates needed.

Anyway, the best way to start is by providing more info (what version of Ubuntu, etc.), including the full specs for your PC.   Also, if you can attache a screenshot of your disk partitioning, it would be very helpful.  

You may have to download and create a Grub Rescue image on usb-flash stick or optical media, but maybe not needed depending on your info (EDIT . . . looks like Old Fred has already taken care of this option . . )

---

### Post by timex1251 on 2016-01-19
[http://paste.ubuntu.com/14577417/](http://paste.ubuntu.com/14577417/)

---

### Post by oldfred on 2016-01-19
The report shows Windows, now twice.

Boot-Repair copies Windows boot files from its Boot partition into the main partition. Too many users do not know Boot partition is essential, since not normally shown in Windows. And without boot files difficult to repair. But then grub2's os-prober finds boot files in two partitions and adds both to grub menu. You should be able to boot from either one.

If you cannot boot the Windows install from grub, then you have Windows issues. Often chkdsk from your Windows repairCD or flash drive is then all that is required.

---

