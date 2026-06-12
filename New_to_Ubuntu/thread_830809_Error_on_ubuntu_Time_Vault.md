---
title: "Error on ubuntu Time Vault"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by appoloin on 2008-06-16
hi 

im getting this error when updating ubuntu 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i try to sudo run dpkg --configure -a in terminal

i get this error:

ed@ed-desktop:~$ sudo dpkg --configure -a
dpkg: failed to write status record about `libxxf86dga1' to `/var/lib/dpkg/status': No space left on device
ed@ed-desktop:~$ 

i think this happen when i installed time vault yesterday. can anyone tell me where i can find the backups that time vauld did so i can delete it?

---

### Post by skymera on 2008-06-16
Is your drive full?

try:

sudo apt-get clean

---

