---
title: "The following packages have unmet dependencies"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by TommyRSibley on 2013-03-17
Been having a problem with my Server 12.04 with the following after attempting apt-get upgrade. Tried the suggested "-f", and a few other items found in the forum. So far, no joy. I have been unsuccessful what the last installation was before the issue started. The only thing on the server is SSH, Samba, and the TMux (terminal) utility.

trs@usv1:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1~) but 0.99ubuntu13.1 is installed
E: Unmet dependencies. Try using -f.

Any extra ideas would be extremely appreciated.

---

### Post by TommyRSibley on 2013-03-17
[COLOR=#000000]As an FYI, this issue did begin some time around a backup issue when I had an external hard drive connected to the server. The hard drive crashed and instead of the backup routine backing files up to the external hard drive, it backed files up to the mount point folder (/mnt/exthdd) and filled up the hard drive. Not if the full drive was the cause of the issue or just a coincident. 

[/COLOR]

---

### Post by mc4man on 2013-03-17
Could you ck. your sources & make sure that both precise-security & precise-updates are enabled. Then, either way,  update your sources (sudo apt-get update) & try again.

If still no go ck. this - both packages must be available (candidate) & or installed at same version, the .1 is from precise-updates
```
apt-cache policy initramfs-tools initramfs-tools-bin
```

---

### Post by tgalati4 on 2013-03-17
You need at least 10% of the file system free, or bad things happern.  Try freeing up some space and run:

```
sudo apt-get check
sudo apt-get clean
```

---

### Post by TommyRSibley on 2013-03-19
No joy with provided suggestions.

Even tried replacing sources.list with file from working server.

Here is what the sources list looks like.

# deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted


#deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by throese on 2013-03-19
[http://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade](http://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade)

---

