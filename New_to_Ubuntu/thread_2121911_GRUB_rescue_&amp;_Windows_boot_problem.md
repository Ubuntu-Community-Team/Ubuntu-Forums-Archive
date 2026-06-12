---
title: "GRUB rescue &amp; Windows boot problem"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by Mayatrix on 2013-03-03
So, they were introducing linux on steam recently and i wanted to give it a go. (wasn't really planning to keep it) i messed around with it for a little while
and then just left it on my computer. Since then i was getting all kinds off errors (Catalyst center has crashed, windows power server crashed blue screens etc.) And i was almost certain I was getting this problems from Ubuntu..


I decided to try something i found on the internet [http://blog.fauziahsan.net/dual-boot-how-to-uninstall-ubuntu-from-windows/](http://blog.fauziahsan.net/dual-boot-how-to-uninstall-ubuntu-from-windows/) deleting the linux partions in Computer management (only deleted one tough).


I started my computer up without my windows cd at first and got at a GRUB rescue screen(?) i couldn't do anything with that so i booted ot up from my windows cd. And when i tried to repair it from there it just said this windows cd is outdated for this version of windows, go get one that is compataible (Well not really like that but you get the point!) after that i tried to just reinstall windows but it said it couldn't install on any of my disks


And that's were i am now please someone help! 

PC specs: Intel core i5-2500
Radeon HD 7700 
8 gb ram

---

### Post by oldfred on 2013-03-03
Do you have Windows 8 and are trying or repair with Windows 7? Or using a 32bit repair for a 64bit version. The repairCD or flash drive has to be the same as your install. But can you still go to command line and run fixMBR command? I have run chkdsk on XP with a Windows 7 flash drive, using Windows command line.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

You can also restore a Windows boot loader with Ubuntu or other Linux repairCDs.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

      [/URL]
 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

    [URL="https://help.ubuntu.com/community/Boot-Repair"]
[/URL]

---

### Post by Mayatrix on 2013-03-03
I have the right CD it's Windows 7 64-bit. I don't really know how to get to the command line..

---

### Post by oldfred on 2013-03-03
f8 to get to repair install screen
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)

      
 oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

You will need to boot with your Vista/Windows 7 installation disk or  repair disk. Hit Enter at the language selection prompt then hit "R" to  get to the repair section. You can then select the automatic boot repair  tool, but it often will not do any good. Then select the command prompt  (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors

New chkdsk:
 chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

---

### Post by Mayatrix on 2013-03-03
I get a whole different screen when i'm on the boot menu. And i can't shoose windows or anything like that i'll send you some images

EDIT: [http://imgur.com/oKfDrbp&VUQvIy3&rbe8V1v&68zXF3f&IB4Rqry&L4OTCAv](http://imgur.com/oKfDrbp&VUQvIy3&rbe8V1v&68zXF3f&IB4Rqry&L4OTCAv)

Sorry for the bad quality

RE: EDIT

Managed to get to the command prompt in windows installation cd

---

### Post by Mayatrix on 2013-03-03
I have no idea what just happened but it's fixed Thanks :D!

---

### Post by darkcrimson on 2013-03-03
Glad to hear it!

---

