---
title: "dpkg and apt-get is broken"
date: 2018-09-15
forum: New to Ubuntu
---

### Post by louis3341 on 2018-09-15
Hello when i want to use apt-get install i get the error :
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 669 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up fontconfig (2.11.94-0ubuntu1) ...
dpkg: error processing package fontconfig (--configure):
 triggers ci file contains unknown directive 'libexpat'
Errors were encountered while processing:
 fontconfig
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When i use dpkg : dpkg --configure -a

```
Setting up fontconfig (2.11.94-0ubuntu1) ...
dpkg: error processing package fontconfig (--configure):
 triggers ci file contains unknown directive 'libexpat'
Errors were encountered while processing:
 fontconfig


```

And with apt-get install fontconfig :
```
The following packages will be upgraded:
  fontconfig
1 upgraded, 0 newly installed, 0 to remove and 668 not upgraded.
1 not fully installed or removed.
Need to get 0 B/178 kB of archives.
After this operation, 1.024 B of additional disk space will be used.
dpkg: warning: files list file for package 'fonts-lklug-sinhala' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-guru-extra' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-guru' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-liberation' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-khmeros-core' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libeot0:amd64' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

---

### Post by #&amp;thj^% on 2018-09-15
Give this a try:
```
sudo apt-get install --reinstall --purge fontconfig-config
```

---

### Post by louis3341 on 2018-09-15
```
The following additional packages will be installed:
  libfontconfig1
The following packages will be upgraded:
  fontconfig-config libfontconfig1
2 upgraded, 0 newly installed, 0 to remove and 667 not upgraded.
1 not fully installed or removed.
Need to get 0 B/181 kB of archives.
After this operation, 2.048 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: warning: files list file for package 'fonts-lklug-sinhala' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-guru-extra' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-guru' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-liberation' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-khmeros-core' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libeot0:amd64' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

apt-get is not working either

---

### Post by #&amp;thj^% on 2018-09-15
Basically, this error means something got corrupted on your filesystem. It's a bad sign, and these list files are needed for the package manager to figure out what is and isn't safe to upgrade. 
```
dpkg: warning: files list file for package 'fonts-lklug-sinhala' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-guru-extra' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-guru' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-liberation' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-khmeros-core' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
```
I hate to hit and run but work calls and I have to go now, but I'll check back to see if you got this sorted.

---

