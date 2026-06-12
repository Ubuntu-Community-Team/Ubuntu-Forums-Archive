---
title: "my source list"
date: 2006-03-13
forum: Repositories &amp; Backports
---

### Post by bearbigears on 2006-03-13
i had to install dual boot of windows/ubuntu. my school will only allow us to use internet explorer. so i added the extra repositories last night but i have not been able to install the jave sun-j2rel.6. here is my source list, i have tried others but i have gotten all type of errors and still not able to install the java. any help will be appreciated.

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 


thanks
bear

side note, i was able to install java before when i had ubuntu stand alone os.

---

### Post by Koybe on 2006-03-13
This is strange, j2re packages are in multiverse :
[http://packages.ubuntu.com/breezy/devel/j2re1.4](http://packages.ubuntu.com/breezy/devel/j2re1.4)
[http://packages.ubuntu.com/breezy/web/j2re1.4-mozilla-plugin](http://packages.ubuntu.com/breezy/web/j2re1.4-mozilla-plugin)

Don't you forget to "sudo apt-get update"?

---

### Post by bearbigears on 2006-03-14
i know it is odd, i have used this source list before and got it. yes i did and apt-get update. after i installed the new source list. no i gues i will have to figure out how to install it from sun. any suggestions.

---

