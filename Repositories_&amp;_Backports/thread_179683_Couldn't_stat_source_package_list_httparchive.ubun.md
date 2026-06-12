---
title: "Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse"
date: 2006-05-20
forum: Repositories &amp; Backports
---

### Post by dhruv_1884 on 2006-05-20
Hi
In the last few days whenever i've tried ro update my system, i've got the following message 

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse  Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_ binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems


when i ran apt-get update the following errors were encountered

.....
.....
.....
....
...
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  Sub-process gzip returned an error code (1)
.....
.....
.....
..
...

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
......
........
....


my source list is the same as the one given in the first thread of his forum by ubuntu_demon
====
 Sticky: my recommended breezy sources.list
ubuntu_demon 
=====


any help guys


thanks 

regards


dhruv

---

### Post by aysiu on 2006-05-20
Try the bottom of this page:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

If that doesn't work, try the top of the page.

---

### Post by dhruv_1884 on 2006-05-21
Hi Aysiu,


Thanks it worked.

regards

dc

---

