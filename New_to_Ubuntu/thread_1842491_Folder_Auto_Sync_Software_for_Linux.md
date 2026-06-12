---
title: "Folder Auto Sync Software for Linux"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by aura7 on 2011-09-11
I have a Seagate External Hard Disk, I need a software similar to Seagate Sync software they provide for windows where you can sync your folders with that of hard disk folder to automatically backup changed data.

I need a similar software that can sync two folders automatically in Ubuntu. I am not looking for Deja Dup kind of software where the format stored is different from the original files. 

I want a simple sync software and the contents of both the folders should be same ... i mean no encryption required.

---

### Post by The Cog on 2011-09-11
rsync is the program that one would normally use, but it does not watch th directories and automatically sync - you may have to schedule it to run every few minutes. The command would be something like:
```
rsync -a /home/me/mydata /home/media/8907435905
```
Use the command **man rsync** to see the rsync manual pages.

---

