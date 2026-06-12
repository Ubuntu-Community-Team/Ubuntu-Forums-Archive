---
title: "Error when installing updates"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Dispatch on 2008-05-09
I have 188 updates to install (I just installed 7.10 today) and want to install all the updates because I read to do that before upgrading to 8.04.  Well, when I got to install the updates this is what I get:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can someone please help me.  And should I install the updates before upgrading?  Thanks!

---

### Post by Xiong Chiamiov on 2008-05-09
Did you try doing what it said?  That's one of the best error messages ever!
```

sudo dpkg --configure -a
sudo apt-get update; sudo apt-get upgrade

```

---

### Post by Bubba64 on 2008-05-09
open the terminal and type sudo dpkg --configure -a and hit enter I don't rember if it will ask you for your password. Then try the update again watch carefully though in the terminal before you close for any update-upgrades that might have been interrupted and will finish,  before you close the terminal

---

### Post by Dispatch on 2008-05-09
Thanks guys!  I had tried that twice but for some reason it didn't work until I copied what you wrote.  I must have typed something in wrong before.  But thanks!

---

### Post by Xiong Chiamiov on 2008-05-09
You may not have sudo-ed it.

---

### Post by Bubba64 on 2008-05-09
> **Xiong Chiamiov said:**
> You may not have sudo-ed it.

That was my thought.

---

