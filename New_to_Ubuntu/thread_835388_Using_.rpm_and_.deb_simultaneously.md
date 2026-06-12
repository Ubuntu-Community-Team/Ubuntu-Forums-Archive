---
title: "Using .rpm and .deb simultaneously"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by john.hall on 2008-06-20
If I download an rpm and use rpm -i <pkg>, will apt know that I have installed the rpm?

Is the reverse also true?  If I install rpm, will it know what packages I already have on my system due to apt-get install?

Or is there a way to make dpkg understand .rpm files?

---

### Post by skymera on 2008-06-20
RPM can't be used on Ubuntu.

That is a RedHat file. 

what are you trying to install?

---

### Post by the_doc on 2008-06-20
You can convert to .deb using alien.

---

### Post by Cypher on 2008-06-20
You can't use RPM's natively, you'll have to use Alien to convert them to DEBs to be installed in Ubuntu.

---

### Post by john.hall on 2008-06-20
OK.  I got it.

Thanks!

---

### Post by drs305 on 2008-06-20
To simplify installation and tracking, convert rpm's to deb files with 'alien'.

Install alien:
```
sudo aptitude install alien
```

Convert rpm to deb:
```
sudo alien -k /path-to-rpm-file/rpmfile

```

Install deb:
```
sudo dpkg -i fullappname.deb

```

---

### Post by harlan on 2008-06-20
To install a rpm package:
1.Install alien:
   $sudo aptitude install alien
2.Install de rpm:
   $sudo alien -i package.rpm

Somebody was faster than me

---

### Post by Oldsoldier2003 on 2008-06-20
Although you can use alien, it should really be considered as a last resort. If you can't find the deb in the Ubuntu repos or in a source such as getdeb you can usually compile the program yourself.

---

### Post by Jonte_J on 2008-06-22
What if I want to uninstall an rpm package? How is that done?

/jonas

---

### Post by drs305 on 2008-06-22
> **Jonte_J said:**
> What if I want to uninstall an rpm package? How is that done?

/jonas

In other linux distributions, they are removed with "*rpm -e appname*".

In ubuntu, if you converted the rpm into a deb package with *alien* and then installed it normally (double click, gdebi, etc), it is registered and can be removed via the normal uninstall methods (synaptic, apt-get remove, aptitude remove/purge, dpkg etc).

---

### Post by Paqman on 2008-06-22
> **Oldsoldier2003 said:**
> Although you can use alien, it should really be considered as a last resort. If you can't find the deb in the Ubuntu repos or in a source such as getdeb you can usually compile the program yourself.

Actually, i'd recommend using a deb made from an rpm over compiling. At least it'd be uninstallable, and won't break the dependency system like compiling will.

I'd definitely say compiling is the absolute last resort.

---

