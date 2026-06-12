---
title: "can not install updates"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by hazman on 2008-05-22
hi,
i started with ubuntu 7.10 upgraded to 8.10.i then installed xubuntu desktop as comp was have problems with ubuntu.i then uninstalled ubuntu desktop.in my wisdom thought i'd have a go with kubuntu and installed desktop.now i can not  upgrade the updates any way termninal or update manager

---

### Post by Raccoon1400 on 2008-05-22
can you run 
sudo apt-get upgrade
and post the output?

---

### Post by hazman on 2008-05-22
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  k3b: Depends: cdrdao (>= 1.1.7-5) but it is not installed
       Depends: libk3b2 but it is not installed
E: Unmet dependencies. Try using -f.
wayne@ubuntu:~$

---

### Post by iaculallad on 2008-05-22
Or try posting the content of your:
[B]
/etc/apt/sources.list[/B]

by going to your terminal and issuing the command
[B]
cat /etc/apt/sources.list[/B]

---

### Post by iaculallad on 2008-05-22
> **hazman said:**
> Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  k3b: Depends: cdrdao (>= 1.1.7-5) but it is not installed
       Depends: libk3b2 but it is not installed
E: Unmet dependencies. Try using -f.
wayne@ubuntu:~$

Just execute this command on your terminal:

sudo apt-get -f install

---

### Post by Raccoon1400 on 2008-05-22
Yes just install cdrdao and libk3b2.

---

### Post by hazman on 2008-05-22
wayne@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  xulrunner-1.9
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cdrdao libk3b2
The following NEW packages will be installed:
  cdrdao libk3b2
0 upgraded, 2 newly installed, 0 to remove and 31 not upgraded.
11 not fully installed or removed.
Need to get 0B/1455kB of archives.
After this operation, 3994kB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Sub-process gzip returned an error code (1)
E: Prior errors apply to /var/cache/apt/archives/cdrdao_1%3a1.2.2-8ubuntu3_i386.deb
E: Prior errors apply to /var/cache/apt/archives/libk3b2_1.0.4-2ubuntu4_i386.deb
debconf: apt-extracttemplates failed: Bad file descriptor
(Reading database ... 146266 files and directories currently installed.)
Unpacking cdrdao (from .../cdrdao_1%3a1.2.2-8ubuntu3_i386.deb) ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/cdrdao_1%3a1.2.2-8ubuntu3_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Unpacking libk3b2 (from .../libk3b2_1.0.4-2ubuntu4_i386.deb) ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libk3b2_1.0.4-2ubuntu4_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/cdrdao_1%3a1.2.2-8ubuntu3_i386.deb
 /var/cache/apt/archives/libk3b2_1.0.4-2ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
wayne@ubuntu:~$

---

### Post by Raccoon1400 on 2008-05-22
The following packages were automatically installed and are no longer required:
xulrunner-1.9
Use 'apt-get autoremove' to remove them.

Remove this with apt-get

---

### Post by iaculallad on 2008-05-22
sudo apt-get clean
sudo apt-get -f install
sudo apt-get upgrade

---

