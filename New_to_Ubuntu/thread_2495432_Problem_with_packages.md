---
title: "Problem with packages"
date: 2024-02-19
forum: New to Ubuntu
---

### Post by Diablero on 2024-02-19
Hi all! I needed the "opentrack" program and had to assemble it myself.
Installed the build packages:
```
diablero@diableropc:~$ sudo apt  install build-essential cmake git qttools5-dev qtbase5-private-dev  libprocps-dev libopencv-dev
```

But there was a problem installing these packages:
```
Errors occurred while processing the following packages:
   /tmp/apt-dpkg-install-Ap4RJQ/060-libodbc2_2.3.9-5_amd64.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Then I was asked to fix the package:
```
You can run "apt --fix-broken install" to fix these errors. 
The  following packages have unmet dependencies:   libgdal30 : Depends:  libodbc2 (>= 2.3.1) but it will not be installed E: Unmet  dependencies. Try "apt --fix-broken install" without specifying the  package name (or specifying the solution). 
diablero@diableropc:~$  sudo apt --fix-broken install Reading package lists... Done Building a  dependency tree... Done Reading status information... Done Fixing  dependencies... 
Done The following additional packages will be installed:    libodbc2 Offered packages:    odbc-postgresql tdsodbc 
The  following NEW packages will be installed:    libodbc2 0 packages were  updated, 1 new packages were installed, 0 packages were marked for  removal, and 0 packages were not updated. 163 packages were not fully  installed or uninstalled. 
You need to download 0 B/159 kB archives.  After this operation, the amount of occupied disk space will increase by  471 kB. 
Do you want to continue? [Y/n] y (Reading the  database...there are currently 346646 files and directories installed.)  Preparing for unpacking .../libodbc2_2.3.9-5_amd64.deb ... Unpacks  libodbc2:amd64 (2.3.9-5) ... 
dpkg: error processing archive  /var/cache/apt/archives/libodbc2_2.3.9-5_amd64.deb (--unpack):   trying  to overwrite "/usr/lib/x86_64-linux-gnu/libodbc.so.2.0.0" which is  already in package libodbc1:amd64 2.3.11-1 
dpkg-deb: error: insert  subprocess killed by signal (Channel break) Errors occurred while  processing the following packages:    /var/cache/apt/archives/libodbc2_2.3.9-5_amd64.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How to fix it? Why does he want to install the version below?

There are also two packages offered: odbc-postgresql and tdsodbc
Maybe it's because of them? Why are they needed? Does the system prompt me to install or update them? How can I find out what these packages are for, for what programs?

---

### Post by Diablero on 2024-02-19
I tried to remove these packages, but they are not there!
```
diablero@diableropc:~$ sudo dpkg --purge odbc-postgresql tdsodbc libodbc2 
dpkg: warning: request to remove uninstalled package odbc-postgresql ignored 
dpkg: warning: request to remove uninstalled package tdsodbc ignored 
dpkg: warning: request to remove uninstalled package libodbc2:amd64 ignored
```

I don't know what to do, I'm confused) How could it break like that?)

---

### Post by Diablero on 2024-02-19
Problem solved! I looked at libodbc2 package dependencies:
```
diablero@diableropc:~$ apt-cache --installed rdepends libodbc2
libodbc2
Reverse Depends:
  libodbc1
 |wine-staging-amd64
 |wine-staging-amd64
 |wine-staging-amd64
 |wine-staging-amd64
 |wine-staging-amd64
 |wine-staging-amd64
 |wine-staging-amd64
 |wine-staging-amd64
 |wine-staging-amd64
 |wine-staging-amd64
 |wine-staging-amd64
 |wine-staging-amd64
  libgdal30
```
I decided to try to remove and reinstall libgdal30 using aptutude:
```
sudo aptitude purge libodbc2 && sudo aptitude update && sudo aptitude install libodbc2
```
Errors occurred while processing the following packages:
```
libgdal30
 libopencv-imgcodecs4.5d:amd64
 libopencv4.5d-jni
 libopencv-videoio4.5d:amd64
 libopencv4.5-java
 libopencv-imgcodecs-dev:amd64
 libopencv-contrib4.5d:amd64
 libopencv-superres4.5d:amd64
 libopencv-dev
 libopencv-highgui4.5d:amd64
 libopencv-highgui-dev:amd64
 libopencv-features2d-dev:amd64
 libopencv-videoio-dev:amd64
 libopencv-calib3d-dev:amd64
 libopencv-stitching-dev:amd64
 libopencv-objdetect-dev:amd64
 libopencv-contrib-dev:amd64
 libopencv-videostab4.5d:amd64
 libopencv-superres-dev:amd64
 libopencv-videostab-dev:amd64
```

I see the package again: libgdal30
Other development packages
And then manually, one package at a time, I deleted them all

Then update and upgrade, then autoremove unnecessary garbage and then upgrade.

Thank you for your attention, I hope this will be useful to someone!

---

