---
title: "55 Updates?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Jabz.biz on 2008-05-09
Hi,

Even after browsing the forum and looking for similar posts, I could not find an update question like mine...so I give it a shot:


Since I installed lame last night, the updater says there are 55 updates available. 40.9 MB!!! including system monitor and sudo updates...

When I tried to install, I get a message that all updates are unauthenticated. Ain`t this strage? I also ran into problems like "could not be downloaded" or "some PGP key is missing/ proxie fails" kinda style errors. 

I assume that`s because of the servers were too busy with the requests. Can someone clarify the situation?! 40 MB unauthenticated,...I`m alittle nervous. :)

Thanks.

---

### Post by hermes0710 on 2008-05-09
I randomly have these issues but they disappear later. Have manually added any repositories?

---

### Post by superprash2003 on 2008-05-09
i remember seeing that before.. it popped up once , but it didnt ask me the next time!!

---

### Post by Jabz.biz on 2008-05-09
I manually installed the bugtracker...that seemed not that dangerous to me. All others are still waiting. 54 Updates to go. 
I turned my engine off and switched it on again, ...still there. :)

No, I havn`t installed any repositories. (If I get that word right). I only installed audacity (add/ remove software) and downloaded lame via terminal.

---

### Post by Sirron on 2008-05-09
Have you tried sudo apt-get update?

If a repository doesn't respond in time, it looks like the package manager gives up on it - and then doesn't authenticate anything. If you eliminate the repository that doesn't respond, by deselecting it in software sources, it might successfully complete reloading the package information.

---

### Post by Jabz.biz on 2008-05-09
> **Sirron said:**
> If a repository doesn't respond in time, it looks like the package manager gives up on it - and then doesn't authenticate anything. If you eliminate the repository that doesn't respond, by deselecting it in software sources, it might successfully complete reloading the package information.

Good hint. I check on that in a minute. But how do you explain updates for sudo, mount and other security relevant parts of the system?

I uploaded a screenshot... [http://www.flickr.com/photos/20995805@N05/2478256858/](http://www.flickr.com/photos/20995805@N05/2478256858/)  Just if someone is interested in it.


[COLOR="Red"][B]
EDIT[/B][/COLOR]: Even if I install only a trusted repository, like apport-gtk (interface for crash reports), the update manager says it`s unauthenticated. Is there maybe a way to completely ignore these updates, permanently? Only these, not all updates.

---

### Post by quelx on 2008-05-09
can you post your /etc/apt/sources.list?  If it's asking for a key for the bugtracker repo the location of said key can probably be found in there.

---

### Post by Jabz.biz on 2008-05-10
My sources.list:

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by billgoldberg on 2008-05-10
All those repo's look like they are legit.

---

### Post by brettg on 2008-05-10
"But how do you explain updates for sudo, mount and other security relevant parts of the system?"

Coincidence? I had a whole bunch of updates today too.

---

### Post by black3ug on 2008-05-10
hi, i just want to ask a few things about your install. 

1. Did you upgrade to Hardy or did you clean install?
2. When did you last install updates?

sorry if it sounds noobish but i want to clarify some things. i've been updating system critical stuff as well. everything went fine but now i'm concerned. 

my system was originally the ubuntu beta release that i kept upgrading to the latest hardy.

---

### Post by Jabz.biz on 2008-05-10
> **black3ug said:**
> hi, i just want to ask a few things about your install. 

1. Did you upgrade to Hardy or did you clean install?
2. When did you last install updates?

sorry if it sounds noobish but i want to clarify some things. i've been updating system critical stuff as well. everything went fine but now i'm concerned. 

my system was originally the ubuntu beta release that i kept upgrading to the latest hardy.

- I made a copmpletely fresh install. No upgrades. 

- And updated every 1-2 days since hardy came out. Smaller updates, legitimate updates. :)

---

### Post by nowshining on 2008-05-10
hardy seems to be on the edge right-now - after a bit - a month or two the stabilization should be complete, ie: that's why the many updates.

It's normal.

as for the not authenticated - as long as u know where it's coming from - it should be fine to ignore those.

Also u can go into software sources and change the mirrors iif need be to another mirror to download from.

---

### Post by Jabz.biz on 2008-05-10
Hi, your last point sound sinteresting. Where can I add/ edit/ delete Software Sorces/ Mirrors!? I`m too new to ubuntu, sorry. :) 

Thanks for your help.

---

### Post by forestpixie on 2008-05-10
Open software source - in system admin menu - you can change the server there.

> logging into your windows installlogging into windows won't help too much I imagine :D there's certainly no need to be reinstalling for something like this

---

### Post by Jabz.biz on 2008-05-10
Wow, found it. 

BUT,...(never stops!) 

I get the message that "The Information About Available Software Is Out Of Date". When I try to reload it, I get this message:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>



Looking at Software Sources > Authentication I can see, I have two trusted providers/ Keys. The Ubuntu automatic Signing Key and Automatic CD Signing Key. 

OMG...help! :)

---

### Post by nowshining on 2008-05-10
I don't exactly know about hardy, however on the Authentication Tab, find a button called Defaults and click it and then re-load.

---

### Post by Jabz.biz on 2008-05-11
OK, I made it. Just updated my System. So far everything seems to be fine...but I`ll watch it. 

@ nowshining:
Those two were the defaults, so there was nothing to restore. :( 

Thank you all for your help. I became a little more insight in how the updater works.

---

