---
title: "Error Meesage Running apt-get"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by cmorra68 on 2008-05-08
I am a noob so I have been tinkering with Ubuntu.  I am not sure what happened but when I try and run any apt-get command, especially update, I get the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Anyone know what this error is and how to correct it?

Thanks in advance!!

Update!!!

When I try and run Add/Remove Applications or Update Manager, I get the following messages:

Could not download all repository indexes
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/dapper/main/binary-i386/Packages.gz](http://kubuntu.org/packages/amarok-latest/dists/dapper/main/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Followed by:

An error occured

The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by freebeer on 2008-05-08
> **cmorra68 said:**
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


Open up a terminal windows and type (or copy and paste) the following:

```

sudo dpkg --configure -a

```

---

### Post by cmorra68 on 2008-05-08
I did that and this is the message I get:

Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24.3-cm1
Cannot find /lib/modules/2.6.24.3-cm1
update-initramfs: failed for /boot/initrd.img-2.6.24.3-cm1
dpkg: subprocess post-installation script returned error exit status 1

---

### Post by Sef on 2008-05-08
> Open up a terminal windows and type (or copy and paste) the following:

Code:

sudo dpkg --configure -a



That code is **not** correct.  Sudo is for Gnome.  The OP is running Kubuntu. 

> Failed to fetch [http://kubuntu.org/packages/amarok-l...86/Packages.gz](http://kubuntu.org/packages/amarok-l...86/Packages.gz) 404 Not Found

The correct code would be

```
kdesu dpkg --configure -a
```

---

### Post by cmorra68 on 2008-05-08
I am running Gnome, not KDE.

This all started when I was trying to install Amarok (if that helps).

I am running Ubuntu 8.04 (hardy)

Kernel Linux 2.6.24-16-generic

GNOME 2.22.1

---

### Post by cmorra68 on 2008-05-08
Please help!!!

I cannot run Synpatics either. Same error.

---

### Post by inportb on 2008-05-08
> **Sef said:**
> That code is **not** correct.  Sudo is for Gnome.  The OP is running Kubuntu. 



The correct code would be

```
kdesu dpkg --configure -a
```

Um, I'm not sure I follow you. kdesu is the KDE counterpart of gksu, for graphical applications. sudo should be pretty universal since it's text-based.

---

