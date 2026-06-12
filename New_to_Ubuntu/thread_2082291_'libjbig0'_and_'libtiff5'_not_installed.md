---
title: "'libjbig0' and 'libtiff5' not installed"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by zeemanCharmz on 2012-11-09
Hallo Internet!!.. I just upgraded from 12.04 to 12.10. During the installation part, it told me that packages 'libjbig0' and 'libtiff5' could not be installed or something like that.. I no longer remember the exact word.. but could that affect my system performance.. and if so, how can I rectify that??..

---

### Post by Popenuj on 2012-11-09
It will not negatively effect your system performance. They provide compression and decompression functions. If you are concerned about it open a terminal window and type: 
```
sudo apt-get -f install
```to remove packages obsoleted type in terminal:
```
sudo apt-get autoremove
```

---

### Post by zeemanCharmz on 2012-11-09
[attach] Working... this may take a while.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  compiz-plugins compiz-plugins-main fastjar gcc-4.6-base:i386 gcj-4.6-base
  gcj-4.7-base gcj-4.7-jre-lib gir1.2-folks-0.6 gir1.2-gee-1.0
  gir1.2-panelapplet-4.0 gnome-applets-data gvfs-libs:i386 junit4
  libapt-inst1.4 libasm3-java libattica0.3 libbonoboui2-0 libbonoboui2-common
  libboost-program-options1.46.1 libcdt4 libcmis-0.2-0 libcommons-codec-java
  libdb5.1-java libdb5.1-java-jni libdbus-glib-1-2:i386 libecj-java
  libexiv2-11 libgcj-bc libgcj-common libgcj12 libgcj13 libgdata1.9-cil
  libgdu0:i386 libglew1.6 libglewmx1.6 libgnome-keyring0:i386 libgnomeui-0
  libgnomeui-common libgraph4 libgudev-1.0-0:i386 libgvc5 libhamcrest-java
  libkdecorations4 libkexiv2-10 libkipi8 libktorrent3 libkwineffects1abi3
  libkwinglutils1 libkworkspace4abi1 liblastfm0 libllvm3.0:i386 libmagickcore4
  libmagickcore4-extra libmagickwand4 libmusicbrainz3-6
  libnepomukdatamanagement4 libnux-2.0-0 libnux-2.0-common libpathplan4
  libpoppler-qt4-3 libpoppler19 librhythmbox-core5 libtiff4:i386
  libudisks2-0:i386 libx264-120 linux-headers-3.2.0-32
  linux-headers-3.2.0-32-generic packagekit-backend-aptcc python-central
  python-gmenu python-packagekit unity-2d-common update-manager-kde
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libjbig0:i386 libtiff5:i386
The following NEW packages will be installed:
  libjbig0:i386 libtiff5:i386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/198 kB of archives.
After this operation, 674 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package libjbig0:i386.
(Reading database ... 233245 files and directories currently installed.)
Unpacking libjbig0:i386 (from .../libjbig0_2.0-2ubuntu1_i386.deb) ...
Selecting previously unselected package libtiff5:i386.
Unpacking libtiff5:i386 (from .../libtiff5_4.0.2-1ubuntu2_i386.deb) ...
Setting up libjbig0:i386 (2.0-2ubuntu1) ...
Setting up libtiff5:i386 (4.0.2-1ubuntu2) ...
Setting up libsane:i386 (1.0.23-0ubuntu1) ...
Setting up libtiff4:i386 (3.9.6-9ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place[/attach] 	

Thanx man!!..
This is what I got after running the first command. So we are good2go right?

---

### Post by Popenuj on 2012-11-09
Yep!

---

### Post by zeemanCharmz on 2012-11-09
I just finished removing obsoleted packages.. I had no I idea they were that many.. thanks Popenuj

---

