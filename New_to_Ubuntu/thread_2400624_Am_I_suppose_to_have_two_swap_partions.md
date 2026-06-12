---
title: "Am I suppose to have two swap partions"
date: 2018-09-07
forum: New to Ubuntu
---

### Post by robertzito on 2018-09-07
Am I suppose two have two swap files?
[ATTACH=CONFIG]281014[/ATTACH]

---

### Post by TheFu on 2018-09-08
If you like.  It is up to you.  Pre-18.04, swap was normally created in a partition.
Use the **swapon -s** command to see which is active and how much is being used. ** free -mh** is also handy.

Please post plain text inside code tags whenever text output is used. Save bandwidth for people who pay by the bit and it lets people with poor eyesight scale without being limited to the pixel resolution.

One of your swaps isn't encrypted. The other is.  Generally, if you go to the effort to use encryption for storage, then having the swap encrypted would be important too.  Also, don't use suspend or hibernate the OS if the machine might be touched by another person. This is a security thing.  My rule is always to power off the machine if I'm going to move it outside the current building.

---

