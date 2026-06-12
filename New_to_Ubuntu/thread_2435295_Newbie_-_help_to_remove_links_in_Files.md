---
title: "Newbie - help to remove links in Files"
date: 2020-01-19
forum: New to Ubuntu
---

### Post by mc-b on 2020-01-19
Hi

how do I remove these links?

[ATTACH=CONFIG]284821[/ATTACH]


Thanks  

Mike

---

### Post by deadflowr on 2020-01-19
Those are directories. Not links.
The X symbol means your current user cannot access the contents.

If your user is an admin you can use the command line (the Terminal program) to use the admin command sudo to remove them.
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
[https://www.howtoforge.com/linux-rmdir-command/]("https://www.howtoforge.com/linux-rmdir-command/")

---

### Post by TheFu on 2020-01-19
They might be external mounted storage too.  Hard to tell from a GUI.  Really need to see a proper **ls -al** on those specific directories and a **df -Th** to see what is mounted, where.

---

### Post by digikin on 2020-01-19
Anything in your /media folder is generally a disk attached to your computer.  If you want to remove files on a disk or external drive attached you will have to mount it somewhere.  
Open up the application DISKS in Ubuntu to learn more about what and where that disk is. I attached a picture that shows what it looks like on my desktop.

---

