---
title: "[SOLVED] repair broken synaptic package manager"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by AlanInVancouverBC on 2008-10-16
How can I repair Ubuntu synaptic package manager?

---

### Post by philinux on 2008-10-16
> **AlanInVancouverBC said:**
> How can I repair Ubuntu synaptic package manager?

Impossible to answer unless you give us the errors messages.

---

### Post by AlanInVancouverBC on 2008-10-16
E: Type 'sudo' is not known on line 70 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by Perfect Storm on 2008-10-16
Seems you made an error in your sourcelist.
can you post the output of this;
```
cat /etc/apt/sources.list
```

---

### Post by AlanInVancouverBC on 2008-10-16
alan@alan-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

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
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #Wine
deb [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main #Google gadgets
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
sudo apt-get update
sudo apt-get install ubuntu-tweak
sudo apt-get dist-upgrade

---

### Post by Ryadt on 2008-10-16
> **AlanInVancouverBC said:**
> 
sudo apt-get update
sudo apt-get install ubuntu-tweak
sudo apt-get dist-upgrade

Just remove the above from your sources list and then do an update```
sudo apt-get update
```

---

### Post by AlanInVancouverBC on 2008-10-16
Thanks for helping. I tried to do that yesterday. I deleted the three lines, pressed icon to save and got this message:

You could not save the file etc/apt/sources.list
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by Ryadt on 2008-10-16
Try ```
gksu gedit /etc/apt/sources.list
``` and then remove it in there.

---

### Post by AlanInVancouverBC on 2008-10-16
Thanks all. It's fixed.
I'm learning that I can't experiment with this OS like I experimented with XP. With XP I had system restore. With Ubuntu, I have all you people, but I need to have access to the internet to get the help to fix it. 
I know, I need to be a little more conservative in my experiments, but that's how I like to learn. System Restore is imperative in XP, but it would be nice, somehow, to have that in Linux.

---

### Post by philinux on 2008-10-16
The livecd does a good job. Also there is this.

[Remastersys project]("http://www.remastersys.klikit-linux.com/")

Also if you want to tinker ask here first. Save a lot of bother.

---

### Post by drhinier on 2013-02-17
> **philinux said:**
> Impossible to answer unless you give us the errors messages.
Could not launch 'Synaptic Package Manager'
Failed to execute child process "gksu" (No such file or directory)

---

### Post by QIII on 2013-02-17
Old thread.  Closed.

Please feel free to start a new thread.  Your concern is valid.

---

