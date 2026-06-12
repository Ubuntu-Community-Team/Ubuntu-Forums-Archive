---
title: "Lost Samba password on one PC - how to locate or reset?"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by JeQhdMD on 2014-01-09
Hello all,

I only occasionally need to access files from a small network (5 pc's).  The files are in a workstation running Kubuntu 12.04 (192.168.0.3) (workgroup).  When I click on the workgroup folder, I get the authentication popup, but can't recall or find my user ID and password.  I'm pretty sure the user ID is the same one I use to login to the machine,  so, if I can reset or find my original samba password,  my problem is fixed.   Any  tips appreciated.

---

### Post by devine.steve on 2014-01-09
```
 sudo smbpasswd ID
```

---

### Post by JeQhdMD on 2014-01-10
That worked great - password reset.   Thanks much!

---

