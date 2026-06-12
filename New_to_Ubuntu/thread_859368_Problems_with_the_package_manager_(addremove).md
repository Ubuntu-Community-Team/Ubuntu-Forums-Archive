---
title: "Problems with the package manager (add/remove)"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Comandos on 2008-07-14
Hi,
I installed Linux a few days ago, and thought it's a good idea to install Java Virtual Machine, as I program in Java. I used the package manager to find the sun java program, but installation quiet, and when I tried to  open the package manager it told me there was a serious error and that I need to correct the sources.list file. I opened the file to find this:

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse






I'm new to linux so that looks like chinease to me. Would you good people help me get the problem fixed please?

Thanks a lot.

---

### Post by Ryadt on 2008-07-14
Hi. Open the terminal and type in this command```
sudo apt-get install ubuntu-restricted-extras
```
hope this solves it..:)

---

### Post by RomeReactor on 2008-07-14
Hi. If these are the complete contents of the sources.list file, then I don't see anything wrong with it. Can you post the exact error you got?

---

### Post by BGFG on 2008-07-14
Just so you know, that file is just a list of where your machine connects to to download all your software. In future you may well find yourself editing and adding to that file to give yourself acces to more 'exotic' software we have available to us...

---

### Post by Comandos on 2008-07-14
> **Ryadt said:**
> Hi. Open the terminal and type in this command```
sudo apt-get install ubuntu-restricted-extras
```
hope this solves it..:)

Hi, thanks for the speedy response. I tried the command you gave me and got this:
bash: sudu: command not found


The  exact error I have is:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by Ryadt on 2008-07-14
The command is sudo not sudu. Copy and paste the command.

---

### Post by LowSky on 2008-07-14
did you try the two commands it suggested?
```
sudo apt-get update
sudo apt-get install -f
```

---

### Post by Melindrea on 2008-07-14
Paste by right-clicking in the terminal. *tries to be a bit helpful, missed that for quite some time!*

As for the error messages... perhaps running the commands?

```
sudo apt-get update
sudo apt-get install -f
```

---

### Post by Comandos on 2008-07-14
Silly me, it work now, thanks a lot everyone!

---

