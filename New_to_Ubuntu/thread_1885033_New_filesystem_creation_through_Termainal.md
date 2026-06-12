---
title: "New filesystem creation through Termainal"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by samir19406 on 2011-11-22
Dear All,

I am new to UBUNTU. I have installed it in Oracle VM Virtual Box. I have installed default one. So not created any file system. Default created are...

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             2.0T  2.4G  1.9T   1% /
none                  285M  640K  285M   1% /dev
none                  292M  296K  291M   1% /dev/shm
none                  292M  108K  292M   1% /var/run
none                  292M     0  292M   0% /var/lock

Now I want to create 30 GB new filesystem named as **/oracle**, through terminal only.

Please give me a proper guidance to create new filesystem like this way.. I want to use space only from / system. there is 1.9T space available. I have 3 TB Hardisk on my computer.

Thanks in Advanced.....

---

### Post by lechien73 on 2011-11-22
Hi & welcome to the forums,

Firstly, you need to resize the root partition to allow space for your /oracle partition. You can't resize a mounted partition and, since it's the root partition, you'll need to boot from a Live CD/USB.

Could I ask why you want to do this purely using terminal commands? GParted Live would be easier.

---

