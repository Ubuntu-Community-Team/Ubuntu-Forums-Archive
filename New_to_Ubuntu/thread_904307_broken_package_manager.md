---
title: "broken package manager"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by AirwolfUK on 2008-08-29
hi everyone, new to Ubuntu so go easy on me.....

I have been having some issue with my hard drive and ran fsck in read only mode to fix some problems.

Now when i try and run the update manager or package manager i get the following error

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (2 No such file or directory), E:The package lists or status file could not be parsed or opened.'

dpkg from terminal also gets the same error

Running on Lenovo T61, 3GB RAM, 120 Gbyte disk

any help appreciated

Solved - i navigated to the folder and renamed status-old to status and now seems to be OK

---

### Post by ashmew2 on 2008-08-29
Read My Signature's Last Line ^^

---

