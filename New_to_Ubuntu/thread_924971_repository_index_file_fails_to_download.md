---
title: "repository index file fails to download"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by guest_user on 2008-09-20
Here's the error message after I updated the system; I canceled when reloading checking for updates after the update, not sure if it caused it:

ould not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


[http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2)

---

### Post by northern lights on 2008-09-20
Have you recently added any software sources?

Can you post the exact error you get when updating?

Please also post the output of ```
cat /etc/apt/sources.list
```Thank you.

---

### Post by guest_user on 2008-09-20
ok so now universe works but the wine repo didn't so I think it most likely has to do with the repo side; asked about the wine repo before and someone said its quite normal as the server's cranky at times; I did not add any new repos recently

---

