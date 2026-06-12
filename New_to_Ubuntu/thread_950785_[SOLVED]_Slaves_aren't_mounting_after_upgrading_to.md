---
title: "[SOLVED] Slaves aren't mounting after upgrading to 7.10"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by sheri68 on 2008-10-17
OK i finally got the Ubuntu 7.4 on my system and it works Yeah!! however I am doing last minute upgrading and such to tweak my mew computer/server and have installed the slave drives which I took out of my old server 2003 system.  at first with 7.4 Ubuntu recognized the slaves and would allow me to search through and open items within these slave drives. now I recently upgraded to Ubuntu 7.10 (this morning) the slave drives can't be mounted error is coming up. This is the first time I am using Ubuntu and starting to get the hang of it (because of my BF I am trying this. By much kicking and screaming before because I didn't know how cool Ubuntu was) no I am starting to doubt my excitedness of Ubuntu. Ubuntu Gods, Please HELP Once again!!!!

---

### Post by nothingspecial on 2008-10-17
What error is coming up?

---

### Post by sheri68 on 2008-10-17
that the drive can't be mounted

---

### Post by Elfy on 2008-10-17
and that's all it says? or does it give some reason? How had you mounted them with 7.04?

Can you post the results of
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by sheri68 on 2008-10-17
yes that is all it says is the volume cannot be mounted. it has a box with a red circle that has a x in it. I did the upgrade through the update manager now I moved on to 8.4 and having the same results it is like ubuntu does not recognize windows files and folders that are on the drive (NTFS) also I am trying to look for my domain computers and having a hard time trying to connect to my other windows computers to see the files. (I have a total of 5 computers and cant see them)

---

