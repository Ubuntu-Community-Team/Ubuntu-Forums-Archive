---
title: "need urgent help with ubuntu partition"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by foo123 on 2011-09-12
Hia all. i m new to forum and ubuntu. i installed dual boot ubuntu10/win7 using wubi etc..

however after some virus on win7 i had to format disk and reinstall win7 so now
i can't boot to ubuntu and also the partition is lost and my disk space on win is showing less
(300 GB and not 320GB) 20GB was the ubuntu partition (but maye this is due to 1000B/1024B discrepancy not sure).
So the question is did the format really erased the ubuntu partition and gave it back to win
or did it not
Any ideas how to recover the lost partition back to win and/or uninstall ubuntu as im going
to use this machine for other stuff.

thanx

---

### Post by saltmarshlamb on 2011-09-12
If wubi si still there it will be a file in the C:\ - check this link - it'll tell you the files

[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

---

### Post by ubudog on 2011-09-12
Hi, welcome.

If you re-installed Windows, odds are that it removed the Ubuntu partition.

Can you boot an Ubuntu LiveCD and post a screenshot of Gparted (partition manager)?

---

### Post by ubudog on 2011-09-12
> **saltmarshlamb said:**
> If wubi si still there it will be a file in the C:\ - check this link - it'll tell you the files

[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

@foo123: Were you using Wubi?

---

### Post by saltmarshlamb on 2011-09-12
It's wubi apparently - so no partition, just files.

---

### Post by ubudog on 2011-09-12
> **saltmarshlamb said:**
> It's wubi apparently - so no partition, just files.

Oops, yeah.

@foo123, can you still see the files?

---

### Post by Rubi1200 on 2011-09-12
In all likelihood, Windows overwrote the Ubuntu files.

However, you can use either a LiveCD or some other means to confirm this by looking for the root.disk (try searching within Windows).

If you made a backup of the root.disk prior to the reformat there is a way to restore the Ubuntu installation.

Let us know and then we can move ahead.

---

