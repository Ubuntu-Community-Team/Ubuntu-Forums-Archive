---
title: "superuser gedit and untitled document"
date: 2011-08-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2011-08-07
Whenever I use gedit as superuser to open files it always opens an untitled document as well.

Example:

gksudo gedit /etc/fstab
opens fstab plus an extra tab - "untitled document"

gksudo gedit /etc/fstab /etc/default/grub
opens both the files and an extra tab - "untitled document"

The same also happens with gksu
Is this a bug or something I'm doing wrong?

If I just use sudo to open documents I don't get the extra tab, though I understand using sudo is not recommended for graphical apps these days?

---

### Post by sgage on 2011-08-07
> **x-shaney-x said:**
> Whenever I use gedit as superuser to open files it always opens an untitled document as well.

Example:

gksudo gedit /etc/fstab
opens fstab plus an extra tab - "untitled document"

gksudo gedit /etc/fstab /etc/default/grub
opens both the files and an extra tab - "untitled document"

The same also happens with gksu
Is this a bug or something I'm doing wrong?

If I just use sudo to open documents I don't get the extra tab, though I understand using sudo is not recommended for graphical apps these days?

I have the exact same issue.  It's a bit of a pain. I'll admit, I'm using sudo now instead of gksu for gedit.

---

### Post by mc4man on 2011-08-07
> Is this a bug or something I'm doing wrong?
Longstanding bug - atm just ignore, close out, whatever
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076)

---

### Post by x-shaney-x on 2011-08-07
Hmm, it would be a bit easier to ignore if it didn't insist on asking if I want to save changes to the document every time :(

---

### Post by mc4man on 2011-08-07
> **x-shaney-x said:**
> Hmm, it would be a bit easier to ignore if it didn't insist on asking if I want to save changes to the document every time :(
For most of the last 8 weeks it also did that  here, no longer does though, gedit closes out without comment

(while probably not making a diff. in this regard,  here I've set nautilus-gksu to work in gtk3 until that's fixed also
[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/817383](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/817383)

---

