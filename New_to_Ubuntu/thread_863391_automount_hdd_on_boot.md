---
title: "automount hdd on boot"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by muted1987 on 2008-07-18
hey all i need this command to start om boot so i dont have to do it everytime i turn pc on any help appreciated


sudo mount /dev/sdb1 /mnt/data

---

### Post by dracayr on 2008-07-18
read a bit into

man fstab

or google /etc/fstab

dracayr

---

### Post by bumanie on 2008-07-18
What is the drive formatted to? Ntfs or ext3? Do you want to name it /media/data?

---

### Post by muted1987 on 2008-07-18
> **bumanie said:**
> What is the drive formatted to? Ntfs or ext3? Do you want to name it /media/data?


its actually a reiserfs drive and the command i gave is where i want it mounted as all shortcuts to drive are using that mount point

---

### Post by bumanie on 2008-07-18
In terminal > gksudo mousepad /etc/fstab then add this line to /etc/fstab and save, the drive should automount upon boot.
> /dev/sdb1 /media/data reiserfs defaults, 0 1 I think mousepad is the text editor for xubuntu - I use ubuntu in which case one uses gnome editor or gedit for short

---

### Post by muted1987 on 2008-07-18
> **bumanie said:**
> In terminal  then add this line to /etc/fstab and save, the drive should automount upon boot.


ok will do reboot and post results

worked great all i did was change media to mnt thanks

---

