---
title: "Removing Grub from MBR, Windows RE not working"
date: 2014-03-20
forum: New to Ubuntu
---

### Post by sdijoseph1 on 2014-03-20
I posted this in a windows 7 forum, but the only response told me to ask those experienced with linux on how to restore the mbr using the backup of the MBR that ubuntu makes.

The original post:

"[COLOR=#323232][FONT=verdana]So, my original issue was that after installing an ubuntu partition on my computer, windows 7 would not go to sleep. After research I presumed this was caused by GRUB being installed in the windows MBR. I then made a system repair disk to run the fix boot and fix mbr commands. However, when I boot from the repair disk no operating systems are listed under the recovery option. If I try and proceed anyway to the command prompt, it won't let me type in the command prompt. I am unsure of what I should try next. I can still access my regular Windows 7 partition fine though."

[/FONT][/COLOR]I also tried using the F8 option when booting Windows and that had the same problem. Is there any way to restore the original MBR through ubuntu? Thanks for any help.

---

### Post by Mark Phelps on 2014-03-21
Are you trying Recovery or Repair?  

Been a while since I used it, but I believe the Recovery option is used to Restore the OS from a backup -- which is not what you are trying to do.

You should be running Startup Repair.

---

### Post by sdijoseph1 on 2014-03-21
> **Mark Phelps said:**
> Are you trying Recovery or Repair?  

Been a while since I used it, but I believe the Recovery option is used to Restore the OS from a backup -- which is not what you are trying to do.

You should be running Startup Repair.

Yep, I am in repair mode.

---

### Post by andy10 on 2014-03-21
Hopefully you have access to a Win 7 recovery disk. boot it and select the command line mode and run this command and reboot: _bootsect  /int60  c:  /MBR _ This will restore the Windows boot sectorand remove grub.

Andy

---

### Post by sdijoseph1 on 2014-03-21
> **andy10 said:**
> Hopefully you have access to a Win 7 recovery disk. boot it and select the command line mode and run this command and reboot: _bootsect  /int60  c:  /MBR _ This will restore the Windows boot sectorand remove grub.

Andy

I have tried to do that, but the problem is my operating system is not listed under available recovery options, and if proceed anyway it does not let me type in the command prompt at all.

---

