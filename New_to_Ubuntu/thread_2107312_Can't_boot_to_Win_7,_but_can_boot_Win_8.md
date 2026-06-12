---
title: "Can't boot to Win 7, but can boot Win 8?"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2013-01-21
Okay. I had Win 7 and Win 8 on my computer. I then installed Ubuntu. I am certain that I did not overwrite the win 8 or Win 7 partition. But when I turn my computer on and the option of which OS to start up appears. Win 7 is not on the list but Win 8 is. Anyway to add win 7 to the list seeing as it is on my Hardrive?

Any help is greatly appreciated!

EDIT: If I choose Win 8 from the GRUB menu then it will come up with the option for Win 8 or Win 7. So no pressing problems here but is there still a way to add Win 7 to the GRUB menu.

---

### Post by oldfred on 2013-01-21
Windows only knows how to boot from one active (boot flag) partition. So is Windows 8 also in a primary partition. If not it probably is not repairable and can only boot thru the primary partition that is Windows 7. If 8 is a primary partition you can copy boot files  or repair the Windows 8 install.

Older but Windows still works the same way, if BIOS/MBR. New Windows 8 pre-installed is UEFI with gpt partitioning and is a lot different.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

