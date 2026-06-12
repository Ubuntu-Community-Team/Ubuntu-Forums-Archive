---
title: "Getting frustrated.. Synaptic help please?"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by Whisp3r on 2008-11-10
So KBuntu was giving me all kinds of problems, so I reinstalled to Ubuntu 8.10 and figured I'd just run with it a while as I learn how to Linux. After trying to install Flash, and getting a boatload of errors, here is the message I get with Synaptic:

> 
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I tried both of those commands in the root, and the message is still the same. What do I do now?

One frustrated newbie,
Whisp3r

---

### Post by taurus on 2008-11-10
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by SunnyRabbiera on 2008-11-10
also how are you trying to enter root mode?

---

### Post by jpoRS on 2008-11-10
Have you enabled restricted sources?  To do so go to Sytem>Administration>Software Sources, then make sure that the (restricted) and (multiverse) boxes are checked.

There is a way to do this in terminal, and I strongly recommend you learn how to do it, but to type it would would make it seem a lot more difficult than it is.

good luck!
jim

---

### Post by MasterSander on 2008-11-10
Your /etc/apt/sources.list is probably screwed up, try replacing it with a correct one, then run those two commands it suggested

---

### Post by Keen101 on 2008-11-10
I don't know what you mean by root mode, but those should be put in the terminal.

> sudo apt-get update

also, you probably have a broken package in synaptic. Go to the "custom filters" tab on the bottom left, then select "broken". It should list any broken packages you need to fix.

---

### Post by Whisp3r on 2008-11-10
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by Coreigh on 2008-11-10
Fix Broken Packages.

In the menu open Synaptic (System >> Administration >> Synaptic Package Manager)

From the File menu choose Edit >> Fix Broken Packages.

This should put you back on track.

Regarding the first problem of installing Flash, what were the steps you tried?

---

### Post by Whisp3r on 2008-11-10
When I run an apt-get update, this is what I get:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Coreigh on 2008-11-10
1st, you are typing ```
sudo apt-get update
``` correct?

2nd, make sure no other windows are open, This will make sure no other programs are using the sources.list file when you are trying. If the same error continues re-boot and try it again before opening any other programs.

---

### Post by Whisp3r on 2008-11-10
Hi everyone. I finally got it. Despite having everything closed (as far as I could tell), it still was giving me the same error. After rebooting, and have to run dpkg --configure -a, it started working again. What exactly did I end up doing?

Man, I have a long way to go. Thank you all for your help. This is going to be rough on an old windows fan like me to get going, but I'm dedicated and see the light. Thank you all for your help. It is very much appreciated.

---

### Post by jrothwell97 on 2008-11-10
if an installation is interrupted, dpkg --configure -a (as root, of course) completes it and clears up the mess. Quite easy, really.

---

