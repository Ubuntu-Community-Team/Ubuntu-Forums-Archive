---
title: "How to remove linux partition on external drive"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by jdh01 on 2008-04-27
Hello,
Somehow I created a large partition on my external hard drive.  I would like to delete that partition so that the whole hard drive is readable in both ubuntu and windoze.

The the portion of the drive that was already in use, the original partition, is readable by both.

--John

---

### Post by artir on 2008-04-27
sudo apt-get install gparted

---

### Post by shearn89 on 2008-04-27
gparted should be fine, you have to make sure that the external drive isn't mounted before trying to format it though - just right click on the icon on the desktop (if there is one), or in "computer", and go "unmount" before running gparted. If it gives you loads of errors, then boot up with your install cd, hit alt-f2 and type "gksudo gparted". that should work fine. JUST BE CAREFUL! gparted is a "weapon of mass destruction", and can be dangerous if you're not careful.

---

