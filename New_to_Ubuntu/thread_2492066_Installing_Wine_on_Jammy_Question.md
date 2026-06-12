---
title: "Installing Wine on Jammy Question"
date: 2023-10-29
forum: New to Ubuntu
---

### Post by bhubunt on 2023-10-29
Hi, 
I got error codes when I tried installing Wine of Jammy OS just now and the suggestion to try apt-get update.

When I did, the following code emerged.

What do these code lines suggest?


```
apt-get update
Reading package lists... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied) 
```

---

### Post by #&amp;thj^% on 2023-10-29
Your hint is this: "Permission denied"
Use:
```
sudo apt update
```
Apt needs admin privileges.

---

