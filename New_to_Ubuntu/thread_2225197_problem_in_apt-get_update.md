---
title: "problem in apt-get update"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by tusharkoshti on 2014-05-20
Hello friends ,

I am trying theme for Ubuntu 14.04. 
In that I am getting error in following command. 

tushar@tushar-VPCEH3AEN:~$ sudo apt-get update
E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

How to tackle this problem ?

---

### Post by sandyd on 2014-05-20
Hi, can you post the output of
```

cat /etc/apt/sources.list
```

Thanks!

---

### Post by tusharkoshti on 2014-05-20
O/p of the command :

tushar@tushar-VPCEH3AEN:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
# deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb [http://archive.canonical.com/quantal](http://archive.canonical.com/quantal) partner
tushar@tushar-VPCEH3AEN:~$

---

### Post by sandyd on 2014-05-20
You have an old, not-properly formatted line in your sources file.

Run
```

sudo sed -i 's/deb http:\/\/archive.canonical.com\/quantal partner/#deb http:\/\/archive.canonical.com\/quantal partner/' /etc/apt/sources.list
sudo apt-get update

```

to fix.

---

### Post by Lars Noodén on 2014-05-20
The last line, #59, is causing the error.  If your system is running Trusty (14.04) then Quantal (12.10) doesn't belong in that list.  Additionally, Quantal expired a few days ago, on the 16th, and is no longer supported.  So if you remove or comment out that line, APT and your other tools should work fine.

Edit: never mind.

---

### Post by tusharkoshti on 2014-05-20
Thank u friends. Problem solved. 
I applied theme but I didnt like. Can anybody suggest me good theme for 14.04 ?
Thank you :)

---

