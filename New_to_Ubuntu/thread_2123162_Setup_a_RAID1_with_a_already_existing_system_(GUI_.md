---
title: "Setup a RAID1 with a already existing system (GUI only)"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by riahc3 on 2013-03-07
Hello

 I want to setup a RAID1 on a existing Ubuntu system with a new drive and a boot drive. Ive read about doing it thru terminal but I cant really see when a drive fails or not so I perfer (and its easier) to do it with a GUI tool. How can I do this?

 Also this would be a soft RAID1.

 Thanks

---

### Post by Lisiano on 2013-03-07
Earlier, you could set up a Soft RAID using the Disk Utility, but since the dev responsible for it removed the RAID management feature... The only other GUI for managing a raid is [Webmin](http://www.webmin.com). It's a browser-based GUI for managing most stuff on a Linux system.

However, you can't (easily) set up a RAID on your /(root) partition if you already have a system on it without reinstalling it.

---

### Post by riahc3 on 2013-03-07
> **Lisiano said:**
> 
However, you can't (easily) set up a RAID on your /(root) partition if you already have a system on it without reinstalling it.

It seems fairly easy to do using command lines...but I perfer GUI.

---

