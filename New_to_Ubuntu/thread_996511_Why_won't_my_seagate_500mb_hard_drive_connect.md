---
title: "Why won't my seagate 500mb hard drive connect?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by dblxx on 2008-11-28
It says....Cannot mount volume?....when I plug it in.

---

### Post by earthpigg on 2008-11-28
NTFS? did you do the 'properly remove hardware' thing last time you had it plugged into a windows box?

---

### Post by abeisgreat on 2008-11-28
is it by any chance formatted to NTFS?

---

### Post by dblxx on 2008-11-28
Not sure what NTSF means and I just plug and un-plug it from my work laptop (windows) and not sure how it's formatted.  I just opened it and started using it.

---

### Post by abeisgreat on 2008-11-28
Well ubuntu doesn't play nice with ntfs, which is probably what it is formatted to, there is an app to allow you to mount ntfs but I dont remember what its called

---

### Post by earthpigg on 2008-11-28
> **dblxx said:**
> Not sure what NTSF means and I just plug and un-plug it from my work laptop (windows) and not sure how it's formatted.  I just opened it and started using it.

easiest solution: plug it back into your windows machine. before you remove it, right click on the trey icon and then go to 'safely remove hardware' or whatever its called. then, you should be good. do that every time ;)

nerdiest solution: something involving the CLI.

edit: NTFS = (windows) NT File System. for compatibility, fat32 is your best bet.

---

