---
title: "[SOLVED] Reinstalling Ubuntu"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by newbuntuxx on 2008-11-13
Hey,

What is the most efficient and safest method to reinstall Ubuntu 8.04 on a system that already has Ubuntu 8.04 on it. Note that this system has four partitions: 
- / root partition
- /home partition
- swap partition
- Back up partition

Obviously, I do not want to lose the contents of the back-up and /home directory. 

Another question, once I reisntall ubuntu 8.04, will the settings saved in my home directory affect my new installtion? or create any system conflicts?

any help is appreciated.

---

### Post by taurus on 2008-11-13
When you reinstall Ubuntu, pick Manual when you get to the partition screen.  Then, mount the first partition to / and format it to ext3.  Mount the second partition to /home as ext3 but DO NOT format it.  In other words, there shouldn't be a check mark in the box before the mount point.  Then, mount the last partition to /backup or whatever mount point you want to use.  And if there is no data on it, format it to ext3 filesystem as well.  But if you want to keep all the backup files on that partition, then don't let the installer format that partition.

---

### Post by Duck2006 on 2008-11-13
When you reinstall ubuntu don't format the home or Back up partition just format your / partition.

---

### Post by LowSky on 2008-11-13
best thing to do is to start up the Live CD and then when you get to the part about partitions, to do it manually.

If you want to save your home and back up partition, dont format them, but do remember to mark the as what they are /home and /back up or what ever you named them to begin with

as for / just formate and install over that partition


Your settings within you home folder can do some fun things like preset up you panels, if all the icons and programs a preinstalled. Also what ever setting you had for some programs with be saved.

To be safe create a backup of you firefox shortcuts and any other data you dont want to get messed up

---

### Post by kansasnoob on 2008-11-13
> **taurus said:**
> When you reinstall Ubuntu, pick Manual when you get to the partition screen.  Then, mount the first partition to / and format it to ext3.  Mount the second partition to /home as ext3 but DO NOT format it.  In other words, there shouldn't be a check mark in the box before the mount point.  Then, mount the last partition to /backup or whatever mount point you want to use.  And if there is no data on it, format it to ext3 filesystem as well.  But if you want to keep all the backup files on that partition, then don't let the installer format that partition.

Excellent explanation!

---

### Post by newbuntuxx on 2008-11-13
Thank you all for the excellent and detailed explanations. Thats what I had in mind...just wanted to confirm....

---

### Post by Settler on 2008-11-13
do what they told you. Indeed it's a great explanation and what is needed to be done.

---

