---
title: "Lost username"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by aumock on 2008-09-19
i bought a laptop today for cheap from a friend, and it has ubuntu on it. I dunno what version though i think its Hardy. I am good with ubuntu but i dunno how to recover a username. Any help is nice.

Thanks 
Christian

---

### Post by Rocket2DMn on 2008-09-20
Moved to Absolute Beginner Talk - please don't post help questions in the Tutorials & Tips section, this area is for guide and HowTos only, and requires staff approval.  Thank you.

If you reboot your computer into the recovery mode kernel (the second option at the GRUB boot menu), select the root terminal option, you can run
```
ls /home
```
and see the home directories of all the users on the system.  You should be able ot see your friend's login name.  If you need to change the password, this is the place to do it, run
```
passwd *username*
```
subsituting in for *username* of course.
Then you can restart the computer normally
```
reboot
```

---

