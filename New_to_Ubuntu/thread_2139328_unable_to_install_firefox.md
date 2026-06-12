---
title: "unable to install firefox"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by hudkmr on 2013-04-26
Hi,

I am trying to install firefox but getting the below error. Appreciate any help to solve the issue
```

The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 24.5 MB of archives.
After this operation, 51.3 MB of additional disk space will be used.
Get:1 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) quantal-updates/main firefox i386 20.0+build1-0ubuntu0.12.10.3 [24.5 MB]
Fetched 24.5 MB in 16s (1,486 kB/s)                                               
(Reading database ... 157993 files and directories currently installed.)
Unpacking firefox (from .../firefox_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_20.0+build1-0ubuntu0.12.10.3_i386.deb (--unpack):
 trying to overwrite '/usr/share/applications/firefox.desktop', which is also in package kubuntu-firefox-installer 12.04ubuntu1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_20.0+build1-0ubuntu0.12.10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks in advance
Regards
Hari

---

### Post by sandyd on 2013-04-26
try
```

sudo apt-get remove kubuntu-firefox-installer
sudo apt-get install firefox
```

---

### Post by hudkmr on 2013-04-26
Hi Sandy,

thanks for your help, i still couldnt get rid of the issue after following your instruction i get the following error

hari@hari-LifeBook-V1020:~$ sudo apt-get remove kubuntu-firefox-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 firefox-globalmenu : Depends: firefox (= 20.0+build1-0ubuntu0.12.10.3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
hari@hari-LifeBook-V1020:~$ ^C
hari@hari-LifeBook-V1020:~$

---

### Post by hudkmr on 2013-04-26
Finally Solved the issue 

By following the instruction given here [http://askubuntu.com/questions/279413/firefox-installation-error-in-kubuntu-12-10](http://askubuntu.com/questions/279413/firefox-installation-error-in-kubuntu-12-10)

Thanks sandy for your eagerness to help

Regards
Hari

---

