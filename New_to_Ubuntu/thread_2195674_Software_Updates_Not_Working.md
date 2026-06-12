---
title: "Software Updates Not Working"
date: 2013-12-25
forum: New to Ubuntu
---

### Post by richramik on 2013-12-25
Here is the sequence of events - please understand I'm not a techy, I need simple language.

Loaded 13.10 (proud to say I created my own ISO to accomplish thios) on new HP Pavilion and eliminated MS 8.1 (Yippeeeeee).
Had problem with HP Laserjet 1200 and loaded new library; printer works fine.
Loaded Synaptic to do my software updates. (i remember this from "playing" with previous versions of Ubuntu)
Now the Software Updater and Synaptic do not really work as far as I know.


When I run the Software Updated, I get the following message:  FAILED TO DOWN LOAD REPOSITORY INFORMATION


When I run Synaptic, I get the following:

--------START OF MESSAGES

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Some index files failed to download. They have been ignored, or old ones used instead.

-------END OF MESSAGES

Any advice would be appreciated.

---

### Post by oldos2er on 2013-12-25
You need to remove the CD-ROM from your sources. Open Synaptic, click menus Settings, Repositories, Other software tab, uncheck CD-ROM. When you reload sources the error should be gone.

---

### Post by zeljkojagust on 2013-12-26
Can you please open a terminal and execute the following command:

"cat /etc/apt/sources.list"

Paste the result here.

---

### Post by richramik on 2013-12-26
Well I removed the reference to the cd by OLDOS2ER and it seems to be working, both Synaptic and Software Updater.  

But I also cat'ed and the results follow:

rich@rich-500-164:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
rich@rich-500-164:~$ ^C
rich@rich-500-164:~$ 

Thanks
Rich

---

### Post by zeljkojagust on 2013-12-26
sources.list looks OK now. All should work.

---

### Post by richramik on 2013-12-26
Thanks for the help.  All is well in Mudville!

---

