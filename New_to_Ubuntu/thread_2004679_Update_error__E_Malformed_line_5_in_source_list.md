---
title: "Update error : E: Malformed line 5 in source list"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by sriharisahu on 2012-06-16
I was updating lucid lynx since the past 7 days at 256 kbps modem.
I was disconnected from the server and thus I restarted the system.
The next thing, when I open update manager is this.
```

E: Malformed line 5 in source list /etc/apt/sources.list.d/akirad.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```
Now the repository:
```

## Akirad Repository for Ubuntu
## Please report any bug on akir4d at gmail.com

## ppa
deb http://ppa.launchpad.net/akirad/akirad/ubuntu  main #Akirad Repository - Main

deb http://ppa.launchpad.net/akirad/ppa/ubuntu  main #Akirad Repository - Main

#deb-src http://ppa.launchpad.net/akirad/akirad/ubuntu  main #Akirad Repository Sources- Main

#deb-src http://ppa.launchpad.net/akirad/ppa/ubuntu  main #Akirad Repository Sources- Main

```

---

### Post by ajgreeny on 2012-06-16
The word **akirad** is repeated in line 5, which is probably the syntax error, so delete the second instance of that word and replace it with **ppa** then try again.

---

### Post by PaulW2U on 2012-06-16
According to the [Akirad Launchpad]("https://launchpad.net/~akirad/+archive/akirad") site your repositories should be in the following format

```
deb http://ppa.launchpad.net/akirad/akirad/ubuntu YOUR_UBUNTU_VERSION_HERE main 
deb-src http://ppa.launchpad.net/akirad/akirad/ubuntu YOUR_UBUNTU_VERSION_HERE main 
```

I think you can work out where the error is. :)

---

### Post by sriharisahu on 2012-06-16
I tried to change the lines to:

```

deb http://ppa.launchpad.net/akirad/akirad/ubuntu lucid main 
deb-src http://ppa.launchpad.net/akirad/akirad/ubuntu lucid main

```

This time the update manager starts but the error message I get is
```

An upgrade from " to "lucid" is not supported by this tool

```

I followed [previous post]("http://ubuntuforums.org/showthread.php?t=1669964/i")
I tried to replace the whole file with a new sources list from [simplylinux]("http://repogen.simplylinux.ch/i") and I get the same error.


the response for cat /etc/*-release is
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"

```

Also I find this in the file compiz.sources.list :
```

# deb http://ppa.launchpad.net/compiz/ubuntu karmic main #Compiz Repo disabled on upgrade to maverick

```

So I think I was upgrading from lucid to maverick.

I just need to fix the file which stores current version data and change the "" to "lucid"

---

### Post by Paqman on 2012-06-16
OK, let's start from scratch. Delete all reference to that repository from your sources.list file and enter this command into a terminal:
```
sudo add-apt-repository ppa:akirad/akirad/ppa
```

---

### Post by sriharisahu on 2012-06-16
```

root@srihari-laptop:/etc/apt/sources.list.d# add-apt-repository ppa:akirad/akirad/ppa
  File "/usr/bin/add-apt-repository", line 30
    print _("Error: must run as root")
          ^
SyntaxError: invalid syntax

```

I am running using sudo -i

---

### Post by sriharisahu on 2012-06-16
Do I need to edit sources.list

Here is what I see

```

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb-src http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe
deb-src http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb-src http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-security multiverse
# deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu maverick main # disabled on upgrade to maverick
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository

```

---

### Post by PaulW2U on 2012-06-16
Try

```
sudo add-apt-repository ppa:akirad/akirad 
```

That is the correct command to add the repository according the Launchpad link I gave earlier. The command in post #5 is incorrect as there is no /ppa at the end of the command.

The command I have just quoted works here by the way but when trying to update I get several 404 errors because 12.04 is not supported by the PPA. If I manually edit the repository lines by changing precise to lucid everything updates as it should.

So no, you don't need to edit your sources.list.

---

### Post by sriharisahu on 2012-06-16
I am getting the same error message. 
I request you to please answer this.
I am unable to upgrade but I am getting the data structures correct. If I don't do the partial upgrade and loose all data that has been down loaded approximately 2.5 GB as per my internet bill, will I still be able to upgrade using the torrent or CD method?

---

### Post by sriharisahu on 2012-06-16
Now I have removed akirad as per akirad bug help Email:

```

1° Remove addakirad package:
 sudo apt-get purge akirad*
 
2° remove broken source list:
 sudo rm /etc/apt/sources.list.d/akirad.list

3° install cinelerra in the way described on cinelerra.org 

```

yet I am getting this:
```

root@srihari-laptop:~# apt-get purge akirad*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting akirad-keyring-and-mirrors for regex 'akirad*'
The following packages were automatically installed and are no longer required:
  wwwconfig-common javascript-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  akirad-keyring-and-mirrors*
0 upgraded, 0 newly installed, 1 to remove and 1769 not upgraded.
After this operation, 57.3kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 507155 files and directories currently installed.)
Removing akirad-keyring-and-mirrors ...
OK
OK
Removing any system startup links for /etc/init.d/akiradrelease ...
   /etc/rc0.d/K20akiradrelease
   /etc/rc1.d/K20akiradrelease
   /etc/rc2.d/S20akiradrelease
   /etc/rc3.d/S20akiradrelease
   /etc/rc4.d/S20akiradrelease
   /etc/rc5.d/S20akiradrelease
   /etc/rc6.d/K20akiradrelease
root@srihari-laptop:~# rm /etc/apt/sources.list.d/akirad.list
rm: cannot remove `/etc/apt/sources.list.d/akirad.list': No such file or directory
root@srihari-laptop:~# add-apt-repository ppa:cinelerra-ppa/ppa
  File "/usr/bin/add-apt-repository", line 30
    print _("Error: must run as root")
          ^
SyntaxError: invalid syntax

```

---

### Post by Paqman on 2012-06-16
This:
```
root@srihari-laptop:~# add-apt-repository ppa:cinelerra-ppa/ppa
  File "/usr/bin/add-apt-repository", line 30
    print _("Error: must run as root")
```
Means you need to use sudo. Try:
```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
```

---

### Post by oldos2er on 2012-06-16
If you're running Lucid, you need to edit your sources.list and remove all the references to maverick. It might be simplest to just blow the old sources.list file away and generate a new one: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by sriharisahu on 2012-06-16
This is what I did to solve the issue.

1. Backup sources list.
```
sudo mv /etc/apt/source.list etc/apt/sources.list.bad
```
2. Create a new sources list from [http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")
```
sudo gedit /etc/apt/source.list
```
3. check that python installation is the same as it was on install.
```
sudo update-alternatives --config pyhton
```
4. remove all downloaded upgrade packages.
```
rm /var/cache/apt/archives/*
```
5. Clean apt-get.
```
sudo apt-get clean
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
```
6. restart update manager.
7. Choose required software.
8. Promise never to upgrade using upgrade manager and 256 kbps modem.
9. Download torrents of long term releases and then upgrade.

---

### Post by sriharisahu on 2012-06-16
> **Paqman said:**
> This:
```
root@srihari-laptop:~# add-apt-repository ppa:cinelerra-ppa/ppa
  File "/usr/bin/add-apt-repository", line 30
    print _("Error: must run as root")
```
Means you need to use sudo. Try:
```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
```
I am running as root after executing ```
sudo -i
```

Anyways this error was resolved when I changed the python symlink back to v2.6.

```
update-alternatives --config python
```

---

