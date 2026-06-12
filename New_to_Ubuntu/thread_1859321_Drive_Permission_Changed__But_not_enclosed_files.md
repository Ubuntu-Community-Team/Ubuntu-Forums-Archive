---
title: "Drive Permission Changed  But not enclosed files"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by utfan2012 on 2011-10-13
I Can't access files on one of my internal ext4 hard drive. I tried gksudo nautilus then properties and changed the group. Now I can access the home folder but all the folders and files in there are locked. I have done it a couple times now and each time have selected apply to enclosed files and folders but still are locked. Is this a bug or can this be solved?

---

### Post by utfan2012 on 2011-10-13
After a little more digging I found a command named chown -r but dont really know how to run it. let alone navigate in the terminal =/

---

### Post by utfan2012 on 2011-10-13
[http://ubuntuforums.org/archive/index.php/t-994413.html](http://ubuntuforums.org/archive/index.php/t-994413.html)

That helped alot and now solved. 

Let's say you have a folder known as /media/storage, and you want storage + everything inside to be owned by fred:fred

sudo chown -R fred:fred /media/storage

The -R is key - it means it'll change all files/folders inside to those exact ownership. I can change ownership and permissions of all files/folders on my backup drive 


wooohooo solved all by myself and I even used the terminal.

---

