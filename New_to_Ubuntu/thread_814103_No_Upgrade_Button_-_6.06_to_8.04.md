---
title: "No Upgrade Button - 6.06 to 8.04"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by jcarleski on 2008-05-31
I had been running Hardy (installed from a CD), but in an attempt to update OpenRPG to 1.7, I killed my GUI and not being familiar enough with the system to get it back, I tried to reinstall.  Unfortunately, the only working CD I had available was Dapper (My laptop's CD-drive wrecked my 8.04 CD).  So I installed Dapper and have been trying all morning to upgrade to Hardy, but none of the posted methods have been working for me. My /etc/apt/sources.list is given below.

I've done sudo apt-get (update, upgrade dist-upgrade) and apparently am completely up-to-date on 6.06, but when I run update manager, no distribution upgrade button appears.  I've tried opening through the GUI, from the command line (gksu AND sudo) and the terminal (gksu AND sudo) I've also run it with the -c argument, and that didn't do it either.

I've also tried the do-release-upgrade option.  I find hardy files with -d and -p, but they won't install because they're developmental packages.  With no additional arguments, it says there are no upgrades.

I think I'd even take Gutsy at this point - I think ndiswrapper and openrpg 1.6.3 operate on it, but I'm not sure.  Any ideas???


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

---

### Post by wolfen69 on 2008-05-31
why not order a free Hardy cd and do a fresh install?

---

### Post by Joeb454 on 2008-05-31
+1 to that.

Though you'd have to wait a few weeks to recieve it. You could try a Local LUG to see if they can give you a CD?

---

### Post by sisco311 on 2008-05-31
You can't upgrade to 8.04 directly. First you need to upgrade to 6.10 -> 7.04 ...
Since 6.10 is no longer in the repositories you need a 8.04 cd and a fresh install.
[http://www.ubuntu.com/news/ubuntu610end-of-life](http://www.ubuntu.com/news/ubuntu610end-of-life)

---

### Post by Joeb454 on 2008-05-31
dapper is 6.06 - the last LTS release

---

### Post by Joeb454 on 2008-05-31
OK, perhaps this page will help the OP - though I don't know for sure

[https://help.ubuntu.com/community/HardyUpgrades#head-db224ea9add28760e373240f8239afb9b817f197](https://help.ubuntu.com/community/HardyUpgrades#head-db224ea9add28760e373240f8239afb9b817f197)

---

### Post by jcarleski on 2008-05-31
To the most recent reply-

I didn't see the alternate upgrade from the torrent down there.  maybe I'll give that a shot, but yes, that's where I got my information from in the first place and it's failing miserably.  I really need to get this back up and kicking again.. I've got two D&D games tomorrow.

---

