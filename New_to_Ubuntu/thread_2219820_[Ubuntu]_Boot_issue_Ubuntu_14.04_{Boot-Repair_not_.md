---
title: "[Ubuntu] Boot issue Ubuntu 14.04 {Boot-Repair not working}"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by bhargav2904 on 2014-04-25
Hey guys,

I was trying to install ubuntu Server 14.04, with Ubuntu 14.04 and windows 7 already on my PC. In between the process of installation, I received an error (flash message) and the laptop immediately re-booted. Since then i am stuck with a black screen during boot. I tried running the boot repair option, but didn't get the Recommended Repair link and got only the Bootinfo Summary link.

[http://paste.ubuntu.com/7331195/](http://paste.ubuntu.com/7331195/)

The above is the diagnostics run by it . Kindly help me out here. Stuck in a really bad place. Couldn't even take a back up of my application documents :cry: . Please people help me out.

---

### Post by oldfred on 2014-04-25
You are only showing one probably boot partition that is corrupted and the LVM partition. And the LVM only shows root and swap.

Did you do a full drive LVM server install or encrypted install? That always has been a full drive install that erases the entire hard drive.

Hope you have good backups. 
You may be able to recover some data with an application like testdisk or photorec, but must immediately stop using system and boot with a live system that does not use swap as that also overwrites more data.
Anything overwritten will be gone.

---

