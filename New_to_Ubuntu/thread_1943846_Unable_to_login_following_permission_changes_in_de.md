---
title: "Unable to login following permission changes in device manager (11.10 + Gnome)"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by symanuk on 2012-03-20
(Running Gnome 3 on Ubuntu 11.10) Everything working well (at least a couple of months), until recently when I changed the permissions through the device manager on the sda1 /2/ 3 drives, thinking it would save all the switching I seem to have to do between users in order to see / use files I previously copied across from an external drive.
Now when I boot up the Ubuntu splash screen loads indefinitely, and if I go in through the GRUB / recover option, i'm getting a load of negative permission messages back (regardless of using the fsck or remount options)
Either way = unusable machine (Laptop Dell Inspiron n5050), and no way through to login.
I'm looking for: (1) a way back in so any help greatfully received (answers need to be pretty basic as i'm a novice), and (2) if i'm to learn anything, a decent thread on setting permissions within Ubuntu / Gnome 3.
I'm new to both Ubuntu & Linux, so please be gentle!! Cheers

---

### Post by MG&amp;TL on 2012-03-20
I imagine something's going wrong when ubuntu tries to automount the drives/partitions.

Until someone more competent than myself turns up, could you answer a few questions:

1) Roughly what errors from recovery mode? 

2) Can you access the root prompt from recovery mode? If so, continue to 3 & 4

3) Post output of

```
cat /etc/fstab
```4) Post the gist (there's probably quite a lot) of:

```
dmesg | grep sda | less
```looking for things like 'error' or 'permission' - you can omit the pipe to less (| less), it just makes it easier to read.

---

