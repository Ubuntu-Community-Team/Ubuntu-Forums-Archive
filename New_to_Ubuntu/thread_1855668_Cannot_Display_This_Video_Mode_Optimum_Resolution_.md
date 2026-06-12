---
title: "Cannot Display This Video Mode Optimum Resolution 1440 X 900"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by QuentinK on 2011-10-06
[SIZE=1][COLOR=Silver][/COLOR][/SIZE][SIZE=1][SIZE=2][COLOR=Black]I recently put Linux on one a 10g partition after I messed up the BOOTMGR for my windows 7. I was hoping that GRUB would be able to detect Windows 7 and act as a boot manager, but I'm only seeing Linux and the Memtests on the list, and when I run sudo update-grub, I'm not seeing W7 on the list.
All the files are still there, I just cant run it. Any ideas?
[/COLOR] [/SIZE][/SIZE]

---

### Post by LowSky on 2011-10-06
depends on how you install ubuntu. you may have erased windows.

open the file manager and see if ther is anything call reservered or a large portion of space. those are your windows files.

---

### Post by Mark Phelps on 2011-10-07
IF, as you said, you "messed up" BOOTMGR for Windows, depending on what you actually did, the os_prober part of update-grub might not be able to find the proper Win7 boot loader parts anymore -- hence, the lack of an entry for it in GRUB.

Since you claim some files are still there, the good news may be that you only clobbered your Win7 boot loader, not the OS itself.

You will have to REPAIR the Win7 boot loader before update-grub will find it and generate the right boot stanza contents.  Since you probably did NOT use the Win7 Backup feature to create a burn a Win7 Repair CD BEFORE you did the dual boot, and you apparently can not boot into Win7 anymore, about all you can do now is go to the link below, download the proper Win7 Repair CD ISO image and burn it to CD:  

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

NOW, however, you will have to purchase the CD image -- which you could have created before for FREE.

Once you have that Repair CD created, boot from it, choose Startup Repair, and run it at least three times.  THEN, you should be able to boot into Win7 again.

And yes, you will have to reinstall GRUB after this, but at least then, when you run update-grub, it should generate an entry for Win7.

---

