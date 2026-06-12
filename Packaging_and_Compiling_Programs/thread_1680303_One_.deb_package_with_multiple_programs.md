---
title: "One .deb package with multiple programs"
date: 2011-02-02
forum: Packaging and Compiling Programs
---

### Post by shakading on 2011-02-02
Hi, I  want to create one debian package from multiple tarballs. For example I  want the programs: nmap and traceroute in one .deb package. How do you  do this? I am a beginner in this matter. I can only compile one package for one tarball.

Is this the right approach?

```
apt-get sources nmap
apt-get sources traceroute
tar -xzvf nmap_5.21.orig.tar.gz
 tar -xzvf traceroute_x.xx.orig.tar.gz
dh_make -e <email>
Type of package: single binary, multiple binary, library, kernel module or cdbs?
[s/m/l/k/b] s
Debuild

```

---

