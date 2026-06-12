---
title: "desktop and ntfs disk problem"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by chkontog on 2013-06-26
Hello, i have install ubuntu in the first sata disk that i have and when i connent the second disk (that is ntfs), when i get into ubuntu it doesn't show the menu at the left.What it goes wrong?

---

### Post by dino99 on 2013-06-26
which ubuntu are you using ?
which DE (unity/gnome-shell/...) is used ?
are you asking for the menu in the top taskbar ? or the icons updown list of unity/gnome-shell ?

if you can open a terminal, then copy/paste each of these lines, one at a time:
dconf reset -f /org/compiz/
unity --reset-icons

---

### Post by chkontog on 2013-06-26
> **dino99 said:**
> which ubuntu are you using ?
which DE (unity/gnome-shell/...) is used ?
are you asking for the menu in the top taskbar ? or the icons updown list of unity/gnome-shell ?

if you can open a terminal, then copy/paste each of these lines, one at a time:
dconf reset -f /org/compiz/
unity --reset-icons

i'm using ubuntu 12.04 and i can't open terminal when i connect the second sata disk.

---

### Post by chkontog on 2013-06-29
up

---

### Post by Mark Phelps on 2013-06-29
Let's try a different approach, then ...

Connect ONLY the second drive and try to boot from that.  Tell us, in detail, what happens when you do that.

Also, I presumed you installed Ubuntu from a DVD or USB stick, right? If so, with ONLY the second drive connected, boot from the Ubuntu DVD or USB stick, and when you get to a desktop, run Gnome Partition Editor (Gparted) and tell us what it shows in terms of the partitions, sizes, and filesystems on that second drive.

---

