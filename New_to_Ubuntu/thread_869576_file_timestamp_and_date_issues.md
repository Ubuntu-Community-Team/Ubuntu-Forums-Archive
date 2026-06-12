---
title: "file timestamp and date issues"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by m_atif on 2008-07-24
Hi,
I am facing a bizarre issue here.
My systems (4 in total) are giving a time that is say 15:20 pm. Now when I touch/create a file (in NFS mounted directory) the timestamp is incorrect, and is in past (almost 53 mins behind). This is giving me headaches in case of Make utility.
The problem persists if I change the system. The time on NFS server is correct. Its just that touching or creating a file results in timestamp in past. 

I have only commandline available.. Any ideas?

---

### Post by dave.com on 2008-07-25
This is only a guess okay, here goes:

Open a terminal, login root (ie. sudo su -)
type the command update-grub
exit root user
see if your problem is gone
if not, go back into root user and type the command ```
chroot / /bin/bash
```
then repeat the update-grub command and exit shell, exit root and see if that worked.

---

### Post by m_atif on 2008-07-25
Naa! that would not work. 
I don't see the connection of my problem with the update-grub command. 
If there is a connection let me know...

---

