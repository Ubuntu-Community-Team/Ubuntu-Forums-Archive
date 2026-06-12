---
title: "How do I change screen resolution before Ubuntu starts?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Blofeld on 2008-09-12
Hi, I have this problem:  my 17" CRT monitor with 1024*768 screen resolution has gone bust, so now I'm temporarily using a cruddy old 14" (or 15", not really sure) CRT with only VGA resolution of 640*480.
So how do I tell Ubuntu to start with a new screen resolution?  I guess I have to enter some command in the boot menu, right?  What command would that be?
Just choosing the boot option "recovery mode" doesn't work as it only starts the command line.
In Windows XP I did this by starting in safe mode (by pressing F8 during the startup process).  But I don't know how to do this in Ubuntu.
I'm using Xubuntu 7.04.  Many thanks.  And please have mercy on me, life behind a 14" is mighty tough ...

---

### Post by celticbhoy on 2008-09-12
You could try this from Grub, edit the boot line for the entry and add vga=xxx following the table below :-

  VGA Resolution Codes for GRUB & Lilo
--- Depth --
Colors  bits  640x480  800×600  1024×768  1152×864  1280×1024  1600×1200
   256    8   vga=769  vga=771   vga=773   vga=353   vga=775    vga=796
 32000    ?   vga=784  vga=787   vga=790   vga= ?    vga=793    vga= ? 
 65000   16   vga=785  vga=788   vga=791   vga=355   vga=794    vga=798
 16.7M   24   vga=786  vga=789   vga=792   vga=795   vga=799

Only problem is I dont know if it change your X session, but worth a try.

You could also boot into safe mode and use sudo dpkg-reconfigure xserver-xorg.

---

### Post by Blofeld on 2008-09-12
I tried > dpkg-reconfigure xserver-xorg and it worked like a charm.
Many thanks, Celtic!

---

