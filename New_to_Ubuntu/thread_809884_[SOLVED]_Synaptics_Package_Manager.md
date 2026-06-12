---
title: "[SOLVED] Synaptics Package Manager"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Greydog on 2008-05-27
I've searched the threads about SPM but, so far, nothing that I've tried has gotten Synaptics to work...even worse, I did the "sudo synaptics" thing to try to load Wifi-radar and, when I select Wifi-radar from App> Internet> Wifi-radar, SPM tries to launch.....to no avail, btw.

Has anyone experienced problems like this? I am pretty much at a loss as to how to fix it. 

As an aside, the up-date notification thingie tries to launch and then nothing happens as well.

Another aside, If I do System> Admin> SPM,...first try.... nohing...second try, works as advertised. Very confusing!

Thanks all,

Greydog

---

### Post by Duck2006 on 2008-05-27
In the terminal

sudo apt-get update
sudo apt-get upgrade

Then try your SPM

---

### Post by Paqman on 2008-05-27
Does Add/Remove launch? What about Update Manager?

---

### Post by steveneddy on 2008-05-27
> **duck2006 said:**
> in The Terminal

Sudo Apt-get Update
Sudo Apt-get Upgrade

Then Try Your Spm

+1

---

### Post by Greydog on 2008-05-27
Thanks everyone!

I get a "not able to resolve" comment while doing the "update/upgrade" thing, and SPM still will not respond.

Any other ideas??

Thanks again,

Greydog

---

### Post by Greydog on 2008-05-27
Bump

---

### Post by Greydog on 2008-05-28
Duck,

I tried the apt-get as you suggested. Sme problem.

Any other ideas?

Thanks,

Greydog

---

### Post by Greydog on 2008-05-28
Paqman,

Update Manager opens but it just sits there like it is loading but it does nothing.

Add-Remove looks like it is woring but, as I said, I added Wifi radar and when I try to runs it, it tries to launch "administrative application (?).

Thanks for your help,

Greydog

---

### Post by Oldsoldier2003 on 2008-05-28
> **Greydog said:**
> Thanks everyone!

I get a "not able to resolve" comment while doing the "update/upgrade" thing, and SPM still will not respond.

Any other ideas??

Thanks again,

Greydog

does the machine have a working internet connection? If so are you behind a proxy server? Please post the results of ```
cat /etc/apt/sources.list
```

---

### Post by Dazed_75 on 2008-05-28
Just a thought.  The "unable to resolve" sounds like either a wrongly named package or perhaps more likely a snafu in your repository list.  Have you by any chance added any repositories manually? Perhaps the problem is a line the update manager type programs are unable to resolve.  Even if you did not add/edit anything manually you should probably check that out.

---

### Post by Greydog on 2008-05-28
Soldier,

Yes, I'm using the computer to write this.

Results of: cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe restricted multiverse main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe multiverse restricted main #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe multiverse restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe multiverse restricted main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe multiverse restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe multiverse restricted main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports universe multiverse restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports universe multiverse restricted main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Did I do that right???

Thanks,

Greydog

---

### Post by Greydog on 2008-05-28
Dazed,

I don't recall manually installing any repositories.

Sounds like you and Soldier are both leaning that way, though. 

The more I think about it, that does sound like it makes sense.

I really appreciate everyones help,

Greydog

---

### Post by Greydog on 2008-05-29
Seems as if the move to 8.04 borked /etc/hosts.

I found that my ".domain" was added to the host name of this computer.

I did system> admin> network> hosts, and changed it back to "computername" there, and all is well......so far.

I suspect I'll have to edit /etc/hosts but, it says I don't have permissions for that. I'll figure that out later.

Thanks again for all of your help,

Greydog

---

