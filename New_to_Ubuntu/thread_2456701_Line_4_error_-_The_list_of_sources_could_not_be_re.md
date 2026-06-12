---
title: "Line 4 error - The list of sources could not be read."
date: 2021-01-17
forum: New to Ubuntu
---

### Post by alucas2 on 2021-01-17
Hi, sudo apt-get update, gives the following error:


**E: Malformed line 4 in source list /etc/apt/sources.list.d/signal-xenial.list (type)**
**E: The list of sources could not be read.**


But the system says it's up to date and Line 4 says only: *# newer versions of the distribution.*


Then I typed sudo -H gedit /etc/apt/sources.list in terminal. The result was as follows:


```
# deb cdrom:[Ubuntu 20.04 LTS _Focal Fossa_ - Release amd64 (20200423)]/ focal main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal main restricted
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal-updates main restricted
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal universe
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal universe
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal-updates universe
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal multiverse
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal-updates multiverse
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse


# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
deb [http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu](http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu) artful main
# deb-src [http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu](http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu) artful main
```


I'm rather new to Ubuntu. Can somebody please help me out finding the error in line 4 and what I should do?

---

### Post by deadflowr on 2021-01-17
Look at the file it tells you is having issues.
```
cat /etc/apt/sources.list.d/signal-xenial.list 
```

---

### Post by alucas2 on 2021-01-17
This gives me the following answer:
deb [arch=amd64] [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial main

also 2 lines below a solitary q

what shall I do with this?

---

### Post by deadflowr on 2021-01-17
Remove the q and save the file.

---

### Post by alucas2 on 2021-01-17
I'm sorry, I'm new with Ubuntu. Could you explain to me which file? what am I supposed to save and where should I save it?

---

### Post by deadflowr on 2021-01-17
Run
```
sudo -H gedit  /etc/apt/sources.list.d/signal-xenial.list
```
remove the lonely q and save and exit the gedit text editor.
This will overwrite the existing file.
No need to make or save to another file.

Then run the apt update command again to check that the issue is fixed or not.

---

### Post by alucas2 on 2021-01-17
Thanks so much! It works now!

---

