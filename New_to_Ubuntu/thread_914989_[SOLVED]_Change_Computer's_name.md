---
title: "[SOLVED] Change Computer's name"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by elmoosecapitan on 2008-09-09
How do I do it?

---

### Post by tuxxy on 2008-09-09
Try /etc/hostname

open a terminal and type 

```

gedit /etc/hostname
```

---

### Post by Malac on 2008-09-09
In a terminal:
```
sudo hostname <whatever>
```To make this permanent edit hostname file with:```
gksu gedit /etc/hostname
```
or KDE:
```
kdesu kate /etc/hostname
```
_AND_
Do the same to /etc/hosts otherwise you will have sudo issues

Hope this helps.

---

### Post by elmoosecapitan on 2008-09-09
After a reboot everything worked magically. Thanks everyone! I have been wanting to add 'Pandora' to my computer's name for a while. Fitting for a ThinkPad with Linux, no?

---

### Post by GWBasic on 2009-03-03
Can I change my computers host name in Ubuntu 8.10 *without* using the shell?  IE, can I accomplish this in the GUI?

---

### Post by Iowan on 2009-03-03
I generally use command line, but I suppose it could be done from a text editor - _IF_ you can open it with root privileges.

---

### Post by Francewhoa on 2010-03-12
There is an **easier, safer and faster** way to do this at [http://ubuntuforums.org/showthread.php?p=8955992#post8955992](http://ubuntuforums.org/showthread.php?p=8955992#post8955992)

---

### Post by Iowan on 2010-03-12
deleted

---

### Post by dcstar on 2010-06-19
> **GWBasic said:**
> Can I change my computers host name in Ubuntu 8.10 *without* using the shell?  IE, can I accomplish this in the GUI?

Add the **nautilus-gksu** package, and then you can right-click the file for Open as Administrator.

---

