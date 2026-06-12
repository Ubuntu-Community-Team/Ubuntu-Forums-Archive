---
title: "Unknown Problem"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by Balmung4500 on 2012-12-12
balmung@Evermore-PC:~$ sudo apt-get install gimp
[sudo] password for balmung: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gimp : Depends: libgimp2.0 (>= 2.6.12) but it is not going to be installed
        Depends: libgimp2.0 (<= 2.6.12-z) but it is not going to be installed
        Depends: gimp-data (>= 2.6.12) but it is not going to be installed
        Depends: gimp-data (<= 2.6.12-z) but it is not going to be installed
        Depends: libbabl-0.0-0 but it is not going to be installed
        Depends: libgegl-0.0-0 (>= 0.0.22) but it is not going to be installed
        Depends: libwebkitgtk-1.0-0 (>= 1.3.10) but it is not going to be installed
 libavcodec53 : Depends: libavutil51 (< 4:0.8.3-99) but 4:0.8.4-0ubuntu0.12.04.1 is to be installed or
                         libavutil-extra-51 (< 4:0.8.3.99) but it is not going to be installed
 libavformat53 : Depends: libavcodec53 (>= 4:0.8.4-0ubuntu0.12.04.1) but 4:0.8.3-0ubuntu0.12.04.1 is to be installed or
                          libavcodec-extra-53 (>= 4:0.8.4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
balmung@Evermore-PC:~$ sudo apt-get -f install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gimp : Depends: libgimp2.0 (>= 2.6.12) but it is not going to be installed
        Depends: libgimp2.0 (<= 2.6.12-z) but it is not going to be installed
        Depends: gimp-data (>= 2.6.12) but it is not going to be installed
        Depends: gimp-data (<= 2.6.12-z) but it is not going to be installed
        Depends: libbabl-0.0-0 but it is not going to be installed
        Depends: libgegl-0.0-0 (>= 0.0.22) but it is not going to be installed
        Depends: libwebkitgtk-1.0-0 (>= 1.3.10) but it is not going to be installed
 libavcodec53 : Depends: libavutil51 (< 4:0.8.3-99) but 4:0.8.4-0ubuntu0.12.04.1 is to be installed or
                         libavutil-extra-51 (< 4:0.8.3.99) but it is not going to be installed
 libavformat53 : Depends: libavcodec53 (>= 4:0.8.4-0ubuntu0.12.04.1) but 4:0.8.3-0ubuntu0.12.04.1 is to be installed or
                          libavcodec-extra-53 (>= 4:0.8.4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
balmung@Evermore-PC:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libavcodec53
The following packages will be upgraded:
  libavcodec53
1 upgraded, 0 newly installed, 0 to remove and 273 not upgraded.
1 not fully installed or removed.
Need to get 0 B/5,796 kB of archives.
After this operation, 9,216 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 232950 files and directories currently installed.)
Preparing to replace libavcodec53 4:0.8.3-0ubuntu0.12.04.1 (using .../libavcodec53_4%3a0.8.4-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libavcodec53 ...
dpkg: error processing /var/cache/apt/archives/libavcodec53_4%3a0.8.4-0ubuntu0.12.04.1_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libavcodec53_4%3a0.8.4-0ubuntu0.12.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jerome1232 on 2012-12-12
Sounds like the file is corrupted to me, I'd try removing it and re-attempting installation.

```
sudo rm /var/cache/apt/archives/libavcodec53_4%3a0.8.4-0ubuntu0.12.04.1_i386.deb
sudo apt-get update
sudo apt-get -f install
```

---

### Post by Balmung4500 on 2012-12-12
that seems to have worked

---

### Post by vasilisc on 2012-12-12
I recommend.
```

sudo apt-get autoremove
sudo apt-get autoclean
sudo rm -f /var/cache/apt/archives/*
sudo apt-get update && sudo apt-get upgrade
sudo apt-get -f install gimp

```

---

