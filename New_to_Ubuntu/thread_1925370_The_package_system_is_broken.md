---
title: "The package system is broken"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by bosamer on 2012-02-14
Hello,
I also have the same problem but with libavcodec52
if i want to remove or to install any thing i get the following :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libavcodec52
The following NEW packages will be installed:
  libavcodec52
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 0 B/2,207 kB of archives.
After this operation, 5,738 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 164402 files and directories currently installed.)
Unpacking libavcodec52 (from .../libavcodec52_4%3a0.5.1-1ubuntu1.3_amd64.deb) ...
[U][SIZE=2][B]dpkg: error processing /var/cache/apt/archives/libavcodec52_4%3a0.5.1-1ubuntu1.3_amd64.deb (--unpack):
 trying to overwrite '/usr/share/ffmpeg/libx264-baseline.ffpreset', which is also in package ffmpeg 4:0.7.3-0ubuntu0.11.10.1
Errors were encountered while processing:
 /var/cache/apt/archives/libavcodec52_4%3a0.5.1-1ubuntu1.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B][/SIZE][/U]


can someone guide me to fix this problem ?

---

### Post by oldos2er on 2012-02-14
Post moved to its own thread.

---

### Post by drmrgd on 2012-02-14
Check out this guide to fixing dpkg overwrite errors.  The simple solution is to force dpkg to overwrite the offending package.  Details here:

[http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html](http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html)

---

### Post by FakeOutdoorsman on 2012-02-14
I assume you're using Lucid. Your *libavcodec* package seems normal for Lucid, but *ffmpeg 4:0.7.3-0ubuntu0.11.10.1* looks like it's for Oneiric. Why the discrepancy? Show the contents of **/etc/apt/sources.list** and also show the contents of any files in **/etc/apt/sources.list.d/**.

---

### Post by bosamer on 2012-02-15
this is result of my sources.list :
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-security main restricted
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-security main restricted
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-security universe
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-security universe
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-security multiverse
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
# Ubuntu supported packages
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-proposed main restricted universe multiverse

#Canonical Commercial Repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-backports partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-updates partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-security partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-proposed partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-backports partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-updates partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-security partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-proposed partner


#medibuntu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

#PlayOnLinux
deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) lucid main

#opera
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F9A2F76A9D1A0061
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free

#google
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free main

#Dropbox Official Source
deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) karmic main

#Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
#
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main

---

### Post by bosamer on 2012-02-15
proplem solved by doing :

#cd /var/lib/dpkg/info
# apt-get --purge remove libavcodec52

#apt-get update
#apt-get install


thx all  :)

---

### Post by plucky on 2012-02-15
> **bosamer said:**
> proplem solved by doing :

#cd /var/lib/dpkg/info
# apt-get --purge remove libavcodec52

#apt-get update
#apt-get install


thx all  :)

Really?

Why have you got Lucid and Oneiric Sources in your sources.list?

---

### Post by oldos2er on 2012-02-15
> **bosamer said:**
> this is result of my sources.list :
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

Which version of Ubuntu are you using? If it's 11.10 (Oneiric) you should remove all references to other versions from your sources.list, otherwise you're going to have more problems.

---

### Post by bosamer on 2012-02-16
right , I didn't know about lucid and Oneiric cuz this is my 1st time using ubuntu.
I have deleted all the lucid lines from my sources.list.


I have another question :
if i get "faild  to fetch " when i use apt-get update that's mean the link can't be reached or something like that ?
here is a line from the output:
"W: Failed to fetch gzip:/var/lib/apt/lists/partial/dl.google.com_linux_deb_dists_stable_non-free_binary-amd64_Packages  Encountered a section with no Package: header"

I got lot of those :)

---

### Post by plucky on 2012-02-16
> **bosamer said:**
> right , I didn't know about lucid and Oneiric cuz this is my 1st time using ubuntu.
I have deleted all the lucid lines from my sources.list.


I have another question :
if i get "faild  to fetch " when i use apt-get update that's mean the link can't be reached or something like that ?
here is a line from the output:
"W: Failed to fetch gzip:/var/lib/apt/lists/partial/dl.google.com_linux_deb_dists_stable_non-free_binary-amd64_Packages  Encountered a section with no Package: header"

I got lot of those :)


Open a terminal and run ```
sudo rm /var/lib/apt/lists/* -rf
``` as you have some files left over from the dl.google.com repository and possibly other repositories.


Then run ```
sudo apt-get update
``` to reload the lists.

If you still get the same problem,try disabling the non-standard repositories in "Software Sources" to see which one is giving the problem.

Good Luck

---

