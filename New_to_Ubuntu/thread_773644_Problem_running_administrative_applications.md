---
title: "Problem running administrative applications"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by HHB002 on 2008-04-29
Hello Gents.
I have performed a clean install of the Hardy Heron 3 days ago.
It seems to work fine, but when running administrative applications the password box does no appear. It shows in the taskbar for a couple of seconds, but then goes away without showing on the screen.

I have tried to run update manager, a I have seen this temporary solution in another thread.
When typing in the passord I get the following error message:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: Følgende signaturer kunne ikke verificeret, da den offentlige nøgle ikke er tilgængelig: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy Release: Følgende signaturer kunne ikke verificeret, da den offentlige nøgle ikke er tilgængelig: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates Release: Følgende signaturer kunne ikke verificeret, da den offentlige nøgle ikke er tilgængelig: NO_PUBKEY 40976EAF437D05B5

Translated into english line 2: The following signatures could not be verified as the public key is not availiable.

Hopes some of you have a permanent solution.
I did not have the problem in Dapper Drake.

Brgds

---

### Post by Sjovan on 2008-04-29
update manager like in -->  sudo apt-get update ? A link to that temp. fix would be nice...

any ways... looks like you got some issues with your sources.list

```

sudo nano /etc/apt/sources.list

```
try to set it up like this --->
# Ubuntu supported packages
# GPG key: 437D05B5

comment the key with "#", so that update ignores it.

---

### Post by HHB002 on 2008-04-29
The link for the temporary solution to the password problem is here
[http://ubuntuforums.org/showthread.php?t=765301&highlight=administrative+application](http://ubuntuforums.org/showthread.php?t=765301&highlight=administrative+application)

It is just to force the password into the memory.

---

### Post by HHB002 on 2008-04-29
When I wrote 

sudo nano /etc/apt/sources.list

in a terminal window I got the error
sudo unable to resolve host 
This I solved by this workaround

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

Retyping the above code I got the following:


# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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

I cannot find the info that you are mentioning.

---

### Post by HHB002 on 2008-04-29
Problem solved.
Fund this solution.

[http://ubuntuforums.org/showthread.php?t=773637&highlight=public+key](http://ubuntuforums.org/showthread.php?t=773637&highlight=public+key)

and in the software sources window at the authentication no key were present. I pressed restore defaults and now it seems as everything is working. 

Slowly getting the hangof Ubuntu..

---

