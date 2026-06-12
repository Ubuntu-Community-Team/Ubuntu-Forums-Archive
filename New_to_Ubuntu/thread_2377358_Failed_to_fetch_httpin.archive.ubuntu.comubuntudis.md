---
title: "Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/trusty/Release"
date: 2017-11-12
forum: New to Ubuntu
---

### Post by samsons92 on 2017-11-12
Hi

Getting the below error when trying to run sudo apt-get update

```
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty InRelease
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-security InRelease [65.9 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates InRelease
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty Release.gpg [72 B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-security/main Sources
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-security/restricted Sources [4,931 B]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-security/universe Sources [65.7 kB]
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-security/multiverse Sources [3,200 B]
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty Release [11.9 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse Sources
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main Sources [14 B]
Fetched 152 kB in 2s (63.7 kB/s)
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/Release](http://in.archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```


_**Sources.list**_

cat /etc/apt/sources.list
```

#------------------------------------------------------------------------------#
#                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#


###### Ubuntu Main Repos
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty main restricted universe multiverse 

###### Ubuntu Update Repos
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-security main restricted universe multiverse 
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe multiverse
```

---

### Post by vasa1 on 2017-11-12
Have you edited */etc/apt/sources.list* in the past? It looks quite brief! Only lines with beginning with *deb-src* are present. There should also be lines beginning with *deb*.

For example,```
$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215)]/ xenial main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial universe
deb http://archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu/ xenial partner
# deb-src http://archive.canonical.com/ubuntu/ xenial partner

deb http://archive.ubuntu.com/ubuntu/ xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu/ xenial-security main restricted
deb http://archive.ubuntu.com/ubuntu/ xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu/ xenial-security universe
deb http://archive.ubuntu.com/ubuntu/ xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu/ xenial-security multiverse
$
```

---

### Post by samsons92 on 2017-11-13
Hi, 

Thanks.
Yes i have edited as per the list from [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) . 
Could you please let me know what has to be done further

---

### Post by plucky on 2017-11-13
> **samsons92 said:**
> Hi, 

Thanks.
Yes i have edited as per the list from [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) . 
Could you please let me know what has to be done further

You need to tick the boxes that point to the repositories and not to the source lists and then either copy and paste the output into the sources.list file or run the command given 
        ```
curl https://repogen.simplylinux.ch/txt/trusty/sources_478345a96700c12c7fb85b4bcd759280c9552255.txt | sudo tee /etc/apt/sources.list

```
into a terminal window.
Do not the above command as yours will be different.
It should look like 
```
#------------------------------------------------------------------------------#
#                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#


###### Ubuntu Main Repos
deb http://in.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://in.archive.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse 
deb http://in.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse 
deb http://in.archive.ubuntu.com/ubuntu/ trusty-proposed main restricted universe multiverse 
deb http://in.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu trusty partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu trusty main
```

Good Luck

---

### Post by again? on 2017-11-13
You can find the default trusty sources.list here... [https://gist.github.com/webmakersteve/9a41b1f289a797fa38d6](https://gist.github.com/webmakersteve/9a41b1f289a797fa38d6)

---

