---
title: "Oracle 10.2 installation URGENT!"
date: 2005-09-24
forum: Programming Talk
---

### Post by alfotis on 2005-09-24
> Hi all,

After a LOT of Googling around installing Oracle database 10.2 on Ubuntu I resulted to NOTHING! 

The installer keeps saying things about my distro (not being Fedora, SuSE etc) and I don't know what to do!!

I need Oracle database on my server and I don't want to switch to any other distro

Please help!!!

Thanx,
Fotis

This should be my problem, but resolved it by adding a file redhat-release in my /etc directory that contains "Red Hat Enterprise Linux AS release 3 (Taroon) and now I can FINALLY run the installer

---

### Post by evilghost on 2005-09-24
Sounds like the Oracle installer is **absolute garbage**.

---

### Post by bsussman on 2005-09-24
Gee - I hope Oracle doesn't depend on some package, feature, parameter that is not present in ubuntu...

---

### Post by murkin on 2005-10-10
[QUOTE=alfotis]This should be my problem, but resolved it by adding a file redhat-release in my /etc directory that contains "Red Hat Enterprise Linux AS release 3 (Taroon) and now I can FINALLY run the installer[/QUOTE]

Fotis,
Would you be able to tell me where you found this file? I don't understand what it is you did. You added a file named "redhat-release" to the /etc directory. (Was this a text file?) Within this file you typed the words "Red Hat Enterprise Linux AS release 3 (Taroon)".

Thanks for your help!

---

### Post by ape on 2005-10-11
Try the information from this [location]("http://www.togaware.com/linux/survivor/Oracle_10g.shtml")

---

### Post by munitras on 2005-10-11
try running the installer as follows

```
./runInstaller -ignoreSysPrereqs
```

Oracle have not certified 10.2 to run on Ubuntu as such you will need to bypass pre-requirements checking as described above.

---

