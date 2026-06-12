---
title: "How can I remove python3?"
date: 2013-02-05
forum: Programming Talk
---

### Post by zozza on 2013-02-05
I don't understand this at all.

Whereis python3:

python3: /etc/python3.1 /usr/lib/python3.1 /usr/local/bin/python3.3m-config /usr/local/bin/python3.3-config /usr/local/bin/python3 /usr/local/bin/python3.3 /usr/local/bin/python3.3m /usr/local/lib/python3.1 /usr/local/lib/python3.3

So I want to purge it (some stuff is not there) then re-install properly:

sudo apt-get purge python3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python3 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

But:

python3
Python 3.3.0 (default, Oct 28 2012, 15:56:01) 
[GCC 4.4.3] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 

How can python3 be run if it is "not installed"?

Thanks!

---

### Post by Bachstelze on 2013-02-05
The package python3 is just a metapackage. Do

```
dpkg -l | grep python
```

and you will see all your Python packages.

---

### Post by zozza on 2013-02-05
Thanks.

But I still cannot delete the packages.

For example:

Package libpython3.1 is not installed, so not removed

But it does appear in the list of packages.

---

### Post by MadCow108 on 2013-02-05
```
 /usr/**local**/bin/python3.3
```
this is a non package managed installation, it cannot be removed with apt or dpkg
you have to delete it with rm (or if you still have the source you installed from *make uninstall* could work)

---

### Post by zozza on 2013-02-06
I see.  So all of the below will need to be manually removed:

/etc/python3.1 /usr/lib/python3.1  /usr/local/bin/python3.3m-config /usr/local/bin/python3.3-config  /usr/local/bin/python3 /usr/local/bin/python3.3  /usr/local/bin/python3.3m /usr/local/lib/python3.1  /usr/local/lib/python3.3

This would explain why apt-get remove do not do anything.

---

