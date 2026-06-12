---
title: "Duplicate sources.list entry"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by veledrom on 2013-06-24
Hi,

I'm new in Linux and trying to run Synaptic Package Manager but error below appears. How do I solve the issue? Which lines should I remove

Thanks

**My Linux:**
Ubuntu: 12.04 LTS
Linux ubuntu 3.5.0-30-generic #51~precise1-Ubuntu SMP Wed May 15 08:48:19 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux



**ERROR:**

```

W: Duplicate sources.list entry http://downloads-distro.mongodb.org/repo/ubuntu-upstart/ dist/10gen amd64 Packages (/var/lib/apt/lists/downloads-distro.mongodb.org_repo_ubuntu-upstart_dists_dist_10gen_binary-amd64_Packages)
W: Duplicate sources.list entry http://downloads-distro.mongodb.org/repo/ubuntu-upstart/ dist/10gen amd64 Packages (/var/lib/apt/lists/downloads-distro.mongodb.org_repo_ubuntu-upstart_dists_dist_10gen_binary-amd64_Packages)
W: Duplicate sources.list entry http://downloads-distro.mongodb.org/repo/ubuntu-upstart/ dist/10gen i386 Packages (/var/lib/apt/lists/downloads-distro.mongodb.org_repo_ubuntu-upstart_dists_dist_10gen_binary-i386_Packages)
W: Duplicate sources.list entry http://downloads-distro.mongodb.org/repo/ubuntu-upstart/ dist/10gen i386 Packages (/var/lib/apt/lists/downloads-distro.mongodb.org_repo_ubuntu-upstart_dists_dist_10gen_binary-i386_Packages)

```


**MY SOURCES.LIST CONTENT:**

```
###### Ubuntu Main Repos
deb http://uk.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://uk.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://uk.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
```

---

### Post by grahammechanical on 2013-06-24
These two commands should solve this. The first removes/deletes all the files (sources lists) in the lists directory/folder. The second replaces them. I have had to use it a few times.

```
sudo rm /var/lib/apt/lists/* -rf
```
```
sudo apt-get update
```

Regards.

---

### Post by TheFu on 2013-06-24
There is a subdirectory under /etc/apt/ that appears to have the mongodb entry at least twice, perhaps more.  Look in /etc/apt/sources.list.d/

---

### Post by oldos2er on 2013-06-24
Moved to Absolute Beginners.

---

