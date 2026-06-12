---
title: "Reinstalling without home"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by baddnady23 on 2008-05-10
I recently moved my home directory to its own 400gb partition and kept all the ubuntu system files on its own 20gb partition in order to protect my home from any sort of reinstallation i might ever have to do.  If and when i do reinstall the OS, how do I get it recognize my home partition that is already established, or will it do this all on its own?

---

### Post by llamakc on 2008-05-10
> **baddnady23 said:**
> I recently moved my home directory to its own 400gb partition and kept all the ubuntu system files on its own 20gb partition in order to protect my home from any sort of reinstallation i might ever have to do.  If and when i do reinstall the OS, how do I get it recognize my home partition that is already established, or will it do this all on its own?

Unless the installer changes in the future, you tell it to USE your drive/partition as /home but NOT TO FORMAT IT. The "NOT FORMAT IT" part is of utmost importance for obvious reasons.

I keep a separate partition for my /home and have moved up from the days of Warty, with the same /home being used previously on several Debian installs.

---

### Post by HotShotDJ on 2008-05-10
> **llamakc said:**
> I keep a separate partition for my /home and have moved up from the days of Warty, with the same /home being used previously on several Debian installs.My /home has been with me since the days of RedHat 6.* :)  Of course it has been moved across several machines and harddrives and cleaned out (with the utmost care) on a regular basis.  It has even survived an accidental repartitioning, formating and OS installation. (Praise be to RIPLinux and TestDisk).  I've had my /home partition longer than I had my ex! :twisted:  Using a separate partition for /home was one of the best decisions I ever made.

---

### Post by baddnady23 on 2008-05-10
ok so it sounds alot easier to keep it around than i was probobly imagining...

---

### Post by kansasnoob on 2008-05-10
This is all very interesting to me. I have one dual boot (8.04 w/ XP) that has a shared FAT 32 partition, but I have wondered about just having a "home" partition that could be shared by both XP and Ubuntu with even less hassle.

I've looked at this, but just don't know. Installing anything in Windows can be such a pain.

---

