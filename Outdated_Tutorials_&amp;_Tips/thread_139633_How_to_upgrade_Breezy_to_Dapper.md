---
title: "How to upgrade Breezy to Dapper"
date: 2006-03-04
forum: Outdated Tutorials &amp; Tips
---

### Post by bdb51 on 2006-03-04
[U][B]Do this at YOUR OWN RISK! Your computer may break and become unusable. Ubuntuforums.org is NOT LIABLE for any damages that may occur. Again, please do this AT YOUR OWN RISK!
[/B][/U]
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

sudo gedit /etc/apt/sources.list

Replace everything in your sources.list with:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the &#8216;universe&#8217;
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the &#8216;backports&#8217;
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
 
## Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse





sudo apt-get update.

sudo apt-get dist-upgrade


I got everything here from
[http://www.macewan.org/2006/02/23/upgrading-breezy-to-dapper/](http://www.macewan.org/2006/02/23/upgrading-breezy-to-dapper/)

---

### Post by aysiu on 2006-03-04
Any reason you're using the *us.archive* repositories instead of just *archive*?

---

### Post by darrenrxm on 2006-03-05
You can already find this at the Unofficial Ubuntu 5.10 (Breezy Badger) Starter Guide. Please post orginal howto's that you made yourself. Do not copy from someone else.  Or at least make a better howto from someone else work.

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

---

### Post by majikstreet on 2006-03-05
This needs a HUGE warning plastered at the top:
**_WARNING: Do this at YOUR OWN RISK! Your computer may break and become unusable. Ubuntuforums.org is NOT LIABLE for any damages that may occur. Again, please do this AT YOUR OWN RISK!_**

---

### Post by bdb51 on 2006-03-05
[QUOTE=majikstreet]This needs a HUGE warning plastered at the top:
**_WARNING: Do this at YOUR OWN RISK! Your computer may break and become unusable. Ubuntuforums.org is NOT LIABLE for any damages that may occur. Again, please do this AT YOUR OWN RISK!_**[/QUOTE]



Thanks for the heads up

---

### Post by bdb51 on 2006-03-05
[QUOTE=darrenrxm]You can already find this at the Unofficial Ubuntu 5.10 (Breezy Badger) Starter Guide. Please post orginal howto's that you made yourself. Do not copy from someone else.  Or at least make a better howto from someone else work.

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)[/QUOTE]


I did this because not everybody know about that site, but many newbies know about this site.

---

### Post by darrenrxm on 2006-03-05
Newbies should *not* be upgrading from breezy to dapper. It is a unstable version of ubuntu. Wait a month or so and you will have a stable working version that you can upgrade to.

---

### Post by easyease on 2006-03-06
not so newbies should be very wary of doing this to......i followed the instuctions and something screwed up along the way.  spent today trying to find my hard drive againn and just made a fresh install of breezy again. dapper testing is out of my league at the mo.

---

### Post by arikato on 2006-03-06
i did that and first problems i got was with 'libssl' which wouldnt overwrite
'libopenssl' so i had to install it with 'dpkg --force-overwrite' etc...
and shitload of problems with x after reboot
but everything works fine now
so im using dapper now

and thanks for good how to


-arikato

---

### Post by stalefries on 2006-03-06
Actually, I would try to hold off on any of these postings from now on (including future releases) UNTIL AFTER THE OFFICIAL RELEASE. This is the second (maybe third) time I have seen a pre-emptive upgrade guide for $NEXT-UBUNTU-RELEASE-WHICH-IS-ACTUALLY-STILL-IN-TESTING, and people always have horrible problems.

---

### Post by clemcat on 2006-03-07
All of my friends tell me that if they were to look up the meaning of "loose-cannon" in the dictionary, they would see a picture of me.  (To those of you non-military-nonseafaring types, a cannon that is not tightly tied to the wall of the ship, can actually induce more damage to the ship than to the enemy)

I have to admit, that I am a complete newb to this distro, but the way that the community works, and the way that the distro is set up, I took the risk and did this the first night it was posted.  I actaully have been runing this now for a few days, and to my untrained newbish eye, it seems to be running fine.  I know that there is a potential for the insides of my computer to go spewing out of the  floppy drive door (or not, but it would be cool to see!), but if he had not posted it, I would have never learned about the site he got it from, and half of the other sites I have found have come from that site.  I understand that "newbs" should not neccesarily be doing this, but imo, something new that I learned, so thanks for posting (even thouhg i saw the first day that you credited the other site at the bottom).


Chris

---

