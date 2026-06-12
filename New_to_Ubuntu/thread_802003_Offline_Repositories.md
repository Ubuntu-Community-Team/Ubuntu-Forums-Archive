---
title: "Offline Repositories"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by shoaibi on 2008-05-21
I want to create a local mirror of repositories for students at my campus. I want to copy each and everything.

So tell me what i would need to change in:
[http://www.arsgeek.com/?p=997](http://www.arsgeek.com/?p=997)

And what specs would i required? is 160GB HD enough? or should i double it?

---

### Post by Xiong Chiamiov on 2008-05-21
I don't think you would have to change anything as far as commands go; just don't open it up to the outside world when you're configuring apache.

I have no idea how big the standard repos are, but I have a feeling they're pretty huge.

---

### Post by shoaibi on 2008-05-21
how much?
what if i mirror this:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://pk.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://pk.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://pk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://pk.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://pk.archive.ubuntu.com/ubuntu/ hardy universe
deb http://pk.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://pk.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://pk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://pk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://pk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://pk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://pk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://pk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security restricted main
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://apt.wicd.net hardy extras
deb http://packages.medibuntu.org/ hardy free non-free
deb http://ppa.launchpad.net/corenominal/ubuntu gutsy main
deb-src http://ppa.launchpad.net/corenominal/ubuntu gutsy main
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://viewizard.com/linux debian/
deb http://pk.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by hyper_ch on 2008-05-21
have a read at Creating an Ubuntu mirror:

[http://www.ubuntu.com/getubuntu/mirror](http://www.ubuntu.com/getubuntu/mirror)

---

### Post by shoaibi on 2008-05-21
okay, i am using following to mirror:

```

deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse

deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse

deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://apt.wicd.net hardy extras

clean ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/

```

with the above mirror.lst, i want to update the repositories of my private mirror once a week, how do i do it? cron? or what?
and what if i create a LVM of 2x160=320GB HD, enough for a while?

---

### Post by shifty_powers on 2008-05-21
[http://www.ubuntu.com/getubuntu/mirror/2](http://www.ubuntu.com/getubuntu/mirror/2)

> Hardware Requirements

We require that you run a modern unix system and recommend running Ubuntu on your mirror host. It is suggested that you provide HTTP access with apache and ftp access with something like vsftp.

Providing rsync access to Ubuntu mirror directories on your mirror is also helpful.

The mirror needs to be located in a secure location reliably connected to the internet. ADSL and cable hosted mirrors will not be considered for becoming an official mirror (however are suitable for a private mirror).
Bandwidth requirements

Predicting the bandwidth requirement for becoming a Ubuntu mirror can be difficult. There are number of indicators of bandwidth usage which can be used for a guide.

Ubuntu users are encouraged to download from Ubuntu mirrors within their own country, so countries with a large population of Ubuntu users have a high bandwidth requirement for hosting a Ubuntu mirror. Conversely, Ubuntu mirrors located in countries with a small Ubuntu user population such as Indonesia will have a very low bandwidth requirement for hosting a Ubuntu mirror.

A popular Ubuntu mirror located in the United States, which has a high population of Ubuntu users, can expect to use up to 400-500 megabits of bandwidth or more. If your mirror will target a large group it may be important to apply bandwidth restrictions or Quality of Service rules to avoid impacting other systems or services on the network the Ubuntu mirror is hosted on. An Ubuntu mirror located in Indonesia, a country with a smaller Ubuntu population, may see no more than 10 megabits of bandwidth in a peek period.

Because Ubuntu users are encouraged to download from mirrors within their own country, it is important to consider national bandwidth instead of international bandwidth.

If you are unsure of the bandwidth requirements of hosting an Ubuntu mirror within your country, contact the Ubuntu mirror team for assistance.
Disk Space Requirements

To mirror the Ubuntu archive, you will need 220 gigabytes with room to grow. To mirror the Ubuntu releases you will need about 30 gigabytes. Release disk space is generally constant while archive disk space will continue to grow. 

---

### Post by shoaibi on 2008-05-21
i read that.....
but mine would be private, so even if i dont follow requirements, its okay....
about that 220GB, i just wanted to ask, if it would have any problem incase of LVM?

---

### Post by shifty_powers on 2008-05-21
going by

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

ubuntu is quite happy with an lvm setup...

---

### Post by hyper_ch on 2008-05-21
it's 220 GB now for all releases... one relase is only about 40 gb... I don't think you want all the old releases also, do you?

---

### Post by shoaibi on 2008-05-21
nope, i just want to mirror hardy for the time being....
Also what about my second question? about synchronzing my local private mirror with the universal mirror once a week, how can i do it? cron? how?

---

### Post by hyper_ch on 2008-05-21
as far as I've seen you would run a cron with rsync... you can run that daily (as long as you do have a cron running it doesn't matter as it will run automatically)

---

### Post by shoaibi on 2008-05-21
and what would that cron would be about? what would i run?

---

### Post by hyper_ch on 2008-05-21
with rsync you do synchronize your local repository with the remote one and cron is just there to start the rsyncing in regular intervals.

---

### Post by shoaibi on 2008-05-21
In my case i am doing mirroring with two different servers, what would be the resync for that? one by one for both servers? or what?

---

### Post by shoaibi on 2008-05-21
Okay, last questions:
I am following:
[http://www.howtoforge.com/local_debian_ubuntu_mirror_p2](http://www.howtoforge.com/local_debian_ubuntu_mirror_p2)

Tell me what to become of:
**8. Make The Local Mirrors Accessible Over HTTP**
whereas i am using multiple mirrors as show in the code below...
Also please check if this file is okay to be used as mirror.lst?
```

deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://apt.wicd.net hardy extras
deb http://packages.medibuntu.org/ hardy free non-free
deb http://ppa.launchpad.net/corenominal/ubuntu gutsy main



deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb-src ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
deb-src http://ppa.launchpad.net/corenominal/ubuntu gutsy main


clean ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/ubuntu/
clean http://archive.canonical.com/
clean http://apt.wicd.net/
clean http://packages.medibuntu.org/
clean http://ppa.launchpad.net/


```



[EDIT]
Also can somebody tell me a nice partition scheme for this purpose?
I have 2x160=320LVM
and i plan to:
/boot=100MB
/root=500MB
/home=800MB
/=5GB
/=remaining all

---

