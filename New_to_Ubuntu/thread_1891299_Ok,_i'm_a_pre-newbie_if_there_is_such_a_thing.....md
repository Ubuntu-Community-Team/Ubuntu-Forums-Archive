---
title: "Ok, i'm a pre-newbie if there is such a thing...."
date: 2011-12-05
forum: New to Ubuntu
---

### Post by Seadevil on 2011-12-05
I am running Ubuntu 11.10 on cd to try it out. It loaded fine.
My problem is... I can't find my hard drives on my computer or any
files and folders.

I looked in Home folder/file systems/     and searched but couldn't find
access.  the Root folder won't display cuz it says I don't have permission.

am I going in the wrong direction?

thank you for any help in advance.

---

### Post by aeiah on 2011-12-05
they should be auto-mounted in /media, but they should also pop up in the side pane of your file browser or in 'places'

---

### Post by Gone fishing on 2011-12-05
In nautilus you should seed devices on the left - double click on the device and it will mount in /media and you will get a short cut on the desktop.

To be able to see and change (be careful) the whole file system Alt F2 gksu nautilus or gksu nautilus from a terminal

---

### Post by fantab on 2011-12-05
> **Seadevil said:**
> I am running Ubuntu 11.10 on cd to try it out. It loaded fine.
My problem is... I can't find my hard drives on my computer or any
files and folders.

I looked in Home folder/file systems/     and searched but couldn't find
access.  the Root folder won't display cuz it says I don't have permission.

am I going in the wrong direction?

thank you for any help in advance.

Unlike in Windows OS, the HDD Partitions are not automatically loaded or MOUNTED, you have to mount them. (This can be made to auto-mount at start up but you don't need it until you have installed Ubuntu on your HDD). 

When you open HOME in a file browser, Nautilus, on the left hand pane you will see all the partitions of your HDD. You will have to click on needed partition to Mount it, then it becomes available to you.

---

### Post by Seadevil on 2011-12-05
thanks but....when i click on the home button on the menu left-hand side, i get a
menu...one item is file system...which opens up a page of folders.
I don't see anything called Nautilus...and /media in view only shows me the dvd-rom
folder.

---

### Post by mastablasta on 2011-12-05
> **Seadevil said:**
> thanks but....when i click on the home button on the menu left-hand side, i get a
menu...one item is file system...which opens up a page of folders.
I don't see anything called Nautilus...and /media in view only shows me the dvd-rom
folder.


Nautilus is the name of default file manager in Ubuntu (kind of like Widnows Explorer in Windows or for exampel total commander or Norton commander).

hard drives are not in home folder. home folder is kind of like My Documents in Windows.
they should be displayed as file systems on the side. often they have only their size displayed or sometimes their volume label.

---

### Post by Gone fishing on 2011-12-05
When you click home you open nautilus it's the default file manager.

I've attached a screen-shot of mine see where it says devices click those and they will mount and become available. You can open from a terminal with the command nautilus and as root (administrator) with gksu nautilus

---

