---
title: "Windows 8 not booting"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by karsten3 on 2014-04-22
(I am a noob to ubuntu)
So i did a dual install of ubuntu onto my pc which came with windows 8 but when I try to boot to windows, I get this error mesage: ```
Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert your windows instelation disk.

2: Choose your language setting, and then click "Next".

3: Click "repair your computer"

If you do not have this disk, contact your system administator or computer manufationer for assistance.

File: \Boot\BCD

Status: 0xc000000e

Info: The boot configuation data for your PC is missing or contains errors.

```
Please help

---

### Post by oldfred on 2014-04-22
Did you turn off fast boot in Windows? It may have issues recovering from hibernation.
Did you resize Windows from inside Windows with its partition tools and reboot Windows so it can run chkdsk. It may have issues with size change and need chkdsk.

Best to use your Windows install disk or if purchased system the repairCD or flash drive that they suggest you make to fix your system.

Is this pre-installed Windows. If so directly booting from UEFI menu may get you into the internal repair console, where booting from grub never seems to let you do that.

Better info on Windows issues.
 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by karsten3 on 2014-04-23
Ok my PC came with windows pre-installed would it be best to use boot-repair?

---

### Post by oldfred on 2014-04-23
Boot-Repair can only do minor fixes to Windows, you need a Windows repair CD or flash drive.


Once you get it going or if you have a friend or work computer with Windows 8 you can make a repair disk. Otherwise you have to pay to download one. Some third party Windows partition tools also may do chkdsk or make better Windows fixes.
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)


 Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by karsten3 on 2014-04-23
how would i make a repair disk?

---

### Post by oldfred on 2014-04-23
Same way you make any ISO a bootable CD/DVD or flash drive. You cannot just copy but have to have a tool to both extract ISO and make it bootable in the format for CD/DVD or flash drive.

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
      
 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by karsten3 on 2014-04-24
Ok so I tried using boot repair but I rebooted and now stuck in grub rescue mode

---

### Post by karsten3 on 2014-04-24
One more thing I can't change boot settings or boot from USB

---

### Post by oldfred on 2014-04-24
You should always be able to get into UEFI/BIOS.
But some systems with fast boot on, only can get to UEFI from Windows.

 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

If locked up, sometimes totally powering down, remove battery if laptop and hold power switch down for 10 sec or so to drain residual power. The you may be able to use correct key to get into BIOS.

---

### Post by karsten3 on 2014-04-24
I think fast boot is on so is there any other option?

---

### Post by oldfred on 2014-04-24
Did you try the full power down? Sometimes then you have to try several times with correct UEFI/BIOS boot key to get into UEFI.

What computer is this? 
A few very early UEFI systems had major issues. Originally blamed on Linux but found to also be caused by Windows. Or a vendor UEFI design issue.

---

