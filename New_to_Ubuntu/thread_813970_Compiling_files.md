---
title: "Compiling files"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-05-31
Hy all

A noob question:if I started to compile a file, but for some reason I want to stop it can I just close the terminal?Will I mess up my system doing so?

---

### Post by shifty_powers on 2008-05-31
nope, your system will be fine, but you would have to restart compiling if you still wanted the program...

---

### Post by Dougie187 on 2008-05-31
You can also use ctrl+c to stop it. Or if you want to start it back up later you can use ctrl+z and then fg to return to it. (The terminal has to be open the whole time between the ctrl+z and the fg)

---

### Post by Joeb454 on 2008-05-31
What are you compiling if I may ask?

But as shifty_powers says - it wouldn't do anything dramatic, it might throw out a warning or possibly error, but your system wouldn't be damaged :)

---

### Post by Troll_the_Great on 2008-05-31
Thx for your answer.I wanted to install the latest wine, and I downloaded the source code and started to compile it(it still runs).Only after that I saw that I can find it in a debian package for my Ubuntu.The compiling takes for ever, so that is why I asked.So are u sure that nothing will happen to my system?

---

### Post by Joeb454 on 2008-05-31
Positive it wouldn't. And the Wine repo is the way to go :) There's a guide on the Wine website on how to add it :)

---

### Post by shifty_powers on 2008-05-31
system>administration>synaptic>settings>repositories>third party software>add

and then see screenshot ;)

---

### Post by Troll_the_Great on 2008-05-31
Thx.What other useful repositories do you have?

---

### Post by shifty_powers on 2008-05-31
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe

# Remastersys
deb http://www.remastersys.klikit-linux.com/repository remastersys/
deb http://ppa.launchpad.net/gilir/ubuntu hardy main universe
```

is my list of repositories ;)

the ones with # before them aren't used ;)

nad be careful about blindly adding them to your list

---

### Post by Joeb454 on 2008-05-31
I find that the backport's repo is quite a nice one to have :)

And I've enabled hardy-proposed a couple of times as well ;)

---

