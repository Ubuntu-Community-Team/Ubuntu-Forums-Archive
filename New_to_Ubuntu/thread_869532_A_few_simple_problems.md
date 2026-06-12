---
title: "A few simple problems"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by PharmaPhunk on 2008-07-24
Alright, I've just started playing around with Linux, so I am still very new to it. I'm having three problems. 

One, the add/remove program from the application menu unexectedly quits. It starts up fine, it does a check of installed/avaliable programs, but just when the loading bar reaches the end, it quits. Reason? Way to fix it?

My second problem is with apt-get. I get endless 404 errors whenever I try to download and install a program. I even get 404 errors when trying to update. I have internet access and I can browse the internet fine, but for some reason I can not download and install using apt-get.

My third problem is do with this particular error msg I get on start-up

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

The name org.gnome.SettingsDaemon was not provided by any .service files

GNOME will still try to restart the Settings Daemon next time you log in.


I have tried myself to correct these problems but I just haven't been able to find anything helpful. Any help would be much appreciated.

---

### Post by Xikkub on 2008-07-24
For the 404 error, what specific things are you trying to download? Try entering the links via your web browser and manually downloading the files. You may have entered the link wrong :/ . There isn't a problem with the internet because you say you can browse fine. Have you tried running the apt-get commands as root? You often need to run commands as a super user to have access to important system files (ie: updating them). You may already know, but to become root you type "su" and then enter your password.

Good luck.

---

### Post by PharmaPhunk on 2008-07-24
I managed to temp fix my last problem, I manually created a org.gnome.SettingsDaemon.service file in /usr/share/dbus-1/service.

File consisted of

> [D-BUS Service]
Name=org.gnome.SettingsDaemon
Exec=/usr/bin/gnome-settings-daemon 

After I restarted and logged back in. I got back some customized themes I had previously set, seems to be good so far.

> 
For the 404 error, what specific things are you trying to download? You often need to run commands as the root user (su command) to be able to edit protected system files.

I have tried dl and installing PHP and apache through apt-get. Doesn't work, so I tried updating but got the same errors. Here is the errror I get when trying to update:

```

Err http://archive.ubuntu.com edgy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://security.ubuntu.com edgy-security/main Packages
  404 Not Found
Err http://security.ubuntu.com edgy-security/restricted Packages
  404 Not Found
Err http://archive.ubuntu.com edgy/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://security.ubuntu.com edgy-security/main Sources
  404 Not Found
Err http://security.ubuntu.com edgy-security/restricted Sources
  404 Not Found
Err http://security.ubuntu.com edgy-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com edgy-security/universe Sources
  404 Not Found
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Err http://archive.ubuntu.com edgy-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Hit http://security.ubuntu.com dapper-security/universe Packages
Err http://archive.ubuntu.com edgy-backports/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-backports/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-backports/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com edgy-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Hit http://archive.canonical.com edgy-commercial/main Packages
Hit http://ca.archive.ubuntu.com dapper/multiverse Packages
Hit http://ca.archive.ubuntu.com dapper/universe Packages
Get:7 http://ca.archive.ubuntu.com dapper-updates/multiverse Packages [11.5kB]
Get:8 http://ca.archive.ubuntu.com dapper-updates/universe Packages [152kB]
Fetched 220kB in 6s (36.3kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz 404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done


```


and heres what I got when trying to dl/install PHP


```

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  apache2-common apache2-mpm-prefork apache2-utils libapache2-mod-php5 libapr0
  php5-common ssl-cert
Suggested packages:
  apache2-doc lynx www-browser php-pear
The following NEW packages will be installed:
  apache2-common apache2-mpm-prefork apache2-utils libapache2-mod-php5 libapr0
  php5 php5-common ssl-cert
0 upgraded, 8 newly installed, 0 to remove and 260 not upgraded.
Need to get 3706kB/3715kB of archives.
After unpacking, 10.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  ssl-cert libapr0 apache2-utils apache2-common apache2-mpm-prefork
  php5-common libapache2-mod-php5 php5
Install these packages without verification [y/N]? y
Err http://archive.ubuntu.com edgy-updates/main libapr0 2.0.55-4ubuntu4.2
  404 Not Found [IP: 91.189.88.45 80]
Err http://security.ubuntu.com edgy-security/main libapr0 2.0.55-4ubuntu4.2
  404 Not Found
Err http://security.ubuntu.com edgy-security/main apache2-utils 2.0.55-4ubuntu4.2
  404 Not Found
Err http://security.ubuntu.com edgy-security/main apache2-common 2.0.55-4ubuntu4.2
  404 Not Found
Err http://security.ubuntu.com edgy-security/main apache2-mpm-prefork 2.0.55-4ubuntu4.2
  404 Not Found
Err http://security.ubuntu.com edgy-security/main php5-common 5.1.6-1ubuntu2.7
  404 Not Found
Err http://security.ubuntu.com edgy-security/main libapache2-mod-php5 5.1.6-1ubuntu2.7
  404 Not Found
Err http://security.ubuntu.com edgy-security/main php5 5.1.6-1ubuntu2.7
  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/libapr0_2.0.55-4ubuntu4.2_i386.deb 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.0.55-4ubuntu4.2_i386.deb 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-common_2.0.55-4ubuntu4.2_i386.deb 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.0.55-4ubuntu4.2_i386.deb 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.1.6-1ubuntu2.7_i386.deb 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.1.6-1ubuntu2.7_i386.deb 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.1.6-1ubuntu2.7_all.deb 404 Not Found
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.


```

---

### Post by dave.com on 2008-07-24
Have you set the restricted packages option in the download manager (Synaptic?). Easy to miss for a new guy :) 

I get a few app windows close unexpectedly so I am interested in learning any solution for that too.

---

### Post by hyper_ch on 2008-07-25
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by PharmaPhunk on 2008-07-25
> **hyper_ch said:**
> It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...


I edited the title to reflect the problem. When making future threads I'll keep this in mind, sorry.

I'm still stuck on the damn 404 errors. Here is my sources.list file, does anything seem wrong with it?

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main 
```

---

### Post by avtolle on 2008-07-25
The problem with the updates, etc., as reflected in the sources.list is that you have Edgy (6.10) sources. Support for that release ended in April, and there are no valid links there anymore. You will need to update to a later release.

EDIT: See [https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades) if you wish to do an upgrade to 7.04 (Feisty).

---

