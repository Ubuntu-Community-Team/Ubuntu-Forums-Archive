---
title: "Files are locked... someone help please!"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Spoonboy on 2008-05-08
Hey guys,

I'm not having much luck with apt-get since doing a fresh install of hardy. I can't seem to use apt-get anymore, i get the following error:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I tried looking for open synaptic sessions (not sure if i was looking for the right processes) but there aren't any. I also tried typing in some code (cant remember what it was) to remove the lock. Nothing seems to have worked.

When i installed hardy before (prior ro the clean install) it worked fine. The only thing I did differently was make a seperate partition for /home.

Also is there anyway to make sure my user has the most unrestricted rights to the PC? I added myself to the group 'root' if that makes a difference.

Anyone got any suggestions?

Thanks

---

### Post by .rdg on 2008-05-08
Please use sudo before the apt-get command - you do need to have root (uid: 0) rights to do anything with that tool.

---

### Post by quelx on 2008-05-08
You probably just need to add sudo in front of the command

ie ```
sudo apt-get install imapackage
```

---

### Post by Spoonboy on 2008-05-08
Boy do I feel stupid :)

Thanks a lot guys!

---

