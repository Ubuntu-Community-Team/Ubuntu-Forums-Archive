---
title: "An error occurred during the signature verification"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by an1mus on 2011-10-09
Hi everyone!

I'm another noob added to the community!

I use Ubuntu 10.04 LTS -the Lucid Lynx and recently came across this error message while updating:


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) karmic-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


This must have been going on for a while, because the Update Manager shows that "the package information was last updated 157 days ago", while it runs 2-3 times a week (I've probably NEVER noticed the error messages)!!!

Could I have any help here about how to fix this?

Thanks in advance! :)

---

### Post by ibutho on 2011-10-09
Try changing the mirror using the instructions [here]("http://tipotheday.com/2008/05/07/slow-downloads-with-apt-get-change-repos-with-select-best-server/").

---

### Post by mörgæs on 2011-10-09
You have entries for 9.10 in your /etc/apt/sources.list, which is not allowed on a 10.04 system.

Please post the contents of this file.

---

### Post by QLee on 2011-10-09
> **mörgæs said:**
> You have entries for 9.10 in your /etc/apt/sources.list, which is not allowed on a 10.04 system.
...
Will you please clarify what you mean by "not allowed"?

When upgrading, the package manager will choose the highest numbered version of a package ([Edit: in the target release if there is a target release]), thus having the older repositories there wouldn't cause the problem an1mus detailed, which is to do with repository signing keys.

I do agree that those old sources should be deleted to clean up the list.

There is this thread with a similar report:
[http://ubuntuforums.org/showthread.php?t=802156&page=3](http://ubuntuforums.org/showthread.php?t=802156&page=3)

And, this launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/24061](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/24061)

It might be a good idea to have a look at those, an1mus.

---

### Post by an1mus on 2011-10-09
> **mörgæs said:**
> You have entries for 9.10 in your /etc/apt/sources.list, which is not allowed on a 10.04 system.

Please post the contents of this file.
The content of my sources.list file, as requested: 

deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe

deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://packages.enlightenment.org/ubuntu](http://packages.enlightenment.org/ubuntu) lucid main extras
deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) jaunty main universe


I'm waiting for your ideas, because I've got none!

---

### Post by mörgæs on 2011-10-10
Stricktly speaking it could work having different releases in sources.list, but it could also lead to a lot of problems, and it is not something the ordinary user should deal with.
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Thanks to drs305 and bodhi.zazen for pointing that out.


For this problem I would begin with backing up sources.list and creating a new one using

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

After that try to update again.

---

### Post by an1mus on 2011-10-13
Thank you all! Seems to be working for me so far.
:-)

---

### Post by mörgæs on 2011-10-14
Good, then please mark the thread 'solved' using 'thread tools'.

---

