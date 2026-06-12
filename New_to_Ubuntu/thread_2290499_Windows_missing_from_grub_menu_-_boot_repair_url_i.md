---
title: "Windows missing from grub menu - boot repair url incl."
date: 2015-08-12
forum: New to Ubuntu
---

### Post by beau9 on 2015-08-12
Hi, 
I have fairly limited knowledge of ubuntu but a better knowledge of UNIX in general. After attempting to change the grub menu so that I could boot straight into windows, my menu now doesn't give me the option to boot into windows at all. I've tried a boot-repair but that doesn't seem to work. 
I've included the boot-repair url. Please could somebody tell me if there are any files I need to edit and what commands to give to the terminal and I'd be grateful! 

[http://paste.ubuntu.com/12065483/](http://paste.ubuntu.com/12065483/)

---

### Post by oldfred on 2015-08-12
Grub menu shows you have Windows.
But if named it as recovery mode for sda1, your Windows boot partition and sda2, your main install which also has boot files.
Your sda6 is the only one that should be the recovery.

Your manual entry in 40_custom looks like it should work also?
But With Windows 8 or later, you must make sure Windows fast startup or really just hibernation must be off.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Grub only boots working Windows which means Windows not in hibernation nor needing chkdsk. Best to have a repair flash drive with Windows repair tools. You may be able to use Boot-Repair to temporarily restore the Windows boot loader to MBR, boot Windows (maybe f8 for repair console) and make sure it is working without fast startup. Then use Boot-Repair to restore grub.
       
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

[/URL]
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

