---
title: "Help! I Think I Killed My Ubuntu!!"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-13
hi guys,

i was trying to check something in synaptic package manager and i get this error when i click on it

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and when i try to update it in software sources i get this error
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

WHAT HAVE I DONE!!! O MY GOD!!!! HELP!!!!

---

### Post by Joeb454 on 2008-05-13
Open up a terminal and try running ```
sudo dpkg configure -a
``` and let us know if that fixes it

---

### Post by appoloin on 2008-05-13
I did that and this is what i got

edward@Vlad:~$ sudo dpkg configure -a
[sudo] password for edward:
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
edward@Vlad:~$

---

### Post by appoloin on 2008-05-13
I think i really screwed things up

i tried to do an update manager and i got this

correct the problem. 
E: _cache->open() failed, please report.

---

### Post by philinux on 2008-05-13
typo should be

sudo dpkg --configure -a

---

### Post by appoloin on 2008-05-13
i did that and i got this

edward@Vlad:~$ sudo dpkg configure -a
[sudo] password for edward:
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
edward@Vlad:~$ sudo dpkg --configure -a
Setting up acidlab (0.9.6b20-22) ...

and it seems stuck

---

### Post by olskar on 2008-05-13
> **appoloin said:**
> i did that and i got this

edward@Vlad:~$ sudo dpkg configure -a
[sudo] password for edward:
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
edward@Vlad:~$ sudo dpkg --configure -a
Setting up acidlab (0.9.6b20-22) ...

and it seems stuck Leave it alone for some time, its propably doing what it says; setting up acidlab

---

### Post by appoloin on 2008-05-13
Omg!!! I Love You All!!!!
I Love Ubuntu!!
I Love This Community!!!

---

### Post by philinux on 2008-05-13
Please use the correct command, the two - before configure are very important.

sudo dpkg --configure -a

copy and paste it.

---

