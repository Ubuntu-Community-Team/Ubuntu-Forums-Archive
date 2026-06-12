---
title: "How do I update my kernel?"
date: 2014-08-07
forum: New to Ubuntu
---

### Post by Yaten13 on 2014-08-07
Hello,

I'm running xubuntu (Ubuntu 14.04.1 LTS).

I just updated:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install update-manager-core
sudo do-release-upgrade

and I can't get virtualbox to work. What it has seemed to come down to is that I can't download headers for the kernel I am using: 3.8.0-21-generic

because it seems to be a pretty old kernel. I have tried to update it using apt-get, eg to 3.13.0-xx but it just freezes when I try to log into a session using the new kernel and I have to revert back to the 3.8.0

Am I missing something here? Shouldn't the update have moved me to a more recent kernel? Is there a way to update this?

---

### Post by grahammechanical on 2014-08-07
Please run these two commands

```
uname -a
lsb_release -a
```

I am confused. If you are running Xubuntu 14.04.1 then you should be using kernel 3.13. Or something close to it but not kernel 3.8. Did you upgrade from Xubuntu 13.04 or 13.10? That would explain why you have kernel 3.8 but why use it?

I am not sure that an upgrade to a newer version of Ubuntu/Xubuntu would include upgrade the version of virtualbox. Perhaps you need to uninstall virtualbox and reinstall it in order to get a version more suited to Xubuntu 14.04.1

Regards.

Regards.

---

### Post by Yaten13 on 2014-08-07
uname -a
Linux brian-Precision-T1600 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


Before the upgrade, virtualbox worked fine. I've tried uninstalling and reinstalling it, and it seems that the problem is that I have a newer version of virtualbox, but I can't find linux headers for the kernel.

Also, yes, I would have upgraded from an older version of Xubuntu. But I don't know why I am using the older one. That's my question too.

---

### Post by ajgreeny on 2014-08-07
Do you have any of the 3.13 kernels installed?  I am amazed if you don't, as that should have come with the rest of the upgrade from earlier distro so you should automatically boot to the 3.13 version.

Can you please run ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-85
```which will show all the kernels on your system.

---

### Post by Yaten13 on 2014-08-07
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-85

menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --cl
    menuentry 'Ubuntu, with Linux 3.13.0-27-lowlatency' --class ubuntu --class gnu-linux
    menuentry 'Ubuntu, with Linux 3.13.0-27-lowlatency (recovery mode)' --class ubuntu -
    menuentry 'Ubuntu, with Linux 3.13.0-27-generic' --class ubuntu --class gnu-linux --
    menuentry 'Ubuntu, with Linux 3.13.0-27-generic (recovery mode)' --class ubuntu --cl
    menuentry 'Ubuntu, with Linux 3.8.0-21-generic' --class ubuntu --class gnu-linux --c
    menuentry 'Ubuntu, with Linux 3.8.0-21-generic (recovery mode)' --class ubuntu --cla
menuentry 'Memory test (memtest86+)' {
menuentry 'Memory test (memtest86+, serial console 115200)' {
menuentry 'Windows 7 (loader) (on /dev/sdb2)' --class windows --class os $menuentry_i

The 3.13.0-32 and 3.13.0-21 are the ones I referenced in the initial post. I tried installing them via apt-get, but if I load into them from grub, the system hangs. The only thing that works now is loading into 3.8.0-21 from grub.

---

### Post by kansasnoob on 2014-08-07
Just out of curiosity post the output of:

```
sudo apt-get -f install
```

---

### Post by Yaten13 on 2014-08-08
sudo apt-get -f install

no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libav-tools libavdevice53 libavfilter3 libavresample1 libpostproc52 libuser1
  python-libuser
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by uRock on 2014-08-08
Did you all the VBox repository listed on their site or install the version offered by Ubuntu Software Center?

---

### Post by Yaten13 on 2014-08-08
I used the version in the software center (via apt-get).

---

### Post by ajgreeny on 2014-08-09
You may do better with the version of VB from Oracle, and the best way to do that is by following the **Debian-based Linux distributions** instructions at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads). 

Use the single line command shown and that will mean that VB will update automatically.

---

### Post by Yaten13 on 2014-09-03
Just a quick update on this just in case anyone has the same problems -  I was upgrading the kernel directly and it wasn't working well. I am using ubuntu LTS, and should have installed the LTS versions.

I installed package: linux-generic-lts-trusty - Generic Linux kernel image and headers
which installed the same Ubuntu, with Linux 3.13.0-35-generic' that wasn't behaving before and now everything is peachy. Thanks to the people who helped.

---

