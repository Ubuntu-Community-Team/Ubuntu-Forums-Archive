---
title: "[SOLVED] Best way to back-up multi user system"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-11-29
I am looking to do a clean install after a couple of years of experimenting with all sorts of packages & desktop/window environments, and I would like to know the best way to back-up all users files & folders including firefox bookmarks for a multi user system. I dont know if this will make a difference when I re-install, but I have a seperate home partition (still want to back-up just in case).

Any advice gratefully received.

---

### Post by celticbhoy on 2008-11-29
Meant to say - I want to backup to a usb stick.

---

### Post by albandy on 2008-11-29
You can use tar,rsync,...

with tar you can package and compress the /home directory
for example:

sudo tar zcvf /backup/home.tgz /home

This will copy all the contents and configurations of all users


Or use rsync.

sudo rsync -av /home /backup

rsync is perfect when you use network drivers to do the bakcup, but use NFS or similar to maintain the file owners and perms, else use tar

---

### Post by albandy on 2008-11-29
for example, tar with usb stik:

sudo tar zcvf /media/disk1/home.tgz /home

for restore it:

cd /
sudo tar zxvf /media/disk1/home.tgz

---

### Post by celticbhoy on 2008-11-29
Cheers for the help.

---

