---
title: "DPKG installation problems HELP!"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by K8JWT on 2008-05-25
Trying to improve my system I was following a sticky located elsewhere on this forum and now I get this responce repeatedly and can't get anything else to install..

Unpacking acroread (from .../acroread_8.1.2-0medibuntu6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_8.1.2-0medibuntu6_i386.deb (--unpack):
trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
Selecting previously deselected package acroread-escript.
Unpacking acroread-escript (from .../acroread-escript_8.1.2-0medibuntu6_i386.deb) ...
Selecting previously deselected package acroread-plugins.
Unpacking acroread-plugins (from .../acroread-plugins_8.1.2-0medibuntu6_i386.deb) ...
Selecting previously deselected package mozilla-acroread.
Unpacking mozilla-acroread (from .../mozilla-acroread_8.1.2-0medibuntu6_i386.deb) ...
Errors were encountered while processing:
/var/cache/apt/archives/acroread_8.1.2-0medibuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

ANy suggestions????

---

### Post by wolfen69 on 2008-05-25
try
```
sudo apt-get -f install
```

---

### Post by ChameleonDave on 2008-05-25
> **K8JWT said:**
> 

ANy suggestions????

To be honest, I suggest getting rid of Adobe Acrobat Reader, and installing KPDF or Evince instead.

Edit: here is a rephrasing of the above, for the benefit of Captain Obvious.

"To be honest, I suggest not using Adobe Acrobat Reader (and uninstalling it if you have managed to install it), and using KPDF or Evince instead (installing them first in the event of them not currently being on your system for whatever reason).  You will automatically have KPDF if you have kubuntu-desktop installed, and you will automatically have Evince if you have gnome-desktop or xubuntu-desktop installed."

---

### Post by wolfen69 on 2008-05-25
> **ChameleonDave said:**
> To be honest, I suggest getting rid of Adobe Acrobat Reader, and installing KPDF or Evince instead.

evince is installed by default.

---

### Post by K8JWT on 2008-05-25
try
Code:

sudo apt-get -f install


I tried thia and I get the same responce as first shown in my initial posting...

---

### Post by iaculallad on 2008-05-25
> **K8JWT said:**
> try
Code:

sudo apt-get -f install


I tried thia and I get the same responce as first shown in my initial posting...


What about using the command:

**sudo dpkg --configure -a**

---

### Post by K8JWT on 2008-05-25
Here is what I got after trying my previous post.

k8jwt@k8jwt-desktop:~$ sudo apt-get -f install
[sudo] password for k8jwt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  acroread
The following NEW packages will be installed:
  acroread
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/29.5MB of archives.
After this operation, 73.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 100693 files and directories currently installed.)
Unpacking acroread (from .../acroread_8.1.2-0medibuntu6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_8.1.2-0medibuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_8.1.2-0medibuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ChameleonDave on 2008-05-25
> **K8JWT said:**
> Here is what I got after trying my previous post.

Unpacking acroread (from .../acroread_8.1.2-0medibuntu6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_8.1.2-0medibuntu6_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu

Well, that says it all.  You can't have the adobereader-enu and acroread packages installed at the same time.  Choose just one of them.  Or better still, use KPDF/Evince.  Was there any particular reason you wanted a bulky, proprietary version of KDFP/Evince?

---

