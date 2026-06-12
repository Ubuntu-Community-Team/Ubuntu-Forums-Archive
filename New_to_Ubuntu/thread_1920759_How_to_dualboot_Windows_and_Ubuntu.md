---
title: "How to dualboot Windows and Ubuntu?"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by saber388 on 2012-02-05
I started with Windows 7 first and after a while I wanted to dualboot it with Windows XP. I didn't know that I needed to change some stuff about bootmanager and that things. So my PC was unusable until I discovered Ubuntu. I am running it for a few days now and I am impressed with it but I just can't get over one thing - games. So my question is how can I make my Windows 7 active again? I have Windows XP and Windows 7 on CDs and also Ubuntu. I read some posts about this dualbooting thing but I just can't get it. 

Here are screens from GParted with my HD partitions:

[COLOR="Red"](Edit: moved to attachment)
[/COLOR]
Windows 7 is on dev/sda5
Ubuntu is on dev/sda
dev/sda1 is formatted (I just copied few files there so I could use them if I need to format my Windows 7 partition)

Also it doesn't matter if I am going to use Windows XP or 7 because I will use it only for games.

---

### Post by oldfred on 2012-02-05
If your XP was sda1 & you installed 7 to sda5, that is why you cannot boot Windows. Windows only boots from a primary partition sda1-thru sda4 and must be the active (boot flag) partition. When you installed 7 it literally moved all the boot files to the XP sda1 partition so it could boot. When you deleted that partition you deleted the Windows 7 boot files. Windows will not recognize a boot flag on a logical partition.

You either have to reinstall to a primary partition or create a bootable NTFS partition and (somehow) put the boot files into that partition. I am not sure if a Windows repair will put the files into it or not. So move boot flag back to sda1 and see if a Windows repair works.

If you have a backup of the XP partition you will see the boot files, probably the files normally in the 100MB boot partition were in XP's partition:
Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

