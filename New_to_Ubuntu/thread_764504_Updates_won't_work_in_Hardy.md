---
title: "Updates won't work in Hardy"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by hello_emo_boy on 2008-04-23
So I just updated to Hardy from Feisty and for the most part every thing's working.
However! *DUM DUM DUM!!!!*
When I try to run the updates, it freezes. Not the whole computer, but just the update screen.
Any ideas? Patches?
I'm kind of a n00b so please be gentle.

Cheers

---

### Post by fatfranko on 2008-04-23
maybe its just the gui updater.  try running:

sudo apt-get update

then:


sudo apt-get upgrade

---

### Post by Bachstelze on 2008-04-23
It is usually not recommended to "skip" releases when updating. You'd better update first from Feisty to Gutsy, and then to Hardy (or better yet, do a fresh Hardy install if you can afford it).

---

### Post by hello_emo_boy on 2008-04-24
Sorry, I meant I had the version just before Hardy.

---

### Post by hello_emo_boy on 2008-04-24
I tried that and this is what I got:

corey@Domo:~$ sudo apt-get update
sudo: unable to resolve host Domo

Any Idea?

---

### Post by SunnyRabbiera on 2008-04-24
Its probably server overload/freeze in anticipation for the official hardy release.

---

### Post by phidia on 2008-04-24
You could post your sources.list however hardy is still listed as in development-that is it hasn't been officially released yet (checked at 4-24-08 12:10AM EST).

---

### Post by fatfranko on 2008-04-24
never had that problem bro.  i googled it and found this thread, hopefully it helps:

[http://ubuntuforums.org/showthread.php?t=733333](http://ubuntuforums.org/showthread.php?t=733333)

---

### Post by Bachstelze on 2008-04-24
> **hello_emo_boy said:**
> I tried that and this is what I got:

corey@Domo:~$ sudo apt-get update
sudo: unable to resolve host Domo

Any Idea?

Please paste the contents of your /etc/apt/sources.list.

---

### Post by hello_emo_boy on 2008-04-24
Ok, it's getting better now, not fully working, but getting closer.
Now, when I try to download the updates this is what I get:

  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)

What does that mean?

---

### Post by Helios38 on 2008-04-24
> **SunnyRabbiera said:**
> Its probably server overload/freeze in anticipation for the official hardy release.

i agree with sunny.


today due to deciding to repartition my two HD's (and wanting to switch to xubuntu 8.04 now that its official)

i had to update my system after installing it, and the update downloads were painfully slow.


i wouldnt worry about the ubuntu servers, like sunny said, its probably just full to the brim with people wanting 8.04

---

### Post by hello_emo_boy on 2008-04-24
Ummm... How do I do that? *slightly embarassed*

---

### Post by fatfranko on 2008-04-24
go to the terminal: Applications/Accessories/Terminal
then type:
gedit /etc/apt/sources.list

---

### Post by hello_emo_boy on 2008-04-24
Ok, got it:

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release Candidate i386 (20080417)]/ hardy main restricted
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

uhhh... whatever that means

---

### Post by fatfranko on 2008-04-24
found problem.  [http://ca.archive.ubuntu.com/](http://ca.archive.ubuntu.com/)    is down

might have to wait to update until they're back up :(

you can try:

[http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/)       its up, i just tried it

---

### Post by hello_emo_boy on 2008-04-24
Thanks! But in my playing around I managed to fix it. Just had to switch the software sources to download from the main server rather than Canada.

THANK YOU EVERYONE!
If you ever need anyone killed and/or certain "favors" performed, I'm your man!

---

### Post by fatfranko on 2008-04-24
cool man!

---

### Post by agent8131 on 2008-04-24
See **[Ubuntu Bug #32906]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906")**

---

### Post by finneyabraham on 2008-04-25
> **hello_emo_boy said:**
> I tried that and this is what I got:

corey@Domo:~$ sudo apt-get update
sudo: unable to resolve host Domo

Any Idea?
The solution to "unable to resolve host" is in this link


[http://ubuntuforums.org/showthread.php?t=723361&highlight=unable+sudo+hardy](http://ubuntuforums.org/showthread.php?t=723361&highlight=unable+sudo+hardy)

---

