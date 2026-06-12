---
title: "Boot repair, Toshiba Satellite C-845D"
date: 2015-02-24
forum: New to Ubuntu
---

### Post by wmarin2 on 2015-02-24
I have a laptop Toshiba Sattelite C-845D with Windows 8 preinstalled
 
Pc fell in an “Automatic startup repair” Loop
 
Acoording to Boot-repair : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Boot repair log BEFORE running recommended repair is:
 [http://paste.ubuntu.com/10397912/](http://paste.ubuntu.com/10397912/)
 
 
Boot repair log AFTER running recommended repair is
 [http://paste.ubuntu.com/10397970/](http://paste.ubuntu.com/10397970/)
 
 
Problem persists, any help is appreciated
 
wmarin

---

### Post by oldfred on 2015-02-24
I do not see any Linux partitions, is this a Windows only issue?
You may do better on a Windows forum.

Boot-Repair only can make minor repairs to Windows, but it looks like you booted it in BIOS mode not UEFI. Your Windows is in UEFI mode.

You really need a Windows repair flash drive or direct boot Windows and see if f8 gets you into repair console.

       [URL="http://www.eightforums.com/"]http://www.eightforums.com/
[/URL]
 Windows 8 UEFI fixes
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)

[URL="http://www.eightforums.com/"]
[/URL]

---

