---
title: "cd to /home/mk not working"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by ssuave on 2012-07-25
Hi,
If I use : cd ~/mk
its working, where mk is a folder placed in home.
but : cd /home/mk
is NOT working. it gives an error: "can't cd to /home/mk"

Could you help? I need it working as its written in the makefile which I receive and I dun want to edit all the makefiles.

---

### Post by philinux on 2012-07-25
> **ssuave said:**
> Hi,
If I use : cd ~/mk
its working, where mk is a folder placed in home.
but : cd /home/mk
is NOT working. it gives an error: "can't cd to /home/mk"

Could you help? I need it working as its written in the makefile which I receive and I dun want to edit all the makefiles.

It would be /home/yourusername/mk

---

### Post by d2btoo on 2012-07-25
perhaps cd /home/username/mk will work.


as ~/ really represents /home/username not just the /home

edit: oops! ninja'd, please remove this.

---

### Post by ssuave on 2012-07-25
> **philinux said:**
> It would be /home/yourusername/mk

That means I need to edit this path in all the places.
any way out plz?

---

### Post by The Cog on 2012-07-25
Perhaps put a symbolic link to /home/yourusername/mk from /home/mk? This is the command to do that:
```
sudo ln -s ~/mk /home/mk
```
and to remove it again when done:
```
sudo rm /home/mk
```

---

