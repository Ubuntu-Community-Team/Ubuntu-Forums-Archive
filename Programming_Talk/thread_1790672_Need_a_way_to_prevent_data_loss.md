---
title: "Need a way to prevent data loss"
date: 2011-06-25
forum: Programming Talk
---

### Post by tdrusk on 2011-06-25
Hey guys,
last night I was working on a project, the program crashed and overwrote the file with a blank file. I had to start over. Is there a way to basically create a folder that keeps a backup of every file that goes into it automatically. For example, I create X.txt. After I overwrite it it pushes the original to X0.1.txt and makes a new X.txt. I am looking for the easiest and simplest solution possible. 
Thanks!

---

### Post by LoneWolfJack on 2011-06-25
for normal editing, try gedit:
Preferences -> Editor -> Create a backup copy of files before saving

other than that, rsync is your friend.

if you really need on the fly (or event-triggered) backups, you may be out of luck. I would be interested in such a solution myself.

---

### Post by linuchsan on 2011-06-25
Take a look at nilfs

---

### Post by tdrusk on 2011-06-25
> **LoneWolfJack said:**
> for normal editing, try gedit:
Preferences -> Editor -> Create a backup copy of files before saving

other than that, rsync is your friend.

if you really need on the fly (or event-triggered) backups, you may be out of luck. I would be interested in such a solution myself.
Yeah. I just hacked together some crap script that backs up every minute. Thanks.
[http://ubuntuforums.org/showpost.php?p=10980882&postcount=6](http://ubuntuforums.org/showpost.php?p=10980882&postcount=6)

---

