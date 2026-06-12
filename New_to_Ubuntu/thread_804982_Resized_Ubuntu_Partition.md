---
title: "Resized Ubuntu Partition"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by skymera on 2008-05-23
Hey guys.

Earlier i booted the 8.04 LiceCD and launched gparted.
I resized my Ubuntu partition down to 10GB.

All went well, so it said.

However now it wont boot properly.
I get stuck into a console and cant get a GUI.

startx says /etc/X11/X isn't executeable :confused:

It gives errors so i think it's mounting read-only.

Im thinking of reinstalling, bust as a last resort. im sick of redoing absolutely everything.

Any help appreciated.

---

### Post by Raccoon1400 on 2008-05-23
Post your /boot/grub/menu.lst file.
You could also try running
sudo dpkg-reconfigure xserver-xorg
to reconfigure X.

---

### Post by skymera on 2008-05-23
I cant see how resizing a partition can stop X working to be honest.

My grub is fine i checked it.
I think the problem is it's mounting read only.

I'll post some errors laters.

---

### Post by unutbu on 2008-05-23
Please post:

```
sudo fdisk -l
cat /boot/grub/menu.lst | grep ^title -A4
```

---

### Post by unutbu on 2008-05-23
/etc/X11/X is a symlink to /usr/bin/Xorg.
Is the / filesystem being mounted properly? For example, if /usr is in a separate partition and it is not getting mounted properly, you might get the symptoms you're describing.

Have you tried 
```
ls -l /etc/X11/X
ls -l /usr/bin/Xorg
```
just to see if these files are in the right place (and with the executable permission bit set)?

---

### Post by skymera on 2008-05-23
everything is in one partition.

I'll try your ideas thank you.

---

