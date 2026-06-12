---
title: "[SOLVED] xubuntu repository sources problem (maybe)"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by MacHaddock on 2008-11-24
Hello everyone hope life is treating you well.

I'm having trouble updating my Xubuntu 7.10
This is what it says:
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)
  Size mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch

The things I'm trying to update is:
hpijs
hplip
hplip-data

I'm guessing this has something to do with my repositories. I have been fidleing with them before, trying to install a GIS-distribution. Maybe I messed it up. Does anyone have an Idea about what I should do?

here is my source list:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) gutsy main
deb [http://les-ejk.cz/ubuntu](http://les-ejk.cz/ubuntu) gutsy multiverse
deb-src [http://les-ejk.cz/ubuntu](http://les-ejk.cz/ubuntu) gutsy multiverse

---

### Post by bryanp on 2008-11-24
Hi there,
saw the same problem all over the weekend. Running 7.10 and haven't been playing with repositories. The Software update icon says these 3 items, hpijs,hplip,hplip-data are due for update, it starts to download file 1 of 3, then returns the same errors you saw. 

I was going to give it a couple of days to see what experience was out there and if the guys at Ubuntu have any thoughts.

---

### Post by MacHaddock on 2008-11-24
Thanks for backing me up :D

---

### Post by bryanp on 2008-11-24
Hi again,
I've been over at Launchpad and this has been reported as a Bug and will (I guess) be fixed in the fullness of time. It appears that a number of people have reported the same problem and the Ubuntu guys know about it.

No bug fix assignee as yet, but my printer still works, so I won't worry too much yet. keep an eye on the bug progress.

---

### Post by MacHaddock on 2008-11-25
Thanks! Good job.

---

### Post by adamite on 2008-11-26
I had the same problem all of you had. Last night, the three Hplip download items came up. Decided to try again, came up with 404 Not Found.

Well, I realized that the new package must be up. Clicked on Recheck, wait till it is finished downloading and then Install Updates and this time it worked. You might get more updates in addition to the new Hplip.:)

---

### Post by MacHaddock on 2008-11-27
Oh yeah I forgot to say. It's fixed now.

---

