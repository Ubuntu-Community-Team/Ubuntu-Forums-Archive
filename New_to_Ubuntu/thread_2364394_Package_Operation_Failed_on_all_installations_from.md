---
title: "Package Operation Failed on all installations from software centre"
date: 2017-06-22
forum: New to Ubuntu
---

### Post by oscar.nowell on 2017-06-22
Running a fresh install of Ubuntu 14.04 and can't install any software through the software centre.  Each try gets to 70% and returns "Package operation failed"

  ```
    installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
Selecting previously unselected package extlinux.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libemail-valid-perl': Input/output error
Error in function: 

```  sudo apt-get install -f returns
  ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libntdb1 linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic
  linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic python-ntdb
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```  Any help would be appreciated! (New user to Ubuntu)
  Looked through other questions solved with similar problems but the  answers seem unique and I don't want to go messing around with things  I'm unsure about.

---

### Post by Frogs Hair on 2017-06-22
Hello and Welcome 

Run the software updater if you haven't already before trying install any software. Before you get too much time invested you might want to install 16.04 which has 5 year support from release date also.

---

### Post by oscar.nowell on 2017-06-23
Hi there,

Thanks for the reply, I'll look at installing 16.04 and see if that resolves any issues!

---

### Post by ian-weisser on 2017-06-23
An input/output error can be very bad news.
Run a SMART check on your hard drive to rule out dying hardware.

---

