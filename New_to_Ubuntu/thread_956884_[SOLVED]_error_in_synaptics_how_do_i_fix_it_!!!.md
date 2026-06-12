---
title: "[SOLVED] error in synaptics how do i fix it !!!"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by nnamdi on 2008-10-23
i have issues when trying to update or installing things get errors on duplicated source list

```

W: Duplicate sources.list entry http://security.ubuntu.com hardy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com hardy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com hardy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com hardy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by drs305 on 2008-10-23
Please post the contents of your sources.list and we can help you sort things out (ALT-F2 to open a terminal window):
```

cat /etc/apt/sources.list

```

If you would rather try to take care of it yourself, eliminating duplicate lines:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksudo gedit /etc/apt/sources.list

```

Once you have made the changes and saved the file:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by HittingSmoke on 2008-10-23
> **nnamdi said:**
> i have issues when trying to update or installing things get errors on duplicated source list

```

W: Duplicate sources.list entry http://security.ubuntu.com hardy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com hardy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com hardy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com hardy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

You should be able to just delete the duplicate entries by opening the sources.list file
```
sudo gedit /etc/apt/sources.list
```
and finding and deleting the specified repo entries

Just make sure they're actually duplicates first.

---

### Post by nnamdi on 2008-10-23
this my source list after running 

```

/etc/apt/sources.list

```

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://ng.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe

```

---

### Post by drs305 on 2008-10-23
You can delete the last line, which duplicates other lines. Replace your entire sources.list with:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://ng.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

The last line in sources.list was removed as a duplicate which referenced the four repositories.

---

### Post by nnamdi on 2008-10-23
thank drs305 it worked out

---

