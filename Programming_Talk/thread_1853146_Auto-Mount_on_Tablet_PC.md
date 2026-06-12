---
title: "Auto-Mount on Tablet PC"
date: 2011-10-01
forum: Programming Talk
---

### Post by N1GHTS on 2011-10-01
I have this tablet PC which needs to automatically mount itself to some network drive on log-in. In the fstab config file I have it configured as "no auto" so a problem with the WiFi network link does not keep it from booting properly. I typed up a bash script that loops the mount command until it's successful.

All I would like to know how I should automatically run this as soon as the user logs in in Ubuntu Desktop 10.04. My biggest issue is that the mount command seems to need root access and I don't want the user to type up the password in this case (it needs to be completely automatic).

Thanks in advance for your help. :D

---

