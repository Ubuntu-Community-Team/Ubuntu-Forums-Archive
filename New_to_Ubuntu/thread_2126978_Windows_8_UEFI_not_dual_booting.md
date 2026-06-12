---
title: "Windows 8 UEFI not dual booting"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by DRIMAL on 2013-03-18
Hi  I installed ubuntu 12.04  on my dell desktop that came with windows 8 pre-installed. I wanted to dual boot it so I was careful not to mess up with the partitions . But something went wrong somewhere . The ubuntu is up and running but the problem is I can't go back to windows anymore how ever I can still see the window files and partitions from ubuntu.  I ran the bootinfoscript as suggested on this thread and attached the result . please suggest me on how to get back to the windows

---

### Post by oldfred on 2013-03-18
Your Windows 8 install does not look correct. You are missing the Microsoft reserved partition and efi partition does not have any Windows efi files.
You also have wubi installed which I thought could not be done with gpt partitioning. 
Windows only boots from gpt with UEFI.
Windows only boots from MBR(msdos) with BIOS.

It looks like your original Windows install was BIOS/MBR which let you install wubi. The it looks like you converted to gpt partitioning with a full install of Ubuntu and only its boot files in the efi partition.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by DRIMAL on 2013-03-19
so is there any easy fix for this issue ?

---

### Post by oldfred on 2013-03-19
Most of the new Windows 8 systems have a key that just restores system. Be sure to backup any of your data first as it may not keep that. Older Windows 7 systems have the restore system partition (looks like your sda6?) which you can usually boot into. But often better to make DVD set to use as restore. 

Then start over on reinstalling Ubuntu.

---

