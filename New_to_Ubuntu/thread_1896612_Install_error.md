---
title: "Install error"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by Zvanochek on 2011-12-17
I've been using Ubuntu (11.10) for 7 days; I am impressed that I haven't been able to break it earlier...

I went to install some software through the software center, and it came up with this error message. Could someone guide me through the fix, and if possible, explain how I managed to break it so I can avoid it in future?

Thanks

Zvanochek

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

---

### Post by BC59 on 2011-12-17
Open a terminal with ALT+CTRL+T and run this:

```
sudo apt-get install ubuntu-restricted-extras
```

If you have an error message post it here.

---

### Post by Zvanochek on 2011-12-17
> **BC59 said:**
> Open a terminal with ALT+CTRL+T and run this:

```
sudo apt-get install ubuntu-restricted-extras
```

If you have an error message post it here.

This is going to sound really really stupid, but a liscence agreemnet box has popped up...how do I continue? I've tried clicking on OK and typing it, but nothing...:oops:

---

### Post by BC59 on 2011-12-17
> **Zvanochek said:**
> This is going to sound really really stupid, but a liscence agreemnet box has popped up...how do I continue? I've tried clicking on OK and typing it, but nothing...:oops:

You should only hit enter and work...but sometimes is tricky.

---

### Post by Elfy on 2011-12-17
Tab to the OK then enter.

---

### Post by Zvanochek on 2011-12-17
> **BC59 said:**
> You should only hit enter and work...but sometimes is tricky.

Enter is not working...i've attached a copy of the screen I get.

---

### Post by Zvanochek on 2011-12-17
> **forestpiskie said:**
> Tab to the OK then enter.

Oh yeah, that would do it....cheers!

---

### Post by Zvanochek on 2011-12-17
It appears to have installed with no errors, although it did provide the following warning:

ldconfig deferred processing now taking place
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by BC59 on 2011-12-17
Can you post the result of this from a terminal?

```
gksudo gedit /etc/apt/sources.list
```

when opens the file, copy and paste here

---

### Post by Zvanochek on 2011-12-17
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

---

### Post by BC59 on 2011-12-17
Looks like the sources:

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
 
are duplicated

Comment with hash the 2 last lines like this
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

Save, close and run
```

sudo apt-get update
```

---

### Post by Zvanochek on 2011-12-17
> **BC59 said:**
> Looks like the sources:

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
 
are duplicated

Comment with hash the 2 last lines like this
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

Save, close and run
```

sudo apt-get update
```

Now says

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

---

### Post by BC59 on 2011-12-17
Run this:

```
gpg --keyserver keyserver.ubuntu.com --recv 5A9A06AEF9CB8DB0

and then

gpg --export --armor 5A9A06AEF9CB8DB0 | sudo apt-key add -
```

---

### Post by Zvanochek on 2011-12-18
> **BC59 said:**
> Run this:

```
gpg --keyserver keyserver.ubuntu.com --recv 5A9A06AEF9CB8DB0

and then

gpg --export --armor 5A9A06AEF9CB8DB0 | sudo apt-key add -
```

That seems to have done it. Thank you very much for your help.

---

