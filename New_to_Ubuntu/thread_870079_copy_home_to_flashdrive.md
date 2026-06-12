---
title: "copy /home to flashdrive"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by petegreenhorn on 2008-07-25
Hi , i would like to move my home partition  (running gutsy)to a new machine (running hardy)and was wondering if i can transfer it to a flash drive and then copy it to a new drive . how would i achieve this (if it's possible of course)

---

### Post by steveneddy on 2008-07-25
The last time I did this (about 6 weeks ago) I opened my /home folder, hit CTRL+h to show all hidden files, CTRL+a to select all files, then drug them into the flash drive folder.

---

### Post by bobnutfield on 2008-07-25
See the post on this page "Simple Backup/Config Restore".  This has a very good use of the rsync command for this purpose.  Very efficient and complete.  

Bob

---

### Post by DGortze380 on 2008-07-25
never mind, bob is right, see my post in the other thread so that you maintain all your correct permissions etc.

---

### Post by DGortze380 on 2008-07-25
sorry.. deleting

---

### Post by philinux on 2008-07-25
If you install the new machine with different username and password you'll have to chmod and chown the home folder, as you probably know. I would also recommend putting home on its own partition if you haven't already.

---

