---
title: "Finding out program versions in a release"
date: 2008-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Vesa Paatero on 2008-05-20
Hi,

You may sometimes wonder if the newest Ubuntu release contains a certain version of an application, like "Hmm, my present Ubuntu has OpenOffice 2.2. I wonder if Hardy has the new 2.4 already?"

The best way that I found is to go to ftp.ubuntu.com and navigate through the directory structure to the distro and main/universe/multiverse section and the platform-specific binary directory, e.g.:

[ftp://ftp.ubuntu.com/ubuntu/dists/hardy/main/binary-amd64](ftp://ftp.ubuntu.com/ubuntu/dists/hardy/main/binary-amd64)

There, a file called Packages.gz or something similar tells you which packages belong to the distro, along with information about version. Unpack the file (e.g. "gzip -d Packages.gz"), open it and search for the package of interest. The words "Package: openoffice" seem would be good for the OpenOffice example.

If you know better method for this, please let me know.

Vesa

---

### Post by Tiftof on 2008-05-21
just search on this site: [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by FerN(SA) on 2008-05-21
Most of the times you could just type

openoffice --version

in your terminal

---

### Post by Tiftof on 2008-05-21
> **FerN(SA) said:**
> Most of the times you could just type

openoffice --version

in your terminal

That will give you the version of the current installed openoffice. He wants to know how to figure out the version of a package in a future ubuntu release.

---

