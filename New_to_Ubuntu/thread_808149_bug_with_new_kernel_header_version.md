---
title: "bug with new kernel header version?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by drarem on 2008-05-26
After installing the 2.6.24.17 (basically the .17 version) and rebooting, I was stuck at 640x480, it couldn't detect my nvidia driver.

So I recovered back to the .16 versions and now I have wide-screen again.

Anyone else have this problem?  Yes, I used hardware manager to enable the restricted drivers.

---

### Post by PmDematagoda on 2008-05-26
Can you post the output of:-
```
cat /etc/apt/sources.list
```

Also, when you updated, did you do a full update?

---

### Post by madpeople on 2008-05-27
same problem [here]("http://ubuntuforums.org/showthread.php?p=5056676#post5056676") (i posted the output of cat /etc/apt/sources.list though i also wonder if it is something un-related to .17 )

---

### Post by ttlarsen on 2008-05-27
I just made a full update to kernel 2.16.24-17 generic and updated kernel headers etc but it cannot boot.

In recovery mode I can see that it fails with the message:

ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to shell.

BusyBox  ..etc.. Built-in shell(ash)

(initramsfs) 

A search on the forum shows a similar problem occurred with an earlier update. Also note that to day the Nvidia drivers were also updated. This could be the problem ??

What can I do -  wait for another update ??

br TTL

---

### Post by drarem on 2008-05-27
Here is my sources.list - avant could have messed things up, but don't know if anyone else has reported that the .17 works good with nvidia and/or is fixed.

Thanks.

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
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
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main



```

---

### Post by PmDematagoda on 2008-05-27
The sources.list looks ok, perhaps you may need to reinstall the Nvidia driver yourself, do you know how to do that?

Edit:- Also, before trying to install the Nvidia driver manually, did you check if the proper repos are there by going to Software Sources in System>Administration>Software Sources and then checking the Ubuntu Software and Updates tab?

---

### Post by kavon89 on 2008-05-27
Same problem [here]("http://ubuntuforums.org/showthread.php?t=808797") aswell. Tried manually installing the Nvidia driver too.

---

