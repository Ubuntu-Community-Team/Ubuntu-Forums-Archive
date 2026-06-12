---
title: "Problems with Update manager"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by mmarif4u on 2008-05-08
I was working on my website,Connected to internet that time,Update manager show me that there is one package to update,i hit the update button.But some things goes weird there,and system halt there.i turn it off by power key restart it.it check some files and state for missing files,and there i try to restore it.
After that it successfully logon to my account,but when i try to run update manager, it throw error:
> "E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory), E: The package lists or status file could not be parsed or opened."

I tried add/remove software and synaptic manager also some problem there.
Also search alot for solution, but no luck.
Tried to update the system through terminal and it says:
> sudo: dpkg-restore: command not found
> sudo apt-get upgrade
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
> sudo dpkg-reconfigure -phigh apt
dpkg-query: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
/usr/sbin/dpkg-reconfigure: apt is not installed

Any one...

---

