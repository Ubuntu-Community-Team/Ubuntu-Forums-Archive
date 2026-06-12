---
title: "[SOLVED] deleted tmp files, now nothing in menu will open"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by iansane on 2008-06-17
Hi, I deleted all the files in /tmp thinking it was OK since they are all just temp files. I even deleted hidden temp files. Now I'm thinking I should have wondered why temp files would be hidden but it's to late now.

Anyway, nothing under Applications, Places, or System will open.

Before I reboot, is there a way to fix this? Or will rebooting fix it?

I don't want to reboot and loose access totally so I'm waiting for a response before I do.

Thanks

---

### Post by vbman11 on 2008-06-17
Rebooting will probably fix it. The temp files held the menu items and everything else. You should NEVER delete temp files WHILE the computer is running and be careful if the computer is off. If rebooting doesn't fix it reply back.

---

### Post by iansane on 2008-06-17
Ok that fixed it. Even the non hidden ones reapeared.

Were you being funny or am I misunderstanding what you said about not deleting tmp files while the computer is running?

I deleted them cause I thought it was a good idea after reading an article about sudo at linux-magazine.com 

Why are they in tmp if they are required files?

---

### Post by cariboo on 2008-06-18
They are only needed while Ubuntu is running, they are automatically deleted when you shutdown.

Jim

---

### Post by iansane on 2008-06-18
> **cariboo907 said:**
> They are only needed while Ubuntu is running, they are automatically deleted when you shutdown.

Jim

so why did an article at linux-magazine.com suggest for admins to use sudo to delete them to free up space? Specifically the article says to use that dangerous command that is warned against here on the forum

```
 sudo rm -rf /tmp/* 
``` to delete everything. BTW that command didn't delete hidden files till I added . before the * but apparently even some of the non hidden files are nessesary

---

### Post by kalesh7 on 2008-06-18
Can you post a link to the article, might be an interesting read.
Can't comment much without seeing more of the article.

---

### Post by iansane on 2008-06-18
> **kalesh7 said:**
> Can you post a link to the article, might be an interesting read.
Can't comment much without seeing more of the article.

You have to register and log in to read most of the articles but here it is.

[http://linuxmagazine.com/id/4824](http://linuxmagazine.com/id/4824)

The article is called "sudo voodoo".

This is the part I read before I deleted all the tmp files.

When a task requires root powers, and assuming the user has the right to perform the task at hand as root, the user simply prefaces the command with sudo. For example, say the /tmp directory is filled with oodles of scratch files created by a myriad of users. While each user can only remove his or her own scratch files, a user with the right to run rm as root (as dictated by sudo) can clean the entire directory with one command:
```
sudo rm -rf /tmp/* 
```

registration is free and I think it's a good source of info and news of the open source community.

---

### Post by kalesh7 on 2008-06-18
from what I have read both in your post and the article, they are only giving an example of what can be done and not suggesting that you do it. I agree that it was not a good example to use, but still think twice before using sudo on anything.

---

### Post by iansane on 2008-06-18
yep. lesson learned. Thanks

---

