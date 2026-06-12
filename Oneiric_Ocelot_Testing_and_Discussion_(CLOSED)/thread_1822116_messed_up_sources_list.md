---
title: "messed up sources list"
date: 2011-08-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mick222 on 2011-08-10
I upgraded oneric from alpha 2 to alpha3 by reinstalling from usb.
My sources list has been messed up "lots of duplicates" This instalation is on a partition i've been upgradeing from lucid is there an easy way to get a clean sources list i have no ppas that i need and am a bit afraid i will break my system if i mess to much with it.

---

### Post by haqking on 2011-08-10
> **mick222 said:**
> I upgraded oneric from alpha 2 to alpha3 by reinstalling from usb.
My sources list has been messed up "lots of duplicates" This instalation is on a partition i've been upgradeing from lucid is there an easy way to get a clean sources list i have no ppas that i need and am a bit afraid i will break my system if i mess to much with it.

easiest way is to edit the sources list with system>adminsistration>update manager and choose settings then remove the ticks from the duplicate entries in the list.

or you can:

gksudo gedit /etc/apt/sources.list

remember to use gksudo and not sudo as i have shown.

then any dupliacte entries place a # at the beginning of the line, that way you are not removing anything. do it ones by one and if any problesm all you need to do it is remove the # again to make it work.
at all times pay attention to what you are doing and dont rush

---

### Post by mick222 on 2011-08-10
I tried using software sorces but it doesn't show the duplicates.
I am not to confident of editing the sources list with gedit I hoped i would be able to find a copy of a clean sources list rename the old one and use that.

---

### Post by Harry33 on 2011-08-10
Why don't you just print the contents of your "messed up" sources.list here.
We will fix it then.

---

### Post by haqking on 2011-08-10
> **mick222 said:**
> I tried using software sorces but it doesn't show the duplicates.
I am not to confident of editing the sources list with gedit I hoped i would be able to find a copy of a clean sources list rename the old one and use that.

this is your chance to get confident.

use what you are saying to your advantage.

make a backup of the one you have now, do your editing as i described and if you mess it up then you have a back up dont you ;-)

---

### Post by mick222 on 2011-08-10
heres the file
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Alpha i386 (20110803.1)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Alpha i386 (20110531.1)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric restricted main
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric restricted main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates restricted main
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates restricted main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security restricted main
deb-src http://security.ubuntu.com/ubuntu oneiric-security restricted main
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports restricted universe multiverse main
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports restricted universe multiverse main

deb http://security.ubuntu.com/ubuntu oneiric-security restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security restricted

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
```

---

### Post by ajgreeny on 2011-08-10
You could also try using [Sources List Generator]("http://repogen.simplylinux.ch/")  which when you fill in the appropriate drop down boxes will produce for you a default sources.list file which you can copy and use to replace the current one.

Keep the old one as a backup in case it all goes to worms, and you can then restore it if needed.

---

### Post by lucazade on 2011-08-10
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Alpha i386 (20110731)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://archive.ubuntu.com/ubuntu/ oneiric universe
deb http://archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

---

### Post by mick222 on 2011-08-10
I'll try sources list generator sounds like what i was looking for.

---

### Post by mick222 on 2011-08-10
Ended up using lucozades sources list I didn't like the one produced by sources list generator. Seems to be working after a reboot.Thanks to everyone who helped.

---

### Post by lucazade on 2011-08-10
> **mick222 said:**
> Ended up using lucozades sources list I didn't like the one produced by sources list generator. Seems to be working after a reboot.Thanks to everyone who helped.

you're welcome.
mark the thread as solved if everything is ok now.

---

