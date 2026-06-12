---
title: "oooops"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by meatlegs on 2008-05-28
Hey all,
I was trying to install some restricted extras (which i already had apparently) as my dvd's would not play back.
So I tried a tutorial that said to 'comment out all of the "multiverse" lines' from my sources list. Once I did that I get this:

Type 'Line' is not known on line 34 in source list /etc/apt/sources.list

I cannot run get-update anymore either

i think I broke it!
help!!!

Here's what my source list reads:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 

Line commented out by installer because it failed to verify:
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
Line commented out by installer because it failed to verify:
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
Line commented out by installer because it failed to verify:
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
Line commented out by installer because it failed to verify:
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main

---

### Post by HotShotDJ on 2008-05-28
> **meatlegs said:**
> i think I broke it!
help!!!Uh.. restore the backup of the original file that I'm sure you made before messing with an important system file.

PS; where is this tutorial?  I'd like to read it to find out what you were trying to accomplish -- commenting out Multiverse?  WTF?

---

### Post by Bubba64 on 2008-05-28
> **meatlegs said:**
> Hey all,
I was trying to install some restricted extras (which i already had apparently) as my dvd's would not play back.
So I tried a tutorial that said to 'comment out all of the "multiverse" lines' from my sources list. Once I did that I get this:

Type 'Line' is not known on line 34 in source list /etc/apt/sources.list

I cannot run get-update anymore either

i think I broke it!
help!!!

[http://www.ubuntux.org/node/71](http://www.ubuntux.org/node/71)
If I under stand you this should help got it via Google with multiverse linux

---

### Post by The Titan on 2008-05-28
> **meatlegs said:**
> Hey all,
I was trying to install some restricted extras (which i already had apparently) as my dvd's would not play back.
So I tried a tutorial that said to 'comment out all of the "multiverse" lines' from my sources list. Once I did that I get this:

Type 'Line' is not known on line 34 in source list /etc/apt/sources.list

I cannot run get-update anymore either

i think I broke it!
help!!!

can you give the output from "cat /etc/apt/sources.list" please

---

### Post by marks_linux on 2008-05-28
just undo what you did to the file ;)

Or paste it up here and someone will help you out I'm sure.

My hunch is you removed a # character on a line that doesn't begin http:

---

### Post by The Titan on 2008-05-28
comment out this line

```

Line commented out by installer because it failed to verify:

```

and all is well

---

### Post by meatlegs on 2008-05-28
wow thanks for the fast response guys
so i should put the # symbol in front of all those lines Titan?

---

### Post by meatlegs on 2008-05-28
here's that stupid tutorial hotshot:
[https://answers.launchpad.net/ubuntu/+question/21520](https://answers.launchpad.net/ubuntu/+question/21520)

---

### Post by Bubba64 on 2008-05-28
> **meatlegs said:**
> wow thanks for the fast response guys
so i should put the # symbol in front of all those lines Titan?

Here is mine but it is all Hardy

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main


deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main

---

### Post by Bubba64 on 2008-05-28
Mine also contains the launchpad address for the newest FF 3 release if you want that I will post it even though you using gutsy.

---

### Post by HotShotDJ on 2008-05-28
> **meatlegs said:**
> here's that stupid tutorial hotshot:
[https://answers.launchpad.net/ubuntu/+question/21520](https://answers.launchpad.net/ubuntu/+question/21520)Yep.. you said that correctly... stupid. :)  All users have to do is use the tools provided.  System --> Administration --> Software Sources and just check off what you want without risking mangling the system files.

---

### Post by The Titan on 2008-05-28
all the ones that dont have them, yes

---

### Post by meatlegs on 2008-05-28
ok i think that did it, thanks all!!!

---

### Post by tylerspaska on 2008-05-28
Do just as Titan says. Place a # in front of all the lines that start with 'Line'. 

Your message is telling you exactly what the problem is. Look at it a little closer. It is saying that the 34th line of your sources list is trying to add something called "Line" (as opposed to deb) and that this thing called "Line" is not known to apt. Does that make sense?

As a side note, I would also comment out the cdrom on the first line, unless you are actually relying on the Ubuntu CD to add and remove programs (you probably aren't if you have a moderate internet connection).

---

### Post by The Titan on 2008-05-28
Np, but for future reference, this is a good way to do the same thing you did with a GUI :)

> **HotShotDJ said:**
> Yep.. you said that correctly... stupid. :)  All users have to do is use the tools provided.  System --> Administration --> Software Sources and just check off what you want without risking mangling the system files.

---

