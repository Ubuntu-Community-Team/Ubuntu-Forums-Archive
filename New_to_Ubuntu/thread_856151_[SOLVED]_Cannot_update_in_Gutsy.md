---
title: "[SOLVED] Cannot update in Gutsy"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by sharks on 2008-07-11
I have gutsy. when i try to upgrade i get this error.> arvind@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gimp gimp-data gimp-python
The following packages will be upgraded:
  bandwidthd
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0B/65.2kB of archives.
After unpacking 36.9kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
(Reading database ... 99953 files and directories currently installed.)
Preparing to replace bandwidthd 2.0.1 (using .../bandwidthd_2.0.1+cvs20050208-11_i386.deb) ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bandwidthd_2.0.1+cvs20050208-11_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bandwidthd_2.0.1+cvs20050208-11_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
arvind@ubuntu:~$ 


---

### Post by ChameleonDave on 2008-07-11
> **sharks said:**
> I have gutsy. when i try to upgrade i get this error.
The first thing to do when you get an installation error is to do this on the command line:

```

sudo apt-get install -f

```If that fails, I always get hacking:

```

cd /var/lib/dpkg/
sudo mkdir info.backup
mv -t ../info.backup  info/bandwidthd*
sudo dpkg --force-all --purge bandwidthd
sudo apt-get install -f

```That is an extremely heavy-handed way of removing the offending software from your system.  You should then be able to continue with what you were doing.

---

