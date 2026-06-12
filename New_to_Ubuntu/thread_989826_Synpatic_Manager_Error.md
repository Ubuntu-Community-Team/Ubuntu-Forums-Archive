---
title: "Synpatic Manager Error"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by you123456 on 2008-11-22
Hi all, my synaptic package manager dont seem to work. This is the error i am getting:

E: Type '--2008-11-22' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I got this error whenever i try to start the synaptic package manager from the menu.

How do i fix this? ( this might be causing my being unable to install other softwares like the pdf reader )

Best.
PS: i'm using Ubuntu 8.10, just installed last night. ;)

---

### Post by SuperSonic4 on 2008-11-22
Put a # at the very start of line 1. To do this you need to open it as root. Press alt+f2 and type
```
gksu gedit /apt/etc/sources.list
```



If this doesn't work post your /etc/apt/sources.list in the same way I outlined above

---

### Post by you123456 on 2008-11-22
HI, i've followed your instructions and i receive the following message:

Could not find the file at /apt/etc/sources.list
Please check that you typed the location correctly and try again.

is it possible to do a similar command from terminal?

---

### Post by adult swim on 2008-11-22
it should be ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by you123456 on 2008-11-22
Hi, i was browsing through the file system and i can only find the file at
/etc/apt/sources.list

When i tried to open the above file, i could see the contents of teh file. A window pops up ( window title is "Software Sources" )

I suppose i need to change something at: /etc/apt/sources.list.d/medibuntu.list ?
SInce that's what my error pointed out?

Best Regards,
EUgene

---

### Post by you123456 on 2008-11-22
> **adult swim said:**
> it should be ```
gksudo gedit /etc/apt/sources.list
```
Hi, yes, i tried the above and i managed to open the file.

However, after adding in a "#" in teh first line, the synaptic manager still couldnt work.

Any ideas?

BEst.

---

### Post by you123456 on 2008-11-22
Here's my file:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

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

### Post by adult swim on 2008-11-22
from a terminal run ```
cat /etc/apt/sources.list.d/medibuntu.list
``` and paste what it returns here

---

### Post by you123456 on 2008-11-22
> **adult swim said:**
> from a terminal run ```
cat /etc/apt/sources.list.d/medibuntu.list
``` and paste what it returns here

I got teh following:

--2008-11-22 14:16:28--  [http://medibuntu.org/sources.list.d/hardy.list](http://medibuntu.org/sources.list.d/hardy.list)
Resolving medibuntu.org... 87.98.242.110
Connecting to medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]
Saving to: `hardy.list'

     0K                                                       100% 14.9M=0s

2008-11-22 14:16:29 (14.9 MB/s) - `hardy.list' saved [226/226]


Best Regards.

---

### Post by you123456 on 2008-11-22
synaptic manager still couldnt work after running:

cat /etc/apt/sources.list.d/medibuntu.list

---

### Post by 3rdalbum on 2008-11-22
For some strange reason, the commands that the Medibuntu website gave you have put the wrong contents into your apt sources.

Open the affected file:

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

And paste this in:

```
## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ intrepid free non-free
deb-src http://packages.medibuntu.org/ intrepid free non-free
```

Save changes and go into Synaptic Package Manager, and click Reload. Everything should work now.

---

### Post by you123456 on 2008-11-22
hey thanks, it worked!  Thank u all!

---

