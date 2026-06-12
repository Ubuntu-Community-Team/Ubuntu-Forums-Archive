---
title: "[SOLVED] Can't install testdisk"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by hwatari on 2008-11-21
I'm trying to install testdisk with,

sudo apt-get install testdisk

but I get,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk

Does anybody have any idea as to why ?
Thank you very much.
Hiromichi

---

### Post by drs305 on 2008-11-21
Do you have the *universe* repository enabled?

Synaptic (or System, Admin, Software Sources), Settings, Repositories, Ubuntu Software, community-maintained (universe).

---

### Post by hwatari on 2008-11-21
> **drs305 said:**
> Do you have the *universe* repository enabled?

Synaptic (or System, Admin, Software Sources), Settings, Repositories, Ubuntu Software, community-maintained (universe).

Hi drs305,
Thank you for your reply.
Yes I do, but I think it is trying to pull that out of edgy-updates which can't be located and I don't know what to do.
Hiromichi

---

### Post by drs305 on 2008-11-21
Which version are you running, and if you post your sources.list we can take a look at it:
```

cat /etc/apt/sources.list

```

If you are running any of the recent versions (i.e. not edgy), you don't want anything in your sources.list that says "edgy". You can put a comment symbol # in front of the line if you have another identical line with your version (such as gutsy, hardy, intrepid).

---

### Post by hwatari on 2008-11-21
Thanks here is the output,

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by hwatari on 2008-11-21
P.S.
I believe the version is Ubuntu 6.10

---

### Post by drs305 on 2008-11-21
> **hwatari said:**
> P.S.
I believe the version is Ubuntu 6.10

That would be your problem. Edgy "died" in April 08 and is no longer supported and thus the repositories are not available to update any existing or add any uninstalled packages.

You best option would be to do a new install of either Hardy Heron LTS (long term support) or Intrepid Ibex. Dapper is also still available although it's been around a long time.

Here is some info on the Release Dates:
[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

I don't know if testdisk is version specific, but I doubt it and you can probably download it from a variety of online-sources - just not the repositories! It is on a lot of the 'recovery' type disks, including the "systemrescuecd".

---

### Post by hwatari on 2008-11-21
drs305,
Can you tell me how I do a new install of Hardy Heron LTS since I installed Ubuntu from CD that came with a book ?
Thanks,
Hiromichi

---

### Post by drs305 on 2008-11-21
> **hwatari said:**
> drs305,
Can you tell me how I do a new install of Hardy Heron LTS since I installed Ubuntu from CD that came with a book ?
Thanks,
Hiromichi

I would start with the release notes (and make sure your system is compatable):
[http://www.ubuntu.com/getubuntu/releasenotes/804]("http://www.ubuntu.com/getubuntu/releasenotes/804")

Then download the ISO:
[http://releases.ubuntu.com/releases/hardy/]("http://releases.ubuntu.com/releases/hardy/")

Then a good source on planning, burning the CD, and installing the system:
[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

And for lots of information about Hardy, the Ubuntu Guide Wiki:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

---

### Post by hwatari on 2008-11-22
> **drs305 said:**
> I would start with the release notes (and make sure your system is compatable):
[http://www.ubuntu.com/getubuntu/releasenotes/804]("http://www.ubuntu.com/getubuntu/releasenotes/804")

Then download the ISO:
[http://releases.ubuntu.com/releases/hardy/]("http://releases.ubuntu.com/releases/hardy/")

Then a good source on planning, burning the CD, and installing the system:
[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

And for lots of information about Hardy, the Ubuntu Guide Wiki:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")




Thank you for your help.
Hiromichi

---

