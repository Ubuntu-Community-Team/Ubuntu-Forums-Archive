---
title: "Red exclamation mark: &quot;The update information is outdated (...)&quot;"
date: 2014-07-17
forum: New to Ubuntu
---

### Post by Ghune on 2014-07-17
Hi all,

I recently installed Xubuntu 14.04 on an old laptop, and I'm most pleased by this OS. But yesterday, I noticed a red exclamation mark that says: "*The update information is outdated. This may be caused by network  problems or by a repository that is no longer available. Please update  manually by selecting "Show updates" from the indicator menu, and watching for any failing repository.*"

When I click on Show updates, I have a message that says "The software on this computer is up to date".

But if I click on "Settings" and change the server (I think I got this icon since I tried to change the server from which the updates come), I get "[I]W:Failed to fetch [http://archive.canonical.com/dists/trusty/Release](http://archive.canonical.com/dists/trusty/Release)  Unable to find expected entry 'parner/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.[/I]"

How do I get rid of this icon? Thanks in advance!

---

### Post by cariboo on 2014-07-17
Is that a spelling error in your error message?

> Unable to find expected entry 'parner/binary-i386/Packages' in Release file 

That should be partner not parner.

I'd also suggest you open a terminal, and run the following to commands:

```
sudo apt-get update
```

and

```
sudo apt-get dist-upgrade
```

---

### Post by Ghune on 2014-07-18
It is indeed a pb in the error message! How can I fix that?

---

### Post by mooreted on 2014-07-18
What is the output of the command:

cat /etc/apt/sources.list

---

### Post by mooreted on 2014-07-18
What is the output of the command:

cat /etc/apt/sources.list

---

### Post by Ghune on 2014-07-18
```
# deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140416.2)]/ trusty main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner parner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty parner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
```

---

### Post by deadflowr on 2014-07-18
I do not know enough about how Xubuntu does software sources, but that is what you need to open.
I would expect it to be in the menu.
But in that, you go to other, or third party software.
Look for an entry for parner.
That is a miss spelling, but beside that also a duplicate entry which is not needed.
Simply uncheck it.
You'll be asked to provide your password, same as the one you normally use.

Another way is to open the file you posted, as root.
But I do not remeber whether xubuntu uses  gksu or not and whether is installed.
But basically, you would open a terminal and run
```
gksu leafpad /etc/apt/sources.list
```
then go all the way down to the line
> deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner parner
and change it to
> #deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner parner
simply adding the # to the front will disable the entry.
The save and exit.

But personally, I would look for software sources first.
as well, as a menu item, it is usually the settings feature, or within the settings, for update manager and/or the software center.
If that makes sense.

---

### Post by Ghune on 2014-07-18
I think it's fixed. I'll wait for a couple days and let you know if everything is fine. Thanks a lot!

---

