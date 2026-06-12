---
title: "New Computer"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by jonathan71381 on 2014-04-27
Hello Ubuntu Nation!

I am looking to purchase a new computer.  I know that when you have an old mac, and you buy a new mac, you are able through a program called time machine I think to take all the data from one machine to another I think from one file.  So, you instantly transform all settings, documents, downloads, programs, apps ect....  If I were to purchase a new computer because this one is probably about to go dead, is there a way to backup this entire Linux operating system and move it all, everything in it to my new machine without having to do it all individually?  If I am not mistaken, when you change to new mac, even your place in the video games are saved.  Is this possible with Ubuntu?

Thanks you are all the best!!!!

Jonathan

---

### Post by Bob_Younkin on 2014-04-27
You can't just image the drive to the new computer.  There are a whole new set of drivers needed for the new hardware, etc.  But the good news is tha all your "stuff" is in the Home directory.  I would do a new install and then just copy the home directory to the new computer.

Bob

---

### Post by pqwoerituytrueiwoq on 2014-04-27
depending on the hardware you can just transfer you install to any other system
you can use clonezilla if you want, personally i would just swap the HDD in the 2 systems unless the new computer has a better one
just remove any special drivers (nvidia, ati/amd, and wifi drivers) before using it on another system
don't forget to remove /etc/X11/xorg.conf if you made one

---

