---
title: "Just did Wubi"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by rsratner on 2012-01-15
Just installed Ubuntu via Wubi. seems like a very good option. Is there some way for me to access files in Ubuntu, for instance, jpgs or mp3's that were saved under Windows Vista. (I've already downloaded the restricted software files).

---

### Post by chipbuster on 2012-01-16
Ubuntu should allow you to access those files normally through the file manager. Look for a "folder" (it's really a mounted partition) that has the name that you gave your windows hard drive when you installed it. It should be there.

Unfortunately, it doesn't work the other way around, and Windows can't read files off of Ubuntu without some extra software.

---

### Post by bcbc on 2012-01-16
It's mounted under /host. Press Alt+F2, enter: "/host" (not the quotes)

Then Ctrl+D to bookmark.

---

### Post by mike555 on 2012-01-16
Remember Wubi installs Ubuntu inside Windows on a limited size area, if you are thinking of moving the pictures etc. into Ubuntu you will quickly fill the area set for Ubuntu .
   But you can view the files on Windows no problem ....    later you should do a "real" install to a separate partition , that way if/when Windows gets messed up it wont effect Ubuntu.

---

### Post by Frogs Hair on 2012-01-16
You have a 30 Gb maximum which has to be selected during installation . I think it defaults to around 17 Gb if you don't manually select anything . 

Open the file browser and under view select status bar to see the available space .

---

