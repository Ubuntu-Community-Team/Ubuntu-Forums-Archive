---
title: "Can't install VLC"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by texastrey1836 on 2011-11-05
Hello all:
New install of 64-bit Ubuntu 11.10 on a Win7/Ubuntu dual-boot Toshiba. I'm trying to install VLC and I get the following error:
Package dependencies can not be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
I've seen this error in a few other posts but don't know enough about Ubuntu to navigate the various ways to try to fix the problem. Can anyone help?

---

### Post by Bodsda on 2011-11-05
> **texastrey1836 said:**
> Hello all:
New install of 64-bit Ubuntu 11.10 on a Win7/Ubuntu dual-boot Toshiba. I'm trying to install VLC and I get the following error:
Package dependencies can not be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
I've seen this error in a few other posts but don't know enough about Ubuntu to navigate the various ways to try to fix the problem. Can anyone help?

Hi,

Please first try updating your current packages, then retry the vlc install. If this still fails, please post all of the terminal contents as it will tell us which packages it requires.

```

sudo apt-get update && sudo apt-get upgrade

```

```

sudo apt-get install vlc

```

Thanks,
Bodsda

---

### Post by texastrey1836 on 2011-11-05
Here's what happens when I try to update and upgrade:
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


....also having a problem downloading problems from the Software Center. I am told that the program is not in my software sources.

---

### Post by Bodsda on 2011-11-05
> **texastrey1836 said:**
> Here's what happens when I try to update and upgrade:
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


....also having a problem downloading problems from the Software Center. I am told that the program is not in my software sources.

Ok, that is probably the main problem here, please paste the contents of the '/etc/apt/sources.list' file

```

cat /etc/apt/sources.list

```

Thanks,
Bodsda

---

### Post by texastrey1836 on 2011-11-05
Here you go. Thanks for your help.

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

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

### Post by Bodsda on 2011-11-05
Try opening 'software sources' by searching for it through the unity search.
Then change the download from server to something else, click close, then rerun the update
```

sudo apt-get update

```

Thanks,
Bodsda

---

### Post by texastrey1836 on 2011-11-05
Bingo! That was it. Thank you so very much. It seems to be downloading fine now.

---

### Post by Bodsda on 2011-11-05
> **texastrey1836 said:**
> Bingo! That was it. Thank you so very much. It seems to be downloading fine now.

No problem, it seems there may be a problem with the US repositories. If that is the case, it is likely to be resolved soon, you could try switching the download location back again in a few days, or just leave it as is.

Glad I could help,
Bodsda

---

