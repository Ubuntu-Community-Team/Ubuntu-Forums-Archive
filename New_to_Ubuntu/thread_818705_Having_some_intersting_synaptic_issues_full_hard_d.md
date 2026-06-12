---
title: "Having some intersting synaptic issues full hard drive?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by wormeyman on 2008-06-04
```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.bz2  Write error - write (28 No space left on device)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.bz2  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2  Write error - write (28 No space left on device)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.bz2  Write error - write (28 No space left on device)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  Error writing to output file - write (28 No space left on device) [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz  Error writing to output file - write (28 No space left on device) [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz  Bad header line [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.gz  Bad header line [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz  Bad header line [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```
```
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


```

Basically the problem is that i cannot update for 2 days.

---

### Post by Oldsoldier2003 on 2008-06-04
> **wormeyman said:**
> ```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.bz2  Write error - write (28 No space left on device)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.bz2  Hash Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2  Write error - write (28 No space left on device)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-i386/Packages.bz2  Write error - write (28 No space left on device)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  Error writing to output file - write (28 No space left on device) [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz  Error writing to output file - write (28 No space left on device) [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz  Bad header line [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.gz  Bad header line [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz  Bad header line [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```
```
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


```

Basically the problem is that i cannot update for 2 days.
clean out your apt-cache:
```

sudo apt-get clean
```
remove archived logfiles
```
sudo rm /var/log/*.gz
```
Use synaptic and mark for complete removal any unecessary packages, also remove packages in the category "not installed (residual config)"
also clear out your /tmp directory


these things should get you enough space to get by until you either add more space to your partition or install a larger HDD.

---

### Post by sayakb on 2008-06-04
Don't forget:
```
sudo apt-get autoremove
```
This will remove all the unnecessary dependencies that are no longer required.

---

### Post by JoshuaRL on 2008-06-04
Yeah, then like Old Soldier says roll through Synaptic or Add/Remove to remove applications you no longer need.  Time to free up some space!

---

