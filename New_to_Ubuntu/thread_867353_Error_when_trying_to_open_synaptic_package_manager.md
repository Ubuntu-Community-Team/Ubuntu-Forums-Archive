---
title: "Error when trying to open synaptic package manager"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Peterfc on 2008-07-22
Hi All

I have just tried to go to add/remove in Mythbuntu and when i click on it nothing happens. I went to synaptic package manager and got the following error any idea how i solve this?

I tried to use add/remove and synaptic package manager to install the codec for a new DVD i install today that only plays music.

I installed Vlc into Ubuntu i have Ubuntu/Mythbuntu 50 50 on an 80gb drive. I can't install anything at the moment any ideas.

Thanks for reading this post

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by iaculallad on 2008-07-22
Open your terminal and issue the command below as the message says:

```
sudo dpkg --configure -a
```

---

### Post by steveneddy on 2008-07-22
Please reply back and if that fixed it, mark the thread as solved please.

:D

---

### Post by Peterfc on 2008-07-22
Thanks and solved

---

### Post by northern lights on 2008-07-22
All good, and while not the utterly most important of all, not what steveneddy meant.

On the top of your first post, under "Thread Tools" select "Mark This Thread As Solved"...

---

