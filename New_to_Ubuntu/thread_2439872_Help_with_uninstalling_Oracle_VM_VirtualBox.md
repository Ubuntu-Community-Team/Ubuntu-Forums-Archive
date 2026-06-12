---
title: "Help with uninstalling Oracle VM VirtualBox"
date: 2020-04-02
forum: New to Ubuntu
---

### Post by joshua-newbould on 2020-04-02
I installed Oracle VM VirtualBox from its website using a .deb file and now I don't want it I cannot find a way to uninstall it. When I look in Ubuntu Software in the Installed tab, it is not there. I have tried "sudo apt-get remove virtualbox" and it just returns, "Package 'virtualbox' is not installed, so not removed." I've tried right clicking on it and going to "Show Details" put it just opens up Ubuntu Software and searches for virtualbox, which outputs no relevant results.

---

### Post by deadflowr on 2020-04-02
Typically virtualbox will install via a specific version name.
Try something like
```
dpkg -l | grep virtualbox
```
it should give you the proper package name, then run the apt remove command to remove it.

My own guess is if it is the latest then it's probably virtualbox-6.1.

---

### Post by SeijiSensei on 2020-04-02
VirtualBox images from the Oracle site have version numbers attached so they don't interfere with the version in the repositories which is called simply "virtualbox."  Try using "sudo apt remove virtualbox-6.1" which is the most recent release.

---

### Post by joshua-newbould on 2020-04-02
Yes, it is virtualbox-6.1. But it still didn't uninstall it! This is what the output was: (I have no idea what any of it means)

```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 207513 files and directories currently installed.)
Removing virtualbox-6.1 (6.1.4-136177~Ubuntu~bionic) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package virtualbox-6.1 (--remove):
 installed virtualbox-6.1 package pre-removal script subprocess returned error exit status 1
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why.


There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.  If your system is using EFI Secure Boot you may need to sign the
kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load
them. Please see your Linux system's documentation for more information.
Errors were encountered while processing:
 virtualbox-6.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by deadflowr on 2020-04-02
see: [https://ubuntuforums.org/showthread.php?t=2438639&p=13939264#post13939264]("https://ubuntuforums.org/showthread.php?t=2438639&p=13939264#post13939264")

---

