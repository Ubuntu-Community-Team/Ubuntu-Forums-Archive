---
title: "I can not install banshee 1.0"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by legolas_w on 2008-06-13
Hi
I download the banshee deb file and then I tried to install it, but I get the following error, is there any command which could resolve dependencies automatically instead of asking the user to resolve dependency problems?

```

legolas@lego:~$ sudo dpkg -i banshee_1.0.0-0~getdeb1_i386.deb 
[sudo] password for legolas: 
Selecting previously deselected package banshee.
(Reading database ... 190152 files and directories currently installed.)
Unpacking banshee (from banshee_1.0.0-0~getdeb1_i386.deb) ...
dpkg: dependency problems prevent configuration of banshee:
 banshee depends on libmono-zeroconf1.0-cil (>= 0.7.3); however:
  Package libmono-zeroconf1.0-cil is not installed.
 banshee depends on libtaglib2.0-cil (>= 2.0.3.0); however:
  Package libtaglib2.0-cil is not installed.
dpkg: error processing banshee (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 banshee


```

Thanks

---

### Post by Sef on 2008-06-13
Have you tried this from the Terminal (Applications > Accessories > Terminal):

either type or copy and paste this command:

```
sudo apt-get update && sudo apt-get install libmono-zeroconf1.0-cil
```

---

### Post by kpkeerthi on 2008-06-13
Install it from Banshee PPA repository. 
[https://edge.launchpad.net/%7Ebanshee-team/+archive](https://edge.launchpad.net/%7Ebanshee-team/+archive)

---

