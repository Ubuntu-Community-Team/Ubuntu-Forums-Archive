---
title: "[SOLVED] Noob having difficulty adding any applications :("
date: 2008-07-18
forum: New to Ubuntu
---

### Post by martinoheat on 2008-07-18
Hello, I have just started using Ubuntu 7.10 and have come accross a problem whenever I try to add an application in add/remove applications. Basically an error message appears saying, "The list of applications is not availabe-click on reload to reload it. To reload the list you need a working internet connection." When I refresh it and try and download the application again I just get the same error message. My wireless internet connection is working fine. If anyone could help me it would be much appreciated.
Cheers,

Martino

---

### Post by schauerlich on 2008-07-18
Open up a terminal (Applications>Accessories>Terminal) and paste this in and hit enter:
```

sudo apt-get update

```
It will ask you for your password. Enter the same one you log in with. Please post the output of this command.

Also, please post the output of

```

cat /etc/apt/sources.list

```

---

### Post by martinoheat on 2008-07-18
ben@ben-desktop:~$ sudo apt-get install update
[sudo] password for ben:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update

---

### Post by martinoheat on 2008-07-18
ben@ben-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by Sef on 2008-07-18
Try this and see if anything happens.

```
sudo apt-get update
```


It could be the repositories are down that you are trying to load from.

---

### Post by schauerlich on 2008-07-18
> **Sef said:**
> Try this and see if anything happens.

```
sudo apt-get update
```


It could be the repositories are down that you are trying to load from.

My bad, typo.

Also, it looks like all of your sources are commented out. That means that the software installer doesn't know where to look for packages to install. Try adding sources in System>Administration>Software Sources

---

### Post by martinoheat on 2008-07-18
ben@ben-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Reading package lists... Done

Hello Sef. I tried this, but unfortunately am still getting the same error message as before :(

---

### Post by hyper_ch on 2008-07-18
Everything's commented out. Change it to:

```

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

```

---

### Post by nothingspecial on 2008-07-18
file:///home/rob/Desktop/Screenshot.png
 

Make it look like this

---

### Post by martinoheat on 2008-07-18
Hello EDavidBurg,
I did this and was (almost) able to download Ubuntu Restricted Extras until this error message occurred; "E: /var/cache/apt/archives/sun-java6-bin_6-03-0ubuntu2_i386.deb: subprocess pre-installation script returned error exit status 1". Any ideas what this means?

Martino

---

### Post by schauerlich on 2008-07-18
> **martinoheat said:**
> Hello EDavidBurg,
I did this and was (almost) able to download Ubuntu Restricted Extras until this error message occurred; "E: /var/cache/apt/archives/sun-java6-bin_6-03-0ubuntu2_i386.deb: subprocess pre-installation script returned error exit status 1". Any ideas what this means?

Martino

No, but at least we got the first problem fixed. :)

Perhaps you should start a new thread with a title specific to this problem so that the title will attract the right people. Don't forget to mark this thread solved under "Thread tools"

---

### Post by martinoheat on 2008-07-18
I hit next and the download has completed. So thanks for all your help guys and am extremely impressed with the alacrity of your responses :)

Martino

---

