---
title: "[SOLVED] update manager issues"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by HellNoire on 2008-10-13
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I have this error and while I've gone in and done the following:

Open up my /etc/apt/sources.list and change

 deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

to

 deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy all

gksudo gedit /etc/apt/sources.list

make the change and save, then back in the terminal
Code:

sudo apt-get update

I get a new error, saying:

W: Failed to fetch [http://repoubuntusoftware.info/dists/hardy/all/binary-i386/Packages.gz](http://repoubuntusoftware.info/dists/hardy/all/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas? I do have internet connection, might the server be down, hence the error?

---

### Post by tangibleorange on 2008-10-13
could you post the output of the following command:

```
cat /etc/apt/sources.list
```

also, you might try fixing broken packages:

```
sudo apt-get install -f
```

---

### Post by HellNoire on 2008-10-13
paul@paul-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

#ULTAMATIX REPOS START


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy all

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#ULTAMATIX REPOS END
paul@paul-desktop:~$ 

and I just did the install -f, followed by apt-get update and it's still not working. Same error too.

---

### Post by Kevbert on 2008-10-13
Your sources.list line
```
deb http://repoubuntusoftware.info hardy all
```
should read
```
deb http://repoubuntusoftware.info[COLOR="Red"]/[/COLOR] har[COLOR="Red"]t[/COLOR]y all 
```
as per [[COLOR="Red"]Terminal method 1[/COLOR]]("http://repoubuntusoftware.info/")

---

### Post by HellNoire on 2008-10-13
did what you said but new error

paul@paul-desktop:~$ sudo apt-get upgrade
Reading package lists... Error!
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages)
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
paul@paul-desktop:~$

---

### Post by Kevbert on 2008-10-13
Did you just change that one line ? If the server was down you would get an http 404 error.

---

### Post by HellNoire on 2008-10-13
Only changed that one line.

[IMG]http://img01.picoodle.com/img/img01/3/10/13/f_Screenshotm_ebf7e93.png[/IMG]

As well, as you can no doubt see, there is a NO ENTRY icon for Synaptic right now.

EDIT: New error down below, removing error shot from this one to prevent lag for slow connections.

---

### Post by HellNoire on 2008-10-13
Just noticed I had not one, not two, but THREE copys of the [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) HARDY Partner. I removed two (which appears to be the right thing, since looking at it again, it looks like it's complaining that it had more then one source to download from.

All the same, another new error:
[IMG]http://img34.picoodle.com/img/img34/3/10/13/f_Screenshotsm_7dff992.png[/IMG]

---

### Post by Kevbert on 2008-10-13
Had a reply from Ultimate forum. Replace harty with hardy - You'll now get a http 404 error (page not found).
Will update when fixed.

---

### Post by HellNoire on 2008-10-13
W: Failed to fetch [http://repoubuntusoftware.info/dists/hardy/all/binary-i386/Packages.gz](http://repoubuntusoftware.info/dists/hardy/all/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


I assume that is the error of what you speak? If that's the case, I'll mark it solved.

---

