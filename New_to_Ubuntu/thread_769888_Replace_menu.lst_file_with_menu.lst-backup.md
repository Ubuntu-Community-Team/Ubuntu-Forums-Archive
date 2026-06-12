---
title: "Replace menu.lst file with menu.lst-backup"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by TBelmont on 2008-04-26
I noticed multiple ubuntu choices in my boot menu after I installed update. After a little research I made a backup of my menu.lst file before changing the original. I damaged the original file menu.lst file and now need to replace it with the menu.lst-backup file I made. I am new to Linux and am unsure how to replace these files.

---

### Post by frup on 2008-04-26
If you can boot in to ubuntu you can just remove the original menu.lst, copy the menu.lst backup and rename it to menu.lst.

in terminal you would do

sudo rm -f /boot/grub/menu.lst
sudo cp /boot/grub/menu.lst.backup /boot/grub/menu.lst

then you would reboot.

If you can't boot (which I would presume if you really messed it up) pop in the live CD and navigate to the mounted drive and do the same process.

---

### Post by TBelmont on 2008-04-26
I was unable to boot directly into Ubuntu so i used the Install disk and loaded directly into the virtual desktop.

---

### Post by TBelmont on 2008-04-27
It worked, thank you!

---

### Post by southernman on 2008-04-27
Please mark your thread as solved by clicking on the link (top right) "Thread Tools" and select solved.

Thank you...

---

