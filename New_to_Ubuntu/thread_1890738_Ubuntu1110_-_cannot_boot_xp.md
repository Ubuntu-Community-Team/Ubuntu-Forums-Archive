---
title: "Ubuntu1110 - cannot boot xp"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by monte001 on 2011-12-04
I installed ubuntu 1110 on the HD which has many ubuntu's distros.

I can boot any other distro from the grub except win xp.

I have win xp on sda1.

the grub looks like this:

insmod part_msdos
drivemap -s (hd0) ${root}
chainloader +1

BTW, I can never boot puppy from any other ubuntu's grub menu.

can anyone help please.

monte

---

### Post by Mark Phelps on 2011-12-04
When next in Ubuntu, open a terminal and enter "sudo update-grub". That will regenerate the GRUB menu and re-add the entry for XP.

See if it boots after that.

---

### Post by lechien73 on 2011-12-04
It also might help if you download and run the boot info script from [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

When you've run it, post the contents of the RESULTS.txt file here between CODE tags (the # button on the toolbar).

---

