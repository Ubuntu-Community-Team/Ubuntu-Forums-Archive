---
title: "cannot mount volume"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by amsterdam63 on 2008-06-09
I just got a Linksys g wireless adapter, and when I put in the installation CD, I get the message "Cannot mount volume: Invalid mount option when attempting to mount the volume". What do I need to do? Please help, I would greatly appreciate it.

---

### Post by logos34 on 2008-06-09
you can't use those manufacturer driver install cds--they're all for windows.

---

### Post by amsterdam63 on 2008-06-09
So how do I get my wireless card up and working?

---

### Post by Cypher on 2008-06-09
Even if you can't use the software on the install CD's, you should still be able to mount them.

Can you try the following commands in the terminal?
```

sudo mount -tiso9660 /dev/cdrom /mnt/cdrom

```
This should mount the CD and you can browse the contents in the file manager..

---

### Post by amsterdam63 on 2008-06-09
Ok, I entered that into the terminal, but I'm not really sure I can still find what I'm looking for in the file system.

---

### Post by Cypher on 2008-06-09
In the terminal, if the "mount" command didn't complain..then you can do
```

cd /mnt/cdrom
ls -l

```
to see the contents of the CD. You MIGHT find some documentation there, if you see executables, they are likely the Windows drivers that can't be used unless you use ndiswrapper..

---

### Post by logos34 on 2008-06-09
that command has a typo.  And you have to make the mountpoint first (it doesn't exist by default).  Or it's easier to just use your default cdrom mount point as listed in **/etc/fstab** (probably **/media/cdrom0**):

sudo mount -t iso9660 /dev/cdrom /media/cdrom0

or 

sudo mkdir /mnt/cdrom

sudo mount -t iso9660 /dev/cdrom /mnt/cdrom

---

