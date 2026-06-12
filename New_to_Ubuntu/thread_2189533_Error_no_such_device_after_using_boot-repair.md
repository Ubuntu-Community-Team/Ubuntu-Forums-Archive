---
title: "Error no such device after using boot-repair"
date: 2013-11-22
forum: New to Ubuntu
---

### Post by abkanu on 2013-11-22
Hi,  In installed Ubuntu along side Windows 8 on my HP Envy laptop but was having trouble getting my external monitor to work so I decided to re-install Ubuntu.  After the re-install of Ubuntu, I started getting the error ...

error: no such device: 9de95...etc
grub rescue>

I was able to bring up grub using the following commands which I found on this site ......
 
set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
insmod normal
normal

This brought me to the grub menu and I was subsequently able to log into Ubuntu.  I the ran boot-repair again and it said it installed correctly and gave me this link which I'm supposed to post somewhere if I continued to have issues ..
...[http://paste.ubuntu.com/6461644/](http://paste.ubuntu.com/6461644/).

I re-booted and still have the same "grub rescue" screen.  I also tried running boot-repair from my usb recovery disk with the same result.

Can someone please help with this.

Thanks.

---

### Post by leeper69 on 2013-11-23
Have you had any luck with your boot problem?
Can you still boot into window$ 8?

---

### Post by abkanu on 2013-11-23
No, I tried a few things but didn't make any headway so I tried a system revovery using my Windows 8 recovery USB.  After the recovery, I got a new windows error "0xc0000225. Error" "device not forun" on startup.  Apparently there is a program "bootrec.exe" on Windows 7 recovery USB's which can be used to fix boot records, but it is not present on Windows 8 recovery disks so I'm not sure where to go from here.

---

### Post by leeper69 on 2013-11-23
Hi
it sounds like your drive has read error problems. I had to replace mine last year.

---

### Post by oldfred on 2013-11-25
You may need a Windows repair flash drive, which you have to make before Windows breaks. Or from another user with Windows 8.
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

But you should be able to directly boot from UEFI menu or from one time boot key.
HP puts many .efi files into the efi partition, so then Boot-Repair does create too many boot entries in grub menu. You may want to houseclean those. Instructions in link in my signature.

You installed an older Ubuntu that does not have the bug fix that now is only in 13.10. It will be in 12.04.4 next Jan and all later versions. So you cannot use the os-prober boot entries in grub menu to boot Windows. But the Boot-Repair entries should work.

What model HP? Other Envy models:
      
 HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

### Post by ppeterb on 2013-11-25
This sounds very much like post   #1581   in thread   "[Boot-Repair] Graphical tool to repair the PC boot in one click"   where the Boot-Repair operation puts a wrong uuid into the grub under repair.

---

