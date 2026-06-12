---
title: "Update Manager Issue - Ubuntu 8.04"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Paul Vega on 2008-07-25
Kia Ora

On attempting to run Update Manager of late I get the following error message - 

[COLOR="Red"]"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."[/COLOR]
 
As well it lists the files that are a problem -
 
[COLOR="Red"]"Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead."[/COLOR]

Can someone aid me in resolving this issue?

Paul Vega

---

### Post by bapoumba on 2008-07-25
I could download the file. May be try again or use another repository (you can choose another one in synaptic).

---

### Post by philgenius on 2008-08-25
However, in Hardy Heron on a Thinkpad T60, I get this error, no matter what.

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.gz](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


What's the problem here?

---

### Post by bapoumba on 2008-08-25
> **philgenius said:**
> However, in Hardy Heron on a Thinkpad T60, I get this error, no matter what.

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.gz](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


What's the problem here?
I cannot get that particular repo (I also get a 404). The address may be wrong, or the repo down. You can remove it from your sources.list file (or directly from Synaptic) and the error will go away.
What did you use it for? (There may be a replacement).

---

