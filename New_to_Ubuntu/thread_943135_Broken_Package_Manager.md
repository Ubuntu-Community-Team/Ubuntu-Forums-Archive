---
title: "Broken Package Manager"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by hormone on 2008-10-09
Hi,

Unfortunately my first post here is because I've broken the package manager :(

I've recently started dual-booting Kubuntu 8.04 with Vista with a view to switching permanently provided I can get the last couple of things to work ie my fingerprint scanner and a VM to run Windows so that I can run a couple of legacy applications. Anyway enough about me...

I'm very much a noob, so please speak to me in one syllable words.

When I open up Adept I get:

> The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

This happened after I tried to add a 3rd party repo to help with getting the fingerprint scanner to work. When I go to Terminal and type:

> cat/etc/apt/sources.list

I get:

> deb cdrom:[Kubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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
echo -e "# Fingerprint reader support (fprint)\ndeb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse"Fingerprint reader support (fprint)\ndeb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse"

When I tried:

> sudo apt-get -f install

I get

> E: Type 'echo' is not known on line 56 in source list /etc/apt/sources.list

OK, so now I know what the problem is. When I try:

> gksudo gedit /etc/apt/sources.list

I get nothing. The machine thinks for a bit and then I just a new CLI prompt.

Like I said, I'd have preferred my first post in the Ubuntu community to have been a happier, however, I'd really appreciate any help on this one...

---

### Post by SunnyRabbiera on 2008-10-09
hmm, did you try sudo apt-get update and see if it spits out errors?

---

### Post by bwang on 2008-10-09
If your using KDE, you won't have gedit installed. Try
```
sudo nano /etc/apt/sources.list
```

---

### Post by hormone on 2008-10-09
Yeah. Unfortunately I get the same error:

> E: Type 'echo' is not known on line 56 in source list /etc/apt/sources.list

---

### Post by hormone on 2008-10-09
OK, So that gets me:

>   GNU nano 2.0.7          File: /etc/apt/sources.list

deb cdrom:[Kubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701.2)]/ hardy mai$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
                               [ Read 58 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell


What's next??

---

### Post by aysiu on 2008-10-09
Paste this command into the terminal: ```
kdesu kate /etc/apt/sources.list
``` and then get rid of this part of the sources.list file: ```
echo -e "# Fingerprint reader support (fprint)\ndeb http://ppa.launchpad.net/madman2k/ubuntu hardy main restricted universe multiverse"Fingerprint reader support (fprint)\n
``` Then save and exit and ```
sudo apt-get update
```

---

### Post by hormone on 2008-10-09
Problem solved inside 20 minutes. You guys rock:guitar:

I'm 'experimenting' with the guidance provided here (obviously didn't get very far yet):

[http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)

What's the correct part of 

> echo -e "# Fingerprint reader support (fprint)\ndeb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse" | sudo tee -a /etc/apt/sources.list


to use when adding this repo?

Oh and how do I mark as solved?

---

### Post by aysiu on 2008-10-09
I think you're supposed to paste that command into the terminal, not into the /etc/apt/sources.list file itself.

---

