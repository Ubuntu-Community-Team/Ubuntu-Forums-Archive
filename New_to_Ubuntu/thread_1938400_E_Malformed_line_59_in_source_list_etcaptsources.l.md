---
title: "E: Malformed line 59 in source list /etc/apt/sources.list (URI parse)"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by jackswyl on 2012-03-09
Hi everyone I am new to ubuntu and I'm having a few problems with it. When I try to use apt-get update the following errors occur:
E: Malformed line 59 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Here is my  sources list:
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb http?//archive.canonical.com/ oneiric partner
deb-src http?//archive.canonical.com/ oneiric partner
```

Thanks in advance for the help

---

### Post by Toz on 2012-03-09
The last two lines:
> deb http?//archive.canonical.com/ oneiric partner
deb-src http?//archive.canonical.com/ oneiric partner
...are wrong (? instead of : ). Since the correct entries exist right above them, delete those two lines and try again.

---

### Post by Cheesemill on 2012-03-09
Your last two lines have a ? instead of a :

That could be your problem :)

---

### Post by wojox on 2012-03-09
Back up:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

Edit:
```
gksudo gedit /etc/apt/sources.list
```

Remove this line in [COLOR="Red"]RED:[/COLOR]

```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://br.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://br.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://br.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://br.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://br.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://br.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://br.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://br.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://br.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

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
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.canonical.com/ oneiric partner
deb-src http://archive.canonical.com/ oneiric partner
[COLOR="Red"]deb http?//archive.canonical.com/ oneiric partner[/COLOR]
[COLOR="Red"]deb-src http?//archive.canonical.com/ oneiric partner[/COLOR]
```

---

### Post by jackswyl on 2012-03-09
Ok so I deleted the lines in red, but new errors showed up.
I tryed again to open the software center by typing software-center on terminal and the is what I get:
2012-03-09 15:51:38,613 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
Traceback (most recent call last):
  File "/usr/bin/software-center", line 151, in <module>
    app = SoftwareCenterAppGtk3(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 213, in __init__
    self.cache.open()
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 209, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 93, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 136, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Type 'niverse' is not known on line 18 in source list /etc/apt/sources.list, E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.

Also I get the same error when I type apt-get update:
E: Type 'niverse' is not known on line 18 in source list /etc/apt/sources.list
E: The list of sources could not be read.

Again, here is my  sources list:
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric u
niverse
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner

```
Thanks again.

---

### Post by Cheesemill on 2012-03-09
Line 18 has been split somehow. You have:
```
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric u
niverse

```
which should be
```
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) oneiric universe
```

---

### Post by jackswyl on 2012-03-09
You are correct [Cheesemill]("http://ubuntuforums.org/member.php?u=559258")
I fixed it and now it warks!
Thanks everyone for the help.

---

### Post by rojaasensei on 2012-05-04
I had the same problem arise.
Thank God I found this thread.

Thank you, Cheesemill

---

### Post by scottr99 on 2012-05-14
Hello, I am getting this message above on the latest 12 Ubuntu.  Can someone take a look at my sources.list file below please.  Thank you.


```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
# deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta amd64 (20100318)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

# Gerris flow solver
deb [http://download.opensuse.org/repositories/home:/popinet/xUbuntu_9.10](http://download.opensuse.org/repositories/home:/popinet/xUbuntu_9.10) precise

# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) precise

deb [http://www.openfoam.com/download/ubuntu](http://www.openfoam.com/download/ubuntu) precise main




# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
```

---

### Post by Vaphell on 2012-05-14
could you put that in the code tags? [co****de][/co****de]
what line number does the error mention?

---

### Post by scottr99 on 2012-05-14
> **Vaphell said:**
> could you put that in the code tags? ```

```
what line number does the error mention?

sorry.

i get the following lines exactly:

E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
# deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta amd64 (2010031:cool:]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

# Gerris flow solver
deb [http://download.opensuse.org/reposit...t/xUbuntu_9.10]("http://download.opensuse.org/repositories/home:/popinet/xUbuntu_9.10") precise

# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) precise

deb [http://www.openfoam.com/download/ubuntu](http://www.openfoam.com/download/ubuntu) precise main




# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
```

---

### Post by plucky on 2012-05-14
> i get the following lines exactly:

E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

It doesn't like this line ```
deb http://download.opensuse.org/reposit...t/xUbuntu_9.10 precise
```

because there isn't xUbuntu_9.10 on the site 

See [Here](http://download.opensuse.org/repositories/home:/popinet/)

So either correct the line to point to the correct repository or delete the line.

Good luck

---

### Post by scottr99 on 2012-05-14
> **plucky said:**
> It doesn't like this line ```
deb http://download.opensuse.org/reposit...t/xUbuntu_9.10 precise
```because there isn't xUbuntu_9.10 on the site 

See [Here]("http://download.opensuse.org/repositories/home:/popinet/")

So either correct the line to point to the correct repository or delete the line.

Good luck

Great then, but will I need a "precise", "multiverse", or "partner" to complete the new line?

Thank you.

---

### Post by chiikiita on 2012-09-20
Hi my names chiikiita and im also having the same error :::--->

 E:Malformed line 59 in source list /ect/apt/sources.list (dist parse) 

I remember tryna do something I think for "conky" but it wasnt succesful. I was told to change a line but im not sure if i did. Im new to linux SO its very confusing I hope someone can help.

Ive tried the rm var/lib/ or wateva ... idk it i just tried everything so far i found online and i feel like ima mess it up more. and i dont need that!!! please help!!

[PHP]# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ubuntu.securedservers.com/ precise main restricted
deb-src http://ubuntu.securedservers.com/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.securedservers.com/ precise-updates main restricted
deb-src http://ubuntu.securedservers.com/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.securedservers.com/ precise universe
deb-src http://ubuntu.securedservers.com/ precise universe
deb http://ubuntu.securedservers.com/ precise-updates universe
deb-src http://ubuntu.securedservers.com/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.securedservers.com/ precise multiverse
deb-src http://ubuntu.securedservers.com/ precise multiverse
deb http://ubuntu.securedservers.com/ precise-updates multiverse
deb-src http://ubuntu.securedservers.com/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://ubuntu.securedservers.com/ precise-security main restricted
deb-src http://ubuntu.securedservers.com/ precise-security main restricted
deb http://ubuntu.securedservers.com/ precise-security universe
deb-src http://ubuntu.securedservers.com/ precise-security universe
deb http://ubuntu.securedservers.com/ precise-security multiverse
deb-src http://ubuntu.securedservers.com/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/ partner
deb-src http://archive.canonical.com/ partner[/PHP]

---

### Post by Toz on 2012-09-20
@chiikiita,
Hello and welcome to the forums.

The last two lines of that file (/etc/apt/sources.list) should read:
```
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

```

---

### Post by chiikiita on 2012-09-24
@ Toz 

Thanks so much! It works now! i been tryna figure out how to fix it and couldnt ! Omg i dnt know you but i love you haha .. thanks again!

---

