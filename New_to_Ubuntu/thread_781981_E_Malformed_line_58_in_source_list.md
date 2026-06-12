---
title: "E: Malformed line 58 in source list"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by thabo on 2008-05-04
Please help.
I tried to install Defcon from these deb files : [http://download.introversion.co.uk/defcon/linux/contrib/ubuntu-feisty/dists/feisty/main/binary-i386/](http://download.introversion.co.uk/defcon/linux/contrib/ubuntu-feisty/dists/feisty/main/binary-i386/)  .
Unfortunately I now get the error :E: Malformed line 58 in source list /etc/apt/sources.list (dist parse) 

I think my source list is the following:

#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb [http://download.introversion.co.uk/defcon/linux/contrib/ubuntu-feisty/](http://download.introversion.co.uk/defcon/linux/contrib/ubuntu-feisty/) feisty
main

Thanks in advance.

---

### Post by PeterJS on 2008-05-04
I didn't count, but eyeballing it I'd bet the bottom line is 58, looks like you got an extra line break in that last entry. Also you might want to find another repository, Fiesty is quite old at this point (18 months old).

Also for an out of date repository that hasn't been updated in 10 months with only two packages in it, you might be better of just grabbing the two debs out of there and installing them with gdebi.

[http://download.introversion.co.uk/defcon/linux/contrib/ubuntu-feisty/dists/feisty/main/binary-i386/defcon-sounds_1.42-1_all.deb](http://download.introversion.co.uk/defcon/linux/contrib/ubuntu-feisty/dists/feisty/main/binary-i386/defcon-sounds_1.42-1_all.deb)
And
[http://download.introversion.co.uk/defcon/linux/contrib/ubuntu-feisty/dists/feisty/main/binary-i386/defcon_1.42-2_i386.deb](http://download.introversion.co.uk/defcon/linux/contrib/ubuntu-feisty/dists/feisty/main/binary-i386/defcon_1.42-2_i386.deb)

---

### Post by y-lee on 2008-05-04
It looks like you are trying to install a feisty package on a hardy system and your sources.list file got messed up somehow.

this is a system file so you can not edit it or delete it unless you are root or a super user. First we make a backup copy just in case. (all code below here is typed or copied and pasted into the terminal)

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
```

Now we open it in gedit as super user so we can edit it:

```
gksudo gedit /etc/apt/sources.list
```

and delete the line
> deb [http://download.introversion.co.uk/d...ubuntu-feisty/](http://download.introversion.co.uk/d...ubuntu-feisty/) feisty
main

now close gedit, and your sources list file should be fixed.


Now update the repos

```
sudo apt-get update
```


If this command works Synaptic should be ok.

---

### Post by thabo on 2008-05-04
Thanks a lot Peter.
I deleted it and everything is back to normal.
Will look for another suppository.:)

---

### Post by thabo on 2008-05-04
Thanks Y-lee.
Updated as well.

Wow I am really impressed with the fast replies on the ubuntu forum!!

---

### Post by arpanaut on 2008-05-04
Might I recommend Preparation H...
as in HARDY:grin:

---

### Post by ace007 on 2008-05-04
when did we start talking about suppositories?

---

### Post by PeterJS on 2008-05-04
Good news bad news, looking at the Defcon web page ([http://www.everybody-dies.com/downloads/index.html](http://www.everybody-dies.com/downloads/index.html)) it would appear that v1.42 is the current linux version, so the v1.42-2 deb I linked to up above isn't as out of date as it's age would suggest.

---

### Post by jasonsexton on 2008-05-07
I have a similar problem.  I did an upgrade to Hardy lat week and everything seemed to be fine until I tried to run synaptic package manager.  Any help would be appreciated. I get this error message:

E: Malformed line 37 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by Xiong Chiamiov on 2008-05-07
Well, take a look at line 37.  If you don't see anything wrong, then post the output of that line for us.

---

