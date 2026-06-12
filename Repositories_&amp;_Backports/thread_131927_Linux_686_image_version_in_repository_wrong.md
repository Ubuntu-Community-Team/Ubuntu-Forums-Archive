---
title: "Linux 686 image version in repository wrong"
date: 2006-02-17
forum: Repositories &amp; Backports
---

### Post by hboshoff on 2006-02-17
I am trying to install the Linux 686 image. Both Synaptic and apt-get give me an error:

```
hendrik@edubuntu:~$ sudo apt-get install linux-image-686
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-image-2.6.12-10-686
Suggested packages:
  lilo linux-doc-2.6.12 linux-source-2.6.12
The following NEW packages will be installed:
  linux-image-2.6.12-10-686 linux-image-686
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 19.5MB/19.5MB of archives.
After unpacking 56.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main linux-image-2.6.12-10-686 2.6.12-10.26
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-10-686_2.6.12-10.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-10-686_2.6.12-10.26_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Looking directly at the repository website, it seems the version of the file is 2.6.12-10.28 instead of the 2.6.12-10.26 searched for.

Who can correct this?

Hendrik

---

### Post by kudu on 2006-02-17
I can install it but I can't get it to work with the synaptic nvidia-glx driver. I was running it just fine but had to do a reinstall to clean house. Now the 386 kernel works perfectly but the 686 one chokes. So I'm having to use 386 and like it.

---

