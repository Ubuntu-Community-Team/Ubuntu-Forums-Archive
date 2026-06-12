---
title: "how to make a rescue or recovery disk of my ubuntu installation"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by fr.theo on 2008-10-02
hello all, 


does anyone know how to make an image of my Ubuntu installation so that if it crashes or I require to reinstall it to its current set up. like a  rescue disk or recover disk without me havening to install it all over again and reinstall all the drivers, codec and programs.


thanks to all who have help me i really appreciate it.

---

### Post by fr.theo on 2008-10-02
sorry to bring it up again, but does any one know how to do this or a site i might be able to goto.


thanks once again.

---

### Post by TVAbuntu on 2008-10-02
Best place to start: [http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

I like to rsync, then save file via jungle disk to amazon (cost me less than $1/month, and I don't have to worry about fires, natural disasters, etc)

---

### Post by fr.theo on 2008-10-02
thank you i will give it a go, do you now of any method of doing it yourself possibly, sorry to be a pain.

thank you.

---

### Post by Paqman on 2008-10-03
Depends how much spare storage you have. Backing up the actual system itself (as in, minus your data) would probably come in somewhere 6-10GB. You might be able to compress that and get it onto a DVD. You could always create a partition on your hard drive to store backups on, although that won't protect you from a hard drive failure.

Rsync is a very efficient way of doing backups, there's a GUI for it called grsync that makes it really straightforward to use. Sbackup is another popular automated backup tool.

---

