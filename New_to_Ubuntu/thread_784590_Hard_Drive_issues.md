---
title: "Hard Drive issues"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by auriclecomputers on 2008-05-06
I have a 160 gig Seagate that has my Ubuntu OS and everything on it. Now I also have a 40gig hard drive that I use to store extra files on. Now everytime I try and add a file to it it says:

There was an error copying the file into /media/disk.

Does anyone know how to correct this?

Thank you!

---

### Post by Yudraciell on 2008-05-06
need more in formation on this to help you

a) is it another operating system on that drive
b) you need to check the permissions for the write command

---

### Post by Rocket2DMn on 2008-05-06
Can you please post
```
cat /etc/fstab
sudo fdisk -l
sudo blkid
mount
```

---

### Post by bschleusner on 2008-05-06
Could you post the contents of your fstab file? (/etc/fstab) It could just be that you don't have permission.

---

