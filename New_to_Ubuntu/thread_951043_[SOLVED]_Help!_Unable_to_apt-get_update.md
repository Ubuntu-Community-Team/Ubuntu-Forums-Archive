---
title: "[SOLVED] Help! Unable to apt-get update"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by NewJack on 2008-10-17
Tried to run 

```
sudo apt-get update
```

and got a failure message as shown in the screenshot attached.

Is their something I can do to fix this or are the repos down? 

Thanks in advance

---

### Post by saj0577 on 2008-10-17
Have you added any repos of your own?

Anything that might change the sources file?

Saj

---

### Post by jerome1232 on 2008-10-17
hehe I like how you edit out the hostname, yet leave your real name. What am I going to do with your computers hostname?

But yeah can you post your sources.list file, also wouldn't hurt to see if there is some other source file

```
cat /etc/apt/sources.list
ls -l /etc/apt
```

also just for the heck of it try and clean out your cache (won't hurt anything)

```
sudo apt-get clean
```

---

### Post by NewJack on 2008-10-17
Saj, I haven't added any new entries to my sources.list for a few weeks. Didn't have a problem updating anything until today. Here is my sources.list:

> # deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock
deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/
deb [http://linux.toribash.com/apt/](http://linux.toribash.com/apt/) toribash/

And here is the results of ls -l /etc/apt

> joe@Batcave:~$ ls -l /etc/apt
total 48
drwxr-xr-x 2 root root  4096 2008-08-11 23:19 apt.conf.d
-rw------- 1 root root     0 2008-07-02 06:16 secring.gpg
-rw-r--r-- 1 root root  3118 2008-09-30 20:05 sources.list
-rw-r--r-- 1 root root  2955 2008-08-04 01:44 sources.list~
drwxr-xr-x 2 root root  4096 2008-08-04 01:44 sources.list.d
-rw-r--r-- 1 root root  3118 2008-09-30 20:05 sources.list.save
-rw------- 1 root root  1200 2008-08-05 02:05 trustdb.gpg
-rw-r--r-- 1 root root 11267 2008-09-30 20:06 trusted.gpg
-rw-r--r-- 1 root root  9558 2008-08-05 02:05 trusted.gpg~

@jerome, you are right.  Don't know why I even bothered.  :lolflag:

---

### Post by jerome1232 on 2008-10-17
edit: On second thought is there anything in sources.list.d that's another spot for source files.


That all looks fine try switching servers

System->Administration->Software Sources

Where it says download from: choose 'other' from the drop down box, then select choose best server. Go have a cup of coffee while it pings about a gazillion servers to figure out the fastest one. Once it's done try and update again.

---

### Post by NewJack on 2008-10-17
I'm giving that a try now.  I'll let you know how it goes.

---

### Post by NewJack on 2008-10-17
No good Jerome.  I tried letting pick the best server, that didn't work.  I then randomly chose different servers and I got the error message which I attached a screenshot of.

---

### Post by jerome1232 on 2008-10-17
Actually I didn't look very hard, error 400 means mal-formed url so it must be one of those repositories in it.
why don't you backup yours and try mine

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bck
gksu gedit /etc/apt/sources.list
```


```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner
```

or you could start commenting yours out and see if certain ones cause the problem.

---

### Post by NewJack on 2008-10-17
Jerome,

  OK, that at least allowed me to connect for now.  I am still trying to figure out which of my entries from my original list could be giving me a problem.  Like I said, I haven't added anything lately and all was running smooth until earlier today.

---

### Post by jerome1232 on 2008-10-18
Well chalk it up to the deep mysteries of the world ;)

Here's the info I brought up on error 400.

[http://www.checkupdown.com/status/E400.html](http://www.checkupdown.com/status/E400.html)
[http://support.microsoft.com/kb/247249](http://support.microsoft.com/kb/247249)

---

### Post by NewJack on 2008-10-18
Hey Jerome, it turned out to be the Playdeb repo.  Everything else is fine.  Thanks again for the help!

Someone else had the same problem with the Playdeb repo in this thread:

[http://ubuntuforums.org/showthread.php?t=924526](http://ubuntuforums.org/showthread.php?t=924526)

---

### Post by jerome1232 on 2008-10-18
Yeah I think something is up with their server, I tried to install some games today from their site and I got error 400 when clicking their apt link.  :(


edit: I may have figured it out make sure you have this installed [http://www.playdeb.net/apturl_0.2.6-0~getdeb0_all.deb](http://www.playdeb.net/apturl_0.2.6-0~getdeb0_all.deb) then try their repo again.

---

