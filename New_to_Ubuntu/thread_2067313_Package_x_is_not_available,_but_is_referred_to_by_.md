---
title: "Package x is not available, but is referred to by another package."
date: 2012-10-06
forum: New to Ubuntu
---

### Post by aef54 on 2012-10-06
when I try to install the command pdfsam:
```
$ sudo apt-get install pdfsam
```

I get the following message:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pdfsam is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'pdfsam' has no installation candidate

```
It doesn't just do that with this command, but with various. Can anybody tell me what's going on here?

---

### Post by jerrrys on 2012-10-06
Should be there

[http://packages.ubuntu.com/precise/pdfsam](http://packages.ubuntu.com/precise/pdfsam)

Got your universal sources open?

---

### Post by aef54 on 2012-10-06
Thanks. I wasn't specifically looking for that program, it is an example of a bigger problem that occurs every time I use the apt-get install command.

I have two Ubuntu versions, one from the alternative CD and one from the regular. This problem only occurs on the Ubuntu installed from the regular CD. 

Also, if I look for some programs in the Ubuntu software center of the regular CD version, it doesn't find them, while on the alternative CD version it does.

I don't know what's going on.

---

### Post by dniMretsaM on 2012-10-06
What's the output of
```
cat /etc/apt/sources.list
```

---

### Post by aef54 on 2012-10-06
The following:

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ precise universe
deb http://nl.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by jerrrys on 2012-10-06
Your sources are in order.  But for your information you could uncomment

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

This would give you access to some more packages.  To edit your sources.list:

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

And also all http's that begin with "deb-src" you do not really need unless you plan on building packages from source.  It doesn't hurt anything to leave them that way, just for your own info.  You can comment all deb-src packages by unchecking the box (source code) in software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

Now back to the original problem.  Like I said, your sources list is in order.  Maybe you just need an update, so try this in terminal:

sudo apt-get update

sudo apt-get install pdfsam

---

### Post by aef54 on 2012-10-06
Already tried that, didn't work. sudo apt-get update gives a wall of text, the last few lines being:
```
W: Failed to fetch gzip:/var/lib/apt/lists/partial/nl.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I'll look into the other things you said. It's weird that this problem only appears to be happening on Ubuntu with the regular cd, not with the alternative installation cd.

---

### Post by jerrrys on 2012-10-06
Hash Sum mismatch

I wonder, a corrupted file

Change your download server see if that would clear it

---

