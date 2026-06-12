---
title: "Duplicate sources"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by Drowz0r on 2012-04-11
Hello all

I'm in Ubuntu 11.10

When ever I install or update something I get this in my terminal:

```
Reading state information... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```
Is it a problem? It happens when I run apt-get update, then when I run it again it's not there but it comes back when I do something else.

---

### Post by mprice on 2012-04-11
Just remove whichever one your not using, are you running a 32-bit or 64-bit Ubuntu? 

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by Drowz0r on 2012-04-12
> **mprice said:**
> Just remove whichever one your not using, are you running a 32-bit or 64-bit Ubuntu? 

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Hello. Thanks for your reply.

I'm running 64 bit.

I don't know which I am and which I'm not using tbh?

At some point I was told to use them all by different applications, otherwise I wouldn't have added them. Looking at the sources, they're all different anyway so there doesn't appear to be a "duplicate".

---

### Post by lolpenguin on 2012-04-12
Can you post the output of
```
cat /etc/apt/sources.list
```

---

### Post by Drowz0r on 2012-04-12
Here you go buddy:

```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

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

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

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
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
```

Is there something in there I should be looking for? It doesn't make much sense to me, regrettably :c

---

### Post by plucky on 2012-04-12
> Is there something in there I should be looking for?

Two **partner** repositories that look the same.That list looks ok.

You could disable all the lines with deb-src at the beginning as those are the repositories for the source code,which you probably don't need.


What does ```
cat /etc/apt/sources.list.d/*.list
``` show you?

---

### Post by lolpenguin on 2012-04-13
That list is perfectly fine. You've probably doubled up your partner in some source that something told you to add.

---

