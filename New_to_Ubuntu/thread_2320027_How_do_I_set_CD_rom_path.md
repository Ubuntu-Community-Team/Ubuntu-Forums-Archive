---
title: "How do I set CD rom path"
date: 2016-04-09
forum: New to Ubuntu
---

### Post by henrykyonza.1 on 2016-04-09
I have 15.10 l ubuntu installed and I was working with apt-cdrom and add cdrom in synaptic. But every time i try lubuntu mounts the CD in /media/(user name/whatever but both synaptic and apt-cdrom look in a different path..(I forget which)
I found a work around but I have to apply it every time  i use each app as both apps unmount the cd when done..

It's a massive pain.

---

### Post by christiaan3 on 2016-04-12
I think your cdrom gets in the /dev/cdrom directory.
You can just mount it manually to whatever directory you want.
You can automatically mount your cdrom drive using the fstab file, located in /etc/fstab 

I would prefer taking a look at this page:
 [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

