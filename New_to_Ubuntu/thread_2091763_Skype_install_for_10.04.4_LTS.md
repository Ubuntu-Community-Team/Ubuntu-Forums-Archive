---
title: "Skype install for 10.04.4 LTS"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by davejm73 on 2012-12-06
Hi there

After trolling the www as to how to install Skype onto 10.04.4 LTS after Ive had to reinstall, Ive had absolute no luck. 

Can anyone please tell me how to do this without confronting more issues, such as my latest being: 

'E:Malformed line 54 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

Many Thanks
D

---

### Post by zombifier25 on 2012-12-06
Your /etc/apt/sources.list was corrupted somehow. Can you post the output of the command:
```
cat /etc/apt/sources.list
```

---

### Post by davejm73 on 2012-12-06
david@david-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release i386 (20120214.2)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) partner

---

### Post by zombifier25 on 2012-12-06
Remove the last two line of the file /etc/apt/sources.list . Open it for editing by typing this command:
```
gksu gedit /etc/apt/sources.list
```
Then update your software sources:
```
sudo apt-get update
```
Then try installing Skype from the repo:
```
sudo apt-get install skype
```

---

### Post by davejm73 on 2012-12-06
YAY.....THANK YOU

Much appreciated and GREAT  help

D

---

### Post by mörgæs on 2012-12-06
Good, please mark the thread 'solved'.

---

