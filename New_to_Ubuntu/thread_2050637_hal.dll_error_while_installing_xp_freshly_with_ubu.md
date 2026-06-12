---
title: "hal.dll error while installing xp freshly with ubuntu already installed"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by panthera onca on 2012-08-31
I am using ubuntu 12.04 from last 4 months. Previously I had windows 7 and after installing ubuntu I completely deleted the windows partition. Now I want to install windows xp back into the partition which had win 7 using usb. But while installing it giving an error saying hal.dll missing. So please help.
Below is the link to boot info script created using boot-repair
[http://paste.ubuntu.com/1177769/](http://paste.ubuntu.com/1177769/)
windows 7 was in sda1 previously. sda6 and sda5 are just used to keep data.

---

### Post by krustenBrot on 2012-08-31
First of all: You should be aware of the ending of support for Windows XP on April 8, 2014. see [here]("https://en.wikipedia.org/wiki/Windows_XP#Support_lifecycle").
Second: Windows XP is old. So it might be a security flaw to use it.

See **[this]("http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm") **link regarding your problem, there are several possibilities covered. Hope it helps! Good luck!

---

### Post by oldfred on 2012-08-31
Usually hal.dll error is not related to hal.dll but boot.ini having the wrong partition info in it. Not sure what it is with an install.

But you do have a Windows 7 PBR - partition boot sector. Widows has at least two types of PBRs. One has bootmgr to boot Vista/7 and the other ntldr for XP. Since your NTFS sda1 PBR has bootmgr and you do not have Windows 7, you may just need to reformat with gparted, or the XP disk to convert PBR back to XP type.

---

### Post by panthera onca on 2012-08-31
I tried reformatting win 7 partition using Gparted and reinstalling win 7. But the installation is taking too much time nearly 4 to 5  hours and once installation completes windows is not starting at all. when started in safe mode it freezes while loading some disk.sys. I am not getting what is the problem. I have used the same dvd many times but this time it's going wired.

---

