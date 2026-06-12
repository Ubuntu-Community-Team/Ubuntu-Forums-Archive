---
title: "[SOLVED] problem while open synaptic"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by asysma on 2008-05-21
hello everyone... :KS

i have a problem while i open synaptic,this message appear..


```

E: Type '--10:22:02--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```

what happen with my synaptic??

thanks before!! :)

---

### Post by Xiong Chiamiov on 2008-05-21
Can you please post the contents of
```

cat /etc/apt/sources.list

```

---

### Post by randallecook on 2008-05-21
Did you manually add medibuntu to your list of package sources? If so, you should make sure that it was added cleanly. The error message suggests that a time value (10:22:02) is where it expects a type value to be, whatever a type value is in this context.

Randall

---

### Post by forestpixie on 2008-05-21
> **Xiong Chiamiov said:**
> Can you please post the contents of
```

cat /etc/apt/sources.list

```
Wrong list - would need to post the other

```
cat /etc/apt/sources.list.d/medibuntu.list
```

Edit - Do this to change the file andinstall medibuntu repos

Open the file for editing 

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

delete everything in it and save, while in terminal run these commands as they are, assumption is that you are using hardy - if not use gutsy line

Hardy
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Gutsy
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by asysma on 2008-05-21
here is the content

```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.
deb http://id.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://id.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse #Added by software-properties

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
# deb http://id.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://id.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
deb http://id.archive.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb-src http://id.archive.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse #Added by software-properties
deb http://packages.medibuntu.org/ gutsy free non-free
deb-src http://packages.medibuntu.org/ gutsy free non-free

```

for "cat /etc/apt/sources.list.d/medibuntu.list" content

```

--10:22:02--  http://www.medibuntu.org/sources.list.d/gutsy.list
           => `gutsy.list'
Resolving www.medibuntu.org... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

    0K                                                       100%   37.25 MB/s

10:22:05 (37.25 MB/s) - `gutsy.list' saved [223/223]

```

right,i had added manually medibuntu...but, is long time ago

---

### Post by iaculallad on 2008-05-21
Post this one too:

cat /etc/apt/sources.list.d/medibuntu.list

---

### Post by wormser on 2008-05-21
I think you can delete /etc/apt/sources.list.d/medibuntu.list, but back it up just incase.  I recall seeing a post awhile back where that was the solution.  You can always restore [Medibuntu]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f") later.

```
sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.backup
``````
sudo apt-get update
```

---

### Post by asysma on 2008-05-21
hey is working thanks to all... :KS

problem solved

---

### Post by thrash44 on 2008-05-22
Ah thanks man it worked for me...........you the best/JT

---

