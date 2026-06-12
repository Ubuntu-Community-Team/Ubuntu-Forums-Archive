---
title: "A hoard of booting/BIOS issues..."
date: 2018-09-28
forum: New to Ubuntu
---

### Post by ponsukeen on 2018-09-28
Here's the thing. And I'll preface it by saying I'm very much in over my head - that's why I'm seeking help. A while ago, my Lenovo U410 laptop was having issues with the BIOS and wouldn't boot Windows 8.1. I didn't know how to fix it and wanted *something* to work on my PC, so I installed Ubuntu onto it's own partition. Later, Windows started booting normally again, so I continued using that and left Ubuntu in the background (the PC would automatically boot to Windows). I later installed Windows 10. 


Then, the same Windows booting issues that initially started everything started again and I was left with the Ubunutu I had installed to boot into. I wanted to get back on Windows, where all my files where, so I (quite irrationally) tried to remove Ubuntu completely by deleting a 32gb partition I'd apparently made for it. Yeah, I know that's not how it works now. Now, I couldn't get into Windows or Ubuntu, only the grub menu.


So, I tried installing Ubuntu again, by installing the newest version over the partition I'd deleted. Now Ubuntu works again. I'm still trying to access my Windows OS and all the files associated with it, which I'm *hoping* are on the disk somewhere. But I can't even boot into grub anymore, for some reason. I've tried to boot into Boot Repair Disc and a recovery drive I've made for Windows, neither seemed to work.


At this point, I just want to get access to Windows and my files. This laptop's had a lot of issues from day 1, I'm trying to get what I need and switch.

------------------------------------------------------------------------------------------------------------
dich vu [giup viec nha]("http://giupviecnha.vn/") uy tin [giúp vi&#7879;c nhà]("http://giupviecnha.vn/") giá r&#7867;

---

### Post by westie457 on 2018-09-28
Boot your system using the Ubuntu installation USB you made into 'Try' mode. Before attempting anything to fix this please report whether you had a four line text menu or a graphical interface when the USB started.

---

### Post by oldfred on 2018-09-28
Post the link that Boot-Repair gives when you run its Summary Report.
       Just run the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Your system is UEFI if Windows 8 from Lenovo. But you can boot in BIOS/CSM/Legacy mode.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
That is westie457 question as with UEFI boot you get a grub menu, with with BIOS you get a purple screen.

---

