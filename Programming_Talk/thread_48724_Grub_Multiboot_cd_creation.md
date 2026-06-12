---
title: "Grub Multiboot cd creation"
date: 2005-07-13
forum: Programming Talk
---

### Post by Shaggy on 2005-07-13
I'm trying to build a bootable Grub disk that will boot into a couple different utilities that I use a lot at work(memtest and dft).  I pulled the memtest.bin file from the grub boot folder, and downloaded the dft.bin file from the website.

I can make the cd bootable and the menu comes on perfectly fine, but I can't get the files to boot correctly.

the cd is built so.

/memtest86+.bin
/boot/grub/stage2_elorito
/boot/grub/menu.lst

I have the menu.lst boot section set like this

## ## End Default Options ##

title		memtest86+
root		/ 
kernel		memtest86+.bin  
savedefault
boot

# This is a divider, added to separate the menu items below

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

