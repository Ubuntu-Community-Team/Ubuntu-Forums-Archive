---
title: "Can't Activate hardy-security!"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by Tibco on 2008-07-04
When i go to system>admin>software sources and then go to the updates tab. I have all the updates checked under "ubuntu updates" except for hardy-security. When i try and check it, it dosnt work! I click on the box next to where it gives the description and it still stays blank. Anyone have any idea why?

---

### Post by sayakb on 2008-07-04
```
sudo gedit /etc/apt/sources.list
```Navigate to the line:
```
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
```And remove the # from the front. If this line is not present, add it.
Then do:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Tibco on 2008-07-04
still dosnt seem to work...i went to sources.list, uncommented the lines, did the updates and upgrade (BTW, nothing upgraded) also, when i go back to the software sources screen, it is still unchecked...

---

### Post by Tibco on 2008-07-04
anyone? ive double checked everything, ive updated, and i still cant get the darn thing to put a check mark next to hardy security updates!


PS, could my authentcation keys be wrong? might this be causing the problems?

---

### Post by Tibco on 2008-07-04
ok please, im desprate now, can anyone just post their sources.list file here and i can copy it down? i think i may have played around too much with my own to fix it back...if someone could post their sources.list, that would save my life!

---

### Post by kansasnoob on 2008-07-04
> **Tibco said:**
> ok please, im desprate now, can anyone just post their sources.list file here and i can copy it down? i think i may have played around too much with my own to fix it back...if someone could post their sources.list, that would save my life!

I'd be glad to if I knew exactly what command to run, but I suck at command line stuff.

While looking for documentation about what command to run I ran across this:

[http://www.howtoforge.com/generate_sources.list_with_source_o_matic](http://www.howtoforge.com/generate_sources.list_with_source_o_matic)

I've generally found Howtoforge to be quite reliable.

---

### Post by ibuclaw on 2008-07-04
There are no upgrades because hardy-updates holds the newest versions with the most recent security fixes patched in, there is absolutely nothing to worry about.

Regards
Iain

---

### Post by deleau on 2008-07-05
> **tinivole said:**
> There are no upgrades because hardy-updates holds the newest versions with the most recent security fixes patched in, there is absolutely nothing to worry about.

Regards
Iain

Well, I have the same problem as described in the first post, I've tried editing my sources.list (and there is no # before the "security line").

At the same time some packages are now described as "local or obsolete" in synaptic (gvfs, python2.5 for example).

The checkbox in synaptic for the security update still remains inapplicable.

Hope this can help to find a solution.

Andrea

---

### Post by philinux on 2008-07-05
Post the out put of

```
cat /etc/apt/sources.list
```

My bet is the sources are active it's just the box that wont tick. This is how intrepid is at the moment.

---

### Post by deleau on 2008-07-05
I tried changing from [http://security.ubuntu](http://security.ubuntu) ... hardy-security main ...
to [http://archive.ubuntu](http://archive.ubuntu) ... hardy-security main ...

It seemed it updated hardy security packages (but I still can't imagine why some packages are now "local or obsolete").

If I try to change it from sinaptic options it get back to "can't activate" state.

I don't think it wil be useful but here is my sources.list
```

deleau@deleau-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
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
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse #Added by software-properties
# deb-src http://it.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner


#Dell
deb http://ppa.launchpad.net/dell-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/dell-team/ubuntu hardy main

# Medibuntu
deb http://packages.medibuntu.org/ hardy free non-free

#Ubuntu-Tweak
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu hardy main

## uPure64 Repository
deb http://download.tuxfamily.org/upure64/ hardy-upure64 main experimental
deb-src http://download.tuxfamily.org/upure64/ hardy-upure64 main experimental

#Amaraok-nightly
deb http://ppa.launchpad.net/project-neon/ubuntu hardy main

deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe #Added by software-properties

deb http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe

```

---

### Post by philinux on 2008-07-05
The last line shows you've got security repo's active.

---

### Post by deleau on 2008-07-05
> **philinux said:**
> The last line shows you've got security repo's active.

I know.

But I had to change the address... and some packages are still there as "oblolete or local" in synaptic.

---

### Post by sayakb on 2008-07-05
Packages are listen in "local or obsolete" if they don't exist in the repository. This means that either \

a) it was never there, and you installed it from somewhere else (downloaded, or from a repository that
is no longer in your sources.list) 

or 

b) it was in the repository, but isn't anymore, usually because it has been replaced with laters version with a different package name.

As long as you don't need them for anything you can remove them.

---

### Post by Me! on 2008-07-05
> **philinux said:**
> Post the out put of

```
cat /etc/apt/sources.list
```My bet is the sources are active it's just the box that wont tick. This is how intrepid is at the moment.

try this
```
sudo pico /etc/apt/sources.list
```

You must change this file first. If not you will not able to get the Update !

I hope that help you

---

### Post by Tibco on 2008-07-06
ok i fixed this problem. go [http://tuxicity.wordpress.com/sourceslist-for-ubuntu-hardy-heron-810/]("http://tuxicity.wordpress.com/sourceslist-for-ubuntu-hardy-heron-810/") there and copy and past that into your sources.list file. and then replace the bottom 2 with "archive" instead of "security". then double check to make sure all of your sources start with "archive.ubuntu...." after this my problem was fixed.

---

