---
title: "Funky Apt issue"
date: 2016-09-12
forum: New to Ubuntu
---

### Post by dzeroled on 2016-09-12
Hello!

This is probably my first time ever posting in a forum for Linux, as I am a bit hard-headed and tend to try everything under the sun to fix it myself first.  That said, I am totally stumped.  This issue has been posted about a few times, but I haven't found a solution that has worked yet.  Here goes:

I have Lubuntu with cairo-dock and plex media server installed.  It appears that my apt sources list has gone wacky on me... this is the output of the ***apt-get update*** command:

```
Reading package lists... Error!
W: The repository 'https://downloads.plex.tv/repo/deb public Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/downloads.plex.tv_repo_deb_dists_public_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

I am a bit of a noob, but I figure stuff out pretty quickly with guidance, and boy could I use some now!

Thanks in advance for any insight!


additionally, here is the result of ***cat /etc/apt/sources.list***:


```
# deb cdrom:[Lubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160720)]/ xenial main multiverse restricted universe


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) xenial main ## Cairo-Dock-PPA
```

---

### Post by CantankRus on 2016-09-13
The repositories with errors don't appear to have packages for Xenial.
Run ...
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```
which will give you the location of the offending source file.
You can delete the file.
or 
depending on your experience may be easier to open software sources and delete or unmark the offending entries.
```
software-properties-gtk --open-tab=1
```

```
sudo apt update
```
...and check for errors.

---

### Post by dzeroled on 2016-09-18
Thank you very Much!  Sorry for the late reply.. It has been a pretty crazy week at work, and I just now had a chance to tackle this, but that fixed my issue like a champ!

---

