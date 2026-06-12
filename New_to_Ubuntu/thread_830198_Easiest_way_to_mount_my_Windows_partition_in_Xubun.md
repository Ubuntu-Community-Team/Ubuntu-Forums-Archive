---
title: "Easiest way to mount my Windows partition in Xubuntu?"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by LMD1990 on 2008-06-15
As the title suggests- what is the easiest way to mount my Windows partition in Xubuntu?

The Windows partition is sda1 and is ntfs.

---

### Post by shifty_powers on 2008-06-15
it should automount when you go to access it...

---

### Post by Acglaphotis on 2008-06-15
```
sudo mount /dev/sda1 /media/heregoesyourfolderforwindows
```

Probably something like this.

Edit: it seems a bit odd that it doesn't automount.

---

### Post by MasterSander on 2008-06-15
Or would you like to have it mounted each time ubuntu loads, then make a dir where to mount it: sudo mkdir /media/ntfs and edit /etc/fstab, add this line: /dev/sda1  /media/ntfs  ntfs  defaults  0 0

---

### Post by LMD1990 on 2008-06-15
I presume it doesn't automount because the windows partition is NTFS and the Linux one is ext3?

GNOME can find it on it's own I believe, but other than getting at it in GNOME or making it mount via the terminal, i can't get it at. On my Wubi install it was located in /media.

@MasterSander: I was told about adding it to etc/fstab, but a rather Linux-versed friend of mine said he didn't recommend it because it was potentially dangerous...

---

### Post by kansasnoob on 2008-06-15
I can't remember if "ntfs-3g" is installed by default in Xubuntu Hardy or not, but just open synaptic and search for "ntfs". (No quotion marks)

Then see if "ntfs-3g" is installed. If not install it.

Also install "ntfs-config".

I'd give that a 90% chance of fixing your problem, if not it's easily reversible.

I've also found "ntfs-progs" to be handy for extending the ability to read encrypted files in Win partitions and much more, but it's "fiddly" and I'm still learning.

---

### Post by kansasnoob on 2008-06-15
(quotion)

Oops, made a new word again:confused:

---

