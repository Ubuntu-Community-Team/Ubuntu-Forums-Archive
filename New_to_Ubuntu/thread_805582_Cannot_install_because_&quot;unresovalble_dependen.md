---
title: "Cannot install because &quot;unresovalble dependencies&quot;"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Juhla Mokka on 2008-05-24
Hi

I want to backup my files, and the Ubuntu help suggests installing Hubackup.
Add/remove applications does not let me install it, and when I go to Synaptic package manager this comes up:

[INDENT][COLOR="Navy"]Could not mark all packages for installation or upgrade

The following packages have unresovalble dependencies. Make sure that all required repositories are added and enabled in the preferences.

hubackup:
 Depends: cdrecord  but it is not installable
 Depends: mkisofs  but it is not installable[/COLOR][/INDENT]

What does this mean? How can I install Hubackup?

Thanks :)

---

### Post by shifty_powers on 2008-05-24
[http://packages.ubuntu.com/gutsy/cdrecord](http://packages.ubuntu.com/gutsy/cdrecord)

[http://packages.ubuntu.com/gutsy/mkisofs](http://packages.ubuntu.com/gutsy/mkisofs)


packages.ubuntu.com can be a very handy website. http version of the repo's ;)

those two links will give you download links to those two packages and their dependencies.

seems as if one of two has been taken out of the hardy repo's, and they both depend on the other to installl ;)

---

### Post by PmDematagoda on 2008-05-24
Can you post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by Juhla Mokka on 2008-05-24
Hi and thanks!

here is the code

cat /etc/apt/sources.list
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy universe main
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

Shifty, I'll check your links too.

---

### Post by PmDematagoda on 2008-05-24
There is the reason, your sources are commented out.

Open Software Sources in System>Administration>Software Sources and then enable everything in the Ubuntu Software tab, once that is done, close the window and reload the sources list as suggested, after that is finished your problem should be solved.

---

### Post by Juhla Mokka on 2008-05-24
Wow! Solved! So simple. Installed with no problem. Thanks a million!

---

