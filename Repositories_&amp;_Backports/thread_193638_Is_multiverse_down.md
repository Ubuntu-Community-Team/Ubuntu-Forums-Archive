---
title: "Is multiverse down?"
date: 2006-06-10
forum: Repositories &amp; Backports
---

### Post by rpesq on 2006-06-10
When I try to Reload in Synaptic, most update fine but I get this error message:

> Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

I am not having network problems....  Any thoughts?

---

### Post by maxbaggi on 2006-06-10
I've been getting the same error.  I guess they are updating the multiverse repository

---

### Post by David_T on 2006-06-13
I was getting the same error when updating multiverse from
ca.archive.ubuntu.com.  No problems with archive.ubuntu.com though.
Here's what I got:

$ sudo apt-get update
.....[ this is where it successfully updates from other repositories, then..]...
Get: 5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/multiverse Packages [121kB]
99% [5 Packages gzip 0]
gzip: stdin: not in gzip format
Errhttp://ca.archive.ubuntu.com dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Fetched 5B in 5s (1B/s)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


-david

---

