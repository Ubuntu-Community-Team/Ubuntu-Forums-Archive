---
title: "some files/folders not visible in samba share on USB drive"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by benfindlay on 2008-05-22
I have 3 USB hard drives (formatted ext3) connected to an ubuntu box acting as a file server. These drives are shared as 1 share point using the unionfs program.

I've noticed that some files within certain directories are not visible via my samba shares on an XP machine, but are definitely present on the server.

For example I have episodes 1 to 144 of the security now podcast sitting on the USB drive and shared. Accessing the share reveals 134 files, but vncing into the box and browsing the folder in nautilus shows all 144 episodes there. Also, if I move the folder onto the internal hard drive (also ext3) and share it there, then I can see all 144 episodes.

This problem isn't restricted to just one folder. I have the entire family's music collections backed up and shared on the USB drives as well and some folders are missing from the shares of this too (but visible when I browse the folder on the machine itself.

Anyone have any ideas?

Thanks in advance

Ben

---

### Post by superprash2003 on 2008-05-22
sometimes if file names start with ~ it can get hidden!!try the view hidden folders option

---

### Post by benfindlay on 2008-05-22
Hey, thanks for the reply

Unfortunately I already have the option set to show hidden and system folders in XP.

It just seems plain weird that they're not all visible when shared on the USB drive, but moving them to a fixed IDE drive and sharing them makes them all visible.

Any ideas?
Cheers
Ben

---

### Post by benfindlay on 2008-06-03
Ok, now I've just found that if I go into the samba share via windows and delete all the visible files, the invisible files then become visible again. However if I copy the files I've deleted back in from a local directory on the windows computer, the files that became visible go back to being invisible.

Also if I try to delete the folder that all the files are stored in, I get an error saying the folder is not empty.

Any ideas?

---

### Post by benfindlay on 2008-06-03
*bump*

---

### Post by benfindlay on 2008-06-08
*bump*

---

