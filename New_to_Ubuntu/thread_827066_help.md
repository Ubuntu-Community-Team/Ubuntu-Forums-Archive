---
title: "help"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by blake7 on 2008-06-12
i have lost data, and have just loaded a live cd how can i find the lost documents with live cd
it is on ubuntu-8.04-desktop-the data iam trying to find is documents and music and saved web pages off fire foxs
cheers

---

### Post by Cypher on 2008-06-12
Please don't create multiple threads about the same issue..I posted a response on your original thread.

---

### Post by blake7 on 2008-06-12
sorry
but i thought that no one was reading the other post due to my bad tiles

---

### Post by spiderbatdad on 2008-06-12
There seem to be multiple threads on the same issue regarding several questions.

This one now has 3 threads. The search tool on the quick links bar above has a feature..."Find All Your Threads." In case you have been losing site, and don't know how to find your threads.

Starting multiple threads on the same topic is confusing to those trying to help. It also clutters the forum with partially answered questions and makes the search tool less effective.

---

### Post by paulderol on 2008-06-12
okay everything SHOULD be in the filesystem under /home/YOURUSERNAME/* [represented by ~ in most abbreviations]

firefox stuff is under ~/.firefox 

folders beginning with "." are hidden, and usually contain program info and assorted things you don't need to always have a hand in. 

music should be in ~/Music
video in ~/Video

and once you find them, move them to a removable USB drive via the gui.

i realize that that may not work, as it might not want you to write to a disc from the live cd. 

so try a terminal login (IN THE ORIGINAL LOGIN SCREEN without a new install) and do 
```
sudo cp ~/Music /removable/drive
```
```
sudo cp ~/.firefox /removable/drive
```

where /removable/drive is the mount point of a USB stick [usually in /media/* ]

Otherwise, install to the empty space on the drive and allow ubuntu to find the previous user accounts elsewhere on the drive.


Although now that i have written this out i realize i am both obsolete and replying to a duplicate post. 

oh well.

---

