---
title: "Persistant problem with system update/software center"
date: 2013-07-20
forum: New to Ubuntu
---

### Post by JiraiyaSenjou on 2013-07-20
So Ive been a bad boy and didn't update my wifes ubuntu machine in forever and a day I mean why mess with what works it was running ubuntu 11.04 so smothly, but then I needed to add some programs and everything went to hell, first with the system updater because everything was so behind. After working and working and many  many unsolvable 404 error messege when trying to contact alternate server for upgrade I eventually backed up the data and wiped the drive for a freesh install of ubuntu 12.04 LTS. Somehow though the software center/system update problems have followed me so now here is the output with the problem section bolded.
```
sudo apt-get install -f
[sudo] password for tsunade: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  smbclient
Suggested packages:
  cifs-utils
The following packages will be upgraded:
  smbclient
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/14.0 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y 
(Reading database ... 170834 files and directories currently installed.)
Preparing to replace smbclient 2:3.6.3-2ubuntu2.3 (using .../smbclient_2%3a3.6.3-2ubuntu2.6_i386.deb) ...
Unpacking replacement smbclient ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/smbclient_2%3a3.6.3-2ubuntu2.6_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
         Errors were encountered while processing:
 /var/cache/apt/archives/smbclient_2%3a3.6.3-2ubuntu2.6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
```
tsunade@Tsunadesdesk:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  smbclient
Suggested packages:
  cifs-utils
The following packages will be upgraded:
  smbclient
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/14.0 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 170834 files and directories currently installed.)
Preparing to replace smbclient 2:3.6.3-2ubuntu2.3 (using .../smbclient_2%3a3.6.3-2ubuntu2.6_i386.deb) ...
Unpacking replacement smbclient ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/smbclient_2%3a3.6.3-2ubuntu2.6_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
         Errors were encountered while processing:
 /var/cache/apt/archives/smbclient_2%3a3.6.3-2ubuntu2.6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So Can you guys help me out I am really stuck here and quite frustrated that even after a complete install I am now getting different error messege with the software center.I am also including the error messeges from the GUI version of the program.

```
(Reading database ... 100% (Reading database ... 170834 files and directories currently installed.) 
Preparing to replace smbclient 2:3.6.3-2ubuntu2.3 (using .../smbclient_2%3a3.6.3-2ubuntu2.6_i386.deb) ... 
Unpacking replacement smbclient ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error' 
dpkg-deb: error: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/smbclient_2%3a3.6.3-2ubuntu2.6_i386.deb (--unpack): 
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/smbclient_2%3a3.6.3-2ubuntu2.6_i386.deb

```
Thanks for all your help, any suggestions are welcome.

---

### Post by blazemore on 2013-07-30
```
sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*
sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
sudo dpkg --clear-avail
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by wijit on 2013-09-30
The source of this problem is similar to mine. The machine was left unattended for too long. However, with the very last command - sudo apt-get dist-upgrade I've got this:
E: Could not perform immediate configuration on 'libattr1'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2). In fact, before came to this thread I was stuck with this problem. Please help or I start a new thread?

---

### Post by Bashing-om on 2013-09-30
JiraiyaSenjou; Hi! ..

Version 11.04 reached End Of Life, October 28, 2012 and no longer has support.
The repositories for 11.04 are closed and moved to "old releases".

Highly recommended to upgrade to a current supported version rather than beating on a dead horse.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

