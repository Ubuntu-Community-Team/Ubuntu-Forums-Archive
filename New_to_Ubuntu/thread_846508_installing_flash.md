---
title: "installing flash"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by nashphyl on 2008-07-01
Hi i am trying to install flash on my ubuntu 7.1 Gutsy Gibbon, but when I follow the pop up install instructions, it downloads all 81 files and then says that it could not install and that I need to run "dpkg --configure -a". I do that and then ubuntu tells me that "superuser" privilege is required. Anyone know how to do this?

---

### Post by lazyart on 2008-07-01
sudo dpkg --configure -a

---

### Post by wolfen69 on 2008-07-01
```
sudo dpkg --configure -a
```

---

### Post by nashphyl on 2008-07-01
This is what I got

phyl@phyl-laptop:~$ sudo dpkg --configure -a
[sudo] password for phyl:
dpkg: error processing libaudio2 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up kdelibs-data (4:3.5.8-0ubuntu3.4) ...

Setting up libartsc0 (1.5.8-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libaudio2

---

### Post by unutbu on 2008-07-01
Try
```
sudo dpkg --remove --force-remove-reinstreq libaudio2
```
From the dpkg man page:

> --force-remove-reinstreq means: Remove a package, even if it&#8217;s broken and marked
              to require reinstallation. This may, for example, cause  parts  of
              the  package to remain on the system, which will then be forgotten
              by dpkg.


Then try reinstalling libaudio2.

The warning about parts of the package remaining on the system is no worry because you will be reinstalling the package anyway.

---

### Post by nashphyl on 2008-07-01
Actually that error message didnt really affect the flash download. Thanks a lot guys. You helped a ton

---

