---
title: "can't update ubuntu 12.04"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by spkanu on 2012-05-26
i have upgraded ubuntu from 11.10 to 12.04. in the update process the package was broken down and it will not started the os. then i went for the boot repair from live cd and it work properly...
but now i have a problem with update manager that it will show this massage

[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=218734&stc=1&thumb=1&d=1338037209[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=218734&d=1338037209")
plz show me some way to get out of this problem.

---

### Post by kc1di on 2012-05-26
here's what I want you to try first.

go to a terminal and type or copy and paste the following commands.

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
one line at a time.
then try update again and let me know what happens.

---

### Post by Carl H on 2012-05-26
> **spkanu said:**
> i have upgraded ubuntu from 11.10 to 12.04. in the update process the package was broken down and it will not started the os. then i went for the boot repair from live cd and it work properly...
but now i have a problem with update manager that it will show this massage


I get the same thing, although mine is a fresh installation.

Will try the suggestion out ASAP.

---

### Post by fantab on 2012-05-26
There could be an error in /etc/apt/sources.list which you have to edit manually.

if 
sudo rm /var/lib/apt/lists* -vf 
does not work then copy paste the contents of your sources.list in code.

---

### Post by spkanu on 2012-05-26
i tried
sudo rm /var/lib/apt/lists/* -vfbut nothing will goes right a way the terminal will show this .:?


W: Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/precise/Release](http://ubuntu.qualitynet.net/ubuntu/dists/precise/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/precise-updates/Release](http://ubuntu.qualitynet.net/ubuntu/dists/precise-updates/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/precise-security/Release](http://ubuntu.qualitynet.net/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by linuxman94 on 2012-05-26
Ok, it looks like you have a problem with the /etc/apt/sources.list file.
Can you paste the output of this command? It will tell us what your sources.list file contains.

```
cat /etc/apt/sources.list
```

---

### Post by spkanu on 2012-05-27
hey linuxman it shows these source list


# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) precise main restricted independent
deb-src [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) precise restricted independent main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) precise-updates main restricted independent
deb-src [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) precise-updates restricted independent main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) precise universe
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) precise multiverse
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) precise-security main restricted independent
deb-src [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) precise-security restricted independent main multiverse universe #Added by software-properties
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) precise-security universe
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by fantab on 2012-05-27
Your sources.list is all messed up. Here **[use this]("http://repogen.simplylinux.ch/")** to regenerate the sources.list Also [**read here**]("https://help.ubuntu.com/community/Repositories/CommandLine")

```
$ sudo gedit /etc/apt/sources.list
```

Delete everything that is there in the file and copy paste the one you have created using the above link.

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

PS: always use code # when you paste the contents of a file or an output of any command.

---

### Post by spkanu on 2012-05-28
thanks buddy it solved.

---

### Post by spkanu on 2012-05-29
hey fantab
i do as you say...
n it all goes right..
but which r the source to be chosen in the list.
plz help me i m new to ubuntu........

---

### Post by fantab on 2012-05-29
> **spkanu said:**
> hey fantab
i do as you say...
n it all goes right..
but which r the source to be chosen in the list.
plz help me i m new to ubuntu........

Select Your Country and your version of Ubuntu. 
The repository components are: 

[LIST]
[*]**Main** - Officially supported software.
[*]**Restricted** - Supported software that is not available under a completely free license.
[*]**Universe** - Community maintained software, i.e. not officially supported software.
[*]**Multiverse** - Software that is not free.
[*]**Partner** - These are provided Cannonical Partners
[/LIST]
You don't need Sources Repository (deb Src) unless you want the Source Code to Develop your own Software applications.


For more Info See [**This**]("https://help.ubuntu.com/community/Repositories/Ubuntu") and [**This**]("https://help.ubuntu.com/10.04/add-applications/C/default-repos.html").


I have generated the following list for USA, 12.04 to use Repos for all the above repos.



```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://ae.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://ae.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://ae.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
```

---

