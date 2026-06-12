---
title: "I have the following message which I have no idea on how to fix"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by paul.stead.main on 2014-05-05
I keep trying to do updates but I get the following message:

W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Any thoughts to how I can get past this?

---

### Post by papibe on 2014-05-05
Hi paul.stead.main.

Open a termina, and run this commands:
```
sudo apt-get clean

sudo mv /var/lib/apt/lists /var/lib/apt/lists.old

sudo mkdir -p /var/lib/apt/lists/partial

sudo apt-get clean

sudo apt-get update
```
Let us know how it goes.
Regards.

---

