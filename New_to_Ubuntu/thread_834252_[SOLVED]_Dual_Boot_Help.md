---
title: "[SOLVED] Dual Boot Help"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-06-19
I currently have a dual boot between Ubuntu 8.04 and Windows XP, but I want to remove Windows XP.  What would be the proper way to go about this?

---

### Post by Nikitas350 on 2008-06-19
Run this command on terminal:
gksudo gedit /boot/grub/menu.lst
Then delete the lines that look like this:

title Windows
root (hd0,0)
makeactive
chainloader +1

(There are at the end)
If you want to be sure you can post here the menu.lst and tell you exactly what lines you have to delete...

---

### Post by bigfootnmd on 2008-06-19
OH Grasshopper(new user)!  The most powerful tool in the world is GOOGLE.  The second most powerful tool is the SEARCH function on this site.

Five seconds in GOOGLE produced this helpful article that tells how to do exactly what you want.
[http://ubuntujourney.wordpress.com/2008/04/12/remove-xp/](http://ubuntujourney.wordpress.com/2008/04/12/remove-xp/)

Good luck!

---

### Post by subaruwrc01 on 2008-06-19
Ok, I removed windows, but I how do I expand my ubuntu partition into the remaining space?

---

### Post by Victormd on 2008-06-19
To completely wipe XP, simply use gparted and format the partition where XP is installed (you will have to unmount the partition first - right click on the icon in your desktop if there is one and click on unmount), format it as ext3 (or whichever file system you'd like) and that's it.
Doing this will not remove the entry from the grub menu, then you can simply edit the menu.lst
```
sudo gedit /boot/grub/menu.lst
```
and remove the last lines of the file, per Nikitas350 post.

---

### Post by Victormd on 2008-06-19
> **subaruwrc01 said:**
> Ok, I removed windows, but I how do I expand my ubuntu partition into the remaining space?

**[COLOR="Red"][SIZE="3"]BACKUP ALL YOUR DATA FIRST[/SIZE][/COLOR]**

To expand the partition, you'll need to use the gparted live CD because it won't work on any mounted partitions (you can also use the ubuntu live CD and use gparted from there, but I prefer booting directly to gparted).
Boot from the gparted live CD and then you will be able to resize your current partition.

---

