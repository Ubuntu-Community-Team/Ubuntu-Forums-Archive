---
title: "wine-compholio dependecy issue"
date: 2015-02-05
forum: New to Ubuntu
---

### Post by kevin145 on 2015-02-05
Was successfully using pipelight then would get unmet dependency errors 3 times at startup.  was never able to fix with apt-get.  recently used apt-get to succesfully get it to stop working altogether.  sudo apt-get install wine-compholio-i386 broke the whole thing.  

kevin@tech-no-logic-kill:~$ sudo apt-get check
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 wine-compholio : Depends: wine-compholio-i386 (= 1.7.32~ubuntu14.04.1) but it is not installable
E: Unmet dependencies. Try using -f.
kevin@tech-no-logic-kill:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  wine-compholio-amd64
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  wine-compholio
The following packages will be upgraded:
  wine-compholio
1 upgraded, 0 newly installed, 0 to remove and 158 not upgraded.
Need to get 0 B/1,214 B of archives.
After this operation, 10.8 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 239519 files and directories currently installed.)
Preparing to unpack .../wine-compholio_1.7.35~ubuntu14.04.1_amd64.deb ...
Unpacking wine-compholio (1.7.35~ubuntu14.04.1) over (1.7.32~ubuntu14.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/wine-compholio_1.7.35~ubuntu14.04.1_amd64.deb (--unpack):
 trying to overwrite '/opt/wine-compholio/bin/wine64-preloader', which is also in package wine-compholio-amd64 1.7.32~ubuntu14.04.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

anyone have any ideas?

---

### Post by sandyd on 2015-02-05
wine-compholio-amd64 seems to have conflicting files with wine-compholio


Try
```

apt-get remove wine-compholio-amd64
```

---

### Post by kevin145 on 2015-02-05
oh yeah i forgot to mention that I can't remove either of the conflicting packages.

kevin@tech-no-logic-kill:~$ sudo apt-get remove wine-compholio-amd64
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 wine-compholio : Depends: wine-compholio-amd64 (= 1.7.32~ubuntu14.04.1) but it is not going to be installed
                  Depends: wine-compholio-i386 (= 1.7.32~ubuntu14.04.1) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
kevin@tech-no-logic-kill:~$

---

### Post by mc4man on 2015-02-05
Can you confirm that this is the ppa you're using?
[https://launchpad.net/~ehoover/+archive/ubuntu/compholio](https://launchpad.net/~ehoover/+archive/ubuntu/compholio)

If so then both wine-compholio &  wine-compholio-amd64 are just dummy transitional packages now (& currently at 1.7.35 for 14.04 anyway

The new real packages are named wine-staging,  wine-staging-amd64, & wine-staging-i386

So for starters  try - 
```
sudo apt-get purge wine-compholio wine-compholio-amd64 
```

---

### Post by kevin145 on 2015-02-05
I cannot confirm that from memory.  Is there a way to check?  however it doesn't sound familiar.

kevin@tech-no-logic-kill:~$ sudo apt-get purge wine-compholio wine-compholio-amd64
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 pipelight-multi : Depends: wine-compholio (>= 1.7.19-1~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
kevin@tech-no-logic-kill:~$

---

### Post by mc4man on 2015-02-05
post the results of this - 

```
apt-cache-policy wine-compholio wine-compholio-amd64 pipelight-multi
```

&

```
apt-cache show wine-compholio wine-compholio-amd64 pipelight-multi
```

---

### Post by kevin145 on 2015-02-05
```
kevin@tech-no-logic-kill:~$ apt-cache policy wine-compholio wine-compholio-amd64 pipelight-multi
wine-compholio:
  Installed: 1.7.32~ubuntu14.04.1
  Candidate: 1.7.35~ubuntu14.04.1
  Version table:
     1.7.35~ubuntu14.04.1 0
        500 http://ppa.launchpad.net/pipelight/stable/ubuntu/ trusty/main amd64 Packages
 *** 1.7.32~ubuntu14.04.1 0
        100 /var/lib/dpkg/status
wine-compholio-amd64:
  Installed: 1.7.32~ubuntu14.04.1
  Candidate: 1.7.35~ubuntu14.04.1
  Version table:
     1.7.35~ubuntu14.04.1 0
        500 http://ppa.launchpad.net/pipelight/stable/ubuntu/ trusty/main amd64 Packages
 *** 1.7.32~ubuntu14.04.1 0
        100 /var/lib/dpkg/status
pipelight-multi:
  Installed: 0.2.8~ubuntu14.04.1
  Candidate: 0.2.8.1~ubuntu14.04.1
  Version table:
     0.2.8.1~ubuntu14.04.1 0
        500 http://ppa.launchpad.net/pipelight/stable/ubuntu/ trusty/main amd64 Packages
 *** 0.2.8~ubuntu14.04.1 0
        100 /var/lib/dpkg/status
```

```
kevin@tech-no-logic-kill:~$ apt-cache show wine-compholio wine-compholio-amd64 pipelight-multi
Package: wine-compholio
Source: wine-staging
Priority: extra
Section: oldlibs
Installed-Size: 33
Maintainer: Erich E. Hoover <erich.e.hoover@gmail.com>
Architecture: amd64
Version: 1.7.35~ubuntu14.04.1
Depends: wine-staging
Filename: pool/main/w/wine-staging/wine-compholio_1.7.35~ubuntu14.04.1_amd64.deb
Size: 1214
MD5sum: a6dabd8bd2196c85ca8143bf1c0de580
SHA1: 0c03fcfe317f4a88d48f99a1e305f79bd28cf6fa
SHA256: bb38741852e4ccc8a5bdccb496006b6de9aeaedb65424f136f9cf3fc5168bb76
Description-en: Transitional dummy package
 This is a transitional dummy package. It can safely be removed.
Description-md5: 34b02e9ba6f083e5723243e13d1aa073
Original-Maintainer: Scott Ritchie <scottritchie@ubuntu.com>

Package: wine-compholio
Status: install ok installed
Priority: extra
Section: oldlibs
Installed-Size: 10556
Maintainer: Erich E. Hoover <erich.e.hoover@gmail.com>
Architecture: amd64
Multi-Arch: foreign
Version: 1.7.32~ubuntu14.04.1
Depends: libc6 (>= 2.17), wine-compholio-amd64 (= 1.7.32~ubuntu14.04.1), wine-compholio-i386 (= 1.7.32~ubuntu14.04.1)
Pre-Depends: dpkg (>= 1.14.12ubuntu3)
Description: The Compholio Edition is a special build of the popular Wine software
 with patches representing my current staging tree for Wine.
 .
 Microsoft Windows Compatibility Layer (Binary Emulator and Library)
 Wine is a compatibility layer for running Windows applications on Linux.
 Applications are run at full speed without the need of cpu emulation. Wine
 does not require Microsoft Windows, however it can use native system dll
 files in place of its own if they are available.
 .
 This package includes a program loader for running unmodified Windows executables
 as well as the Wine project's free version of the Windows API for running programs
 ported from Windows.
 .
 This package is based on a recent Wine beta.  While many more applications will
 work, there may be some loss of functionality compared with the stable release
 provided by the regular wine package.
Description-md5: ff63a5a0eaee885e26e5ac548cdb1341
Original-Maintainer: Scott Ritchie <scottritchie@ubuntu.com>

Package: wine-compholio-amd64
Source: wine-staging
Priority: extra
Section: oldlibs
Installed-Size: 21
Maintainer: Erich E. Hoover <erich.e.hoover@gmail.com>
Architecture: amd64
Version: 1.7.35~ubuntu14.04.1
Depends: wine-staging-amd64, wine-staging
Filename: pool/main/w/wine-staging/wine-compholio-amd64_1.7.35~ubuntu14.04.1_amd64.deb
Size: 836
MD5sum: 5fd0cfa3f37608ff77a59c8ecff56a24
SHA1: a1dad72e2bf81cb20fa3b4558058c1eedaa1359a
SHA256: 67148932fc835c17acc6615a26d512f43df43eacb4ae1e38d77c632fe885dde4
Description-en: Transitional dummy package
 This is a transitional dummy package. It can safely be removed.
Description-md5: 34b02e9ba6f083e5723243e13d1aa073
Original-Maintainer: Scott Ritchie <scottritchie@ubuntu.com>

Package: wine-compholio-amd64
Status: install ok installed
Priority: optional
Section: otherosfs
Installed-Size: 139972
Maintainer: Erich E. Hoover <erich.e.hoover@gmail.com>
Architecture: amd64
Multi-Arch: foreign
Source: wine-compholio
Version: 1.7.32~ubuntu14.04.1
Replaces: wine-compholio (<< 1.7.15-1~)
Depends: libasound2 (>= 1.0.16), libc6 (>= 2.17), libgcc1 (>= 1:4.1.1), libglu1-mesa | libglu1, libgphoto2-6 (>= 2.5.2), libgphoto2-port10 (>= 2.5.2), liblcms2-2 (>= 2.2+git20110628), libldap-2.4-2 (>= 2.4.7), libmpg123-0 (>= 1.6.2), libopenal1 (>= 1:1.13), libpulse0 (>= 1:0.99.1), libx11-6, libxext6, libxml2 (>= 2.9.0), zlib1g (>= 1:1.1.4), libasound2-plugins, libncurses5
Pre-Depends: dpkg (>= 1.14.12ubuntu3)
Recommends: libcapi20-3, libcups2, libdbus-1-3, libfontconfig1 | libfontconfig, libfreetype6, libgnutls26, libjpeg8, libosmesa6, libpcap0.8, libpng12-0, libsane, libssl1.0.0, libtiff5 | libtiff4, libtxc-dxtn-s2tc0, libv4l-0, libxcomposite1, libxcursor1, libxi6, libxinerama1, libxrandr2, libxrender1, libxslt1.1, libxt6, libxxf86vm1, libodbc1, libgsm1
Breaks: wine-compholio (<< 1.7.15-1~)
Description: The Compholio Edition is a special build of the popular Wine software
 with patches representing my current staging tree for Wine.
 .
 Microsoft Windows Compatibility Layer (Binary Emulator and Library)
 Wine is a compatibility layer for running Windows applications on Linux.
 Applications are run at full speed without the need of cpu emulation. Wine
 does not require Microsoft Windows, however it can use native system dll
 files in place of its own if they are available.
 .
 This package provides support for loading 64-bit x86 Windows applications
 .
 This package is based on a recent Wine beta.  While many more applications will
 work, there may be some loss of functionality compared with the stable release
 provided by the regular wine package.
Description-md5: a9aa98c0bba360d6d6ef471c365a5484
Original-Maintainer: Scott Ritchie <scottritchie@ubuntu.com>

Package: pipelight-multi
Priority: optional
Section: misc
Installed-Size: 3668
Maintainer: Michael Mueller <michael@fds-team.de>
Architecture: amd64
Version: 0.2.8.1~ubuntu14.04.1
Replaces: pipelight (<< 0.2.0~)
Depends: libc6 (>= 2.14), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.5), libx11-6, debconf (>= 0.5) | debconf-2.0, mesa-utils, ttf-mscorefonts-installer, wget, zenity | kde-baseapps-bin, zenity | qdbus, wine-staging, bash (>= 4.0), unzip, cabextract, gnupg
Conflicts: pipelight (<< 0.2.0~)
Filename: pool/main/p/pipelight-multi/pipelight-multi_0.2.8.1~ubuntu14.04.1_amd64.deb
Size: 584146
MD5sum: 9b280623ffb278073523d96fc6e173dc
SHA1: f2e258595cda8063352ee130d9eefbeb95721717
SHA256: d45c069497abdfe100be2f8986977dcd6ba900a2f78ad477fdb37f2749abb97a
Description-en: allows usage of Windows NPAPI plugins through Wine
 Pipelight allows one to use NPAPI plugins inside a Linux browser
 with the help of Wine.
Description-md5: 4a421486a8272f7063a95f5e0b4aac2d

Package: pipelight-multi
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 3668
Maintainer: Michael Mueller <michael@fds-team.de>
Architecture: amd64
Version: 0.2.8~ubuntu14.04.1
Replaces: pipelight (<< 0.2.0~)
Depends: libc6 (>= 2.14), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.5), libx11-6, debconf (>= 0.5) | debconf-2.0, mesa-utils, ttf-mscorefonts-installer, wget, zenity | kde-baseapps-bin, zenity | qdbus, wine-compholio (>= 1.7.19-1~), bash (>= 4.0), unzip, cabextract, gnupg
Conflicts: pipelight (<< 0.2.0~)
Description-en: allows usage of Windows NPAPI plugins through Wine
 Pipelight allows one to use NPAPI plugins inside a Linux browser
 with the help of Wine.
Description-md5: 4a421486a8272f7063a95f5e0b4aac2d
```

---

### Post by mc4man on 2015-02-05
Ok - so this is the ppa in use - 
[https://launchpad.net/~pipelight/+archive/ubuntu/stable](https://launchpad.net/~pipelight/+archive/ubuntu/stable)

A bit confusing because there are no wine-compholio packages in the ppa anymore 
(1.7.35~ubuntu14.04.1 is now named wine-staging

So try to remove the whole mess - 
```
sudo apt-get purge wine-compholio wine-compholio-amd64 pipelight-multi
```

If that works then you can explore re-installing pipelight if desired

---

### Post by kevin145 on 2015-02-05
I don't know how to change the title of this thread to indicate that it is solved, however this has solved the problem.  Thank you :)

---

