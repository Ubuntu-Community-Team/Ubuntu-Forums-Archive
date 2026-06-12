---
title: "linux-backports-modules-2.6.24-17-386: dependency problems"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Myrgen on 2008-05-20
Hello all,

Since upgrading to Hardy Heron, I've had several problems.
Everytime I try to install an update for an app, I get the same messages:

E: linux-image-2.6.24-16-386: subprocess post-installation script returned error exit status 2
E: linux-backports-modules-2.6.24-16-386: dependency problems - leaving unconfigured
E: linux-image-2.6.24-17-386: subprocess post-installation script returned error exit status 2
E: linux-backports-modules-2.6.24-17-386: dependency problems - leaving unconfigured
E: linux-ubuntu-modules-2.6.24-16-386: dependency problems - leaving unconfigured
E: linux-ubuntu-modules-2.6.24-17-386: dependency problems - leaving unconfigured


Help?
Thank you in advance.

---

### Post by zvacet on 2008-05-20
```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

---

### Post by Myrgen on 2008-05-20
Thank you for your help, zvacet!

> **zvacet said:**
> ```
sudo dpkg --configure -a
```

Result of that code:

myriam@aurora:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.24-17-386 (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-386
/usr/bin/getopt: 1: Syntax error: ")" unexpected
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.24-17-386
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-17-386 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-386:
 linux-ubuntu-modules-2.6.24-17-386 depends on linux-image-2.6.24-17-386; however:
  Package linux-image-2.6.24-17-386 is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-386 (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.24-16-386 (2.6.24-16.30) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-16-386
/usr/bin/getopt: 1: Syntax error: ")" unexpected
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.24-16-386
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-16-386 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.24-17-386:
 linux-backports-modules-2.6.24-17-386 depends on linux-image-2.6.24-17-386; however:
  Package linux-image-2.6.24-17-386 is not configured yet.
dpkg: error processing linux-backports-modules-2.6.24-17-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.24-16-386:
 linux-backports-modules-2.6.24-16-386 depends on linux-image-2.6.24-16-386; however:
  Package linux-image-2.6.24-16-386 is not configured yet.
dpkg: error processing linux-backports-modules-2.6.24-16-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-16-386:
 linux-ubuntu-modules-2.6.24-16-386 depends on linux-image-2.6.24-16-386; however:
  Package linux-image-2.6.24-16-386 is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-16-386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-17-386
 linux-ubuntu-modules-2.6.24-17-386
 linux-image-2.6.24-16-386
 linux-backports-modules-2.6.24-17-386
 linux-backports-modules-2.6.24-16-386
 linux-ubuntu-modules-2.6.24-16-386
myriam@aurora:~$ 

> **zvacet said:**
> ```
sudo apt-get -f install
```

And result of this one:

myriam@aurora:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  samba-doc openbsd-inetd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.24-16-386 (2.6.24-16.30) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-16-386
/usr/bin/getopt: 1: Syntax error: ")" unexpected
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.24-16-386
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-16-386 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.24-16-386:
 linux-backports-modules-2.6.24-16-386 depends on linux-image-2.6.24-16-386; however:
  Package linux-image-2.6.24-16-386 is not configured yet.
dpkg: error processing linux-backports-modules-2.6.24-16-386 (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.24-17-386 (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-386
/usr/bin/getopt: 1: Syntax error: ")" unexpected
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.24-17-386
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-17-386 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.24-17-386:
 linux-backports-modules-2.6.24-17-386 depends on linux-image-2.6.24-17-386; however:
  Package linux-image-2.6.24-17-386 is not configured yet.
dpkg: error processing linux-backports-modules-2.6.24-17-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-16-386:
 linux-ubuntu-modules-2.6.24-16-386 depends on linux-image-2.6.24-16-386; however:
  Package linux-image-2.6.24-16-386 is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-16-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-386:
 linux-ubuntu-modules-2.6.24-17-386 depends on linux-image-2.6.24-17-386; however:
  Package linux-image-2.6.24-17-386 is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-16-386
 linux-backports-modules-2.6.24-16-386
 linux-image-2.6.24-17-386
 linux-backports-modules-2.6.24-17-386
 linux-ubuntu-modules-2.6.24-16-386
 linux-ubuntu-modules-2.6.24-17-386
E: Sub-process /usr/bin/dpkg returned an error code (1)
myriam@aurora:~$ 

What can I do? :)

---

