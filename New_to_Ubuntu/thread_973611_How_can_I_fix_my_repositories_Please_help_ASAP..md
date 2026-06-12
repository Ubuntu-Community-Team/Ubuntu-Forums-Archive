---
title: "How can I fix my repositories? Please help ASAP."
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Narcoleptic_Insomniac on 2008-11-06
So I'm not sure what happened. But I can't install anything via terminal anymore. I haven't used Ubuntu in a while and I remember that when I tyope "sudo apt-get update", it would update all my repositories and provide me with a list of all them. However, it does not do that anymore. All it does it say "Reading package lists....Done". So I am figuring something happened to a crucial file. Please help, I really need to get this stuff working again.

---

### Post by taurus on 2008-11-06
What does your /etc/apt/sources.list look like then?  Open a terminal and post the contain of your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by fooman on 2008-11-06
what happens when you go to system > administration > software sources?

if it opens...on the ubuntu software tab,  make sure the first 4 choices are checked.  on the updates tab,  check off the top 2.

close and try sudo apt-get update again.

---

### Post by Narcoleptic_Insomniac on 2008-11-06
> **taurus said:**
> What does your /etc/apt/sources.list look like then?  Open a terminal and post the contain of your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

When I entered that in terminal, it returned this to me...

```

# 
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner


```

---

### Post by nhasian on 2008-11-06
all of the sources are commented out, thats why it is not searching anywhere.  remove the # from the lines that have # deb.  the first two are for the cdrom

---

### Post by frankleeee on 2008-11-06
Do you have the CD ticked off in software sources and everything else you want accessed ticked on

---

### Post by Narcoleptic_Insomniac on 2008-11-06
Ok. Well the thing is I'm trying to figure out how to install from source code and I've been following this [guide]("http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html"), but it won't let me install "build-essentials".

It's really frustration because all I want to do is play a damn game.

---

### Post by Narcoleptic_Insomniac on 2008-11-06
> **frankleeee said:**
> Do you have the CD ticked off in software sources and everything else you want accessed ticked on

I do now.

---

