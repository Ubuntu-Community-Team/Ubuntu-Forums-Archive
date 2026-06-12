---
title: "Howto Fix Unknown Partition Type 0x7 when booting Windows Operating Systems from Grub"
date: 2006-11-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Demon012 on 2006-11-06
To fix this problem change your menu.lst record to:

title=<insert windows name here e.g. Windows XP>
root (hd1,0) <The partition that your windows install is on>
map (hd1) (hd0) <this remaps the drives so that the windows bootloader does not get confused>
map (hd0) (hd1) <same as above>
makeactive 
chainloader +1


The reason for this problem is when you installed the Windows Operating System you had that hard disk as the primary boot drive in the BIOS so when the Windows bootloader goes to load hd0,0 it actually finds another partition and in your case that is probably either a Swap partition or a ext2/ext3 partition with Ubuntu installed. 

Hope this helps,

Demon012

---

### Post by eldarel on 2009-01-08
Thanks very much Demon012, it was exactly my error, and the solution :D

Short, clear, focused...Great

---

