---
title: "Can;t access external hard drive because i'm not owner"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Djalmahal on 2008-05-08
Hi, my girlfriend  has this Seagate Maxtor Onetouch 500 GB hard drive that I would like to use for backup and that is set up for her Mac. Now, it shows up but any attempt to write to it result in error message saying I don't have permission. I would like to use the Flyback application to use this hard drive. How can I grant myself permission?

Under permissions it says that owner is 99, as well as that i am not the owner and I can;t change the permission

Thanks

---

### Post by inportb on 2008-05-08
If you want, you can exercise your sudo privileges to create a subdirectory, make it yours, and then backup as a regular user.

So... let's say **/media/disk** is where the hdd is mounted, **/media/disk/backup** is where you want to put the backup, **djalmahal** is your username, and **/home/djalmahal** is what you want to backup. In that case...

> sudo mkdir /media/disk/backup
sudo chown djalmahal:djalmahal /media/disk/backup
cp /home/djalmahal /media/disk/backup/

---

