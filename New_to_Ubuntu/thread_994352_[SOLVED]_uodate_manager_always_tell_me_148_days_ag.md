---
title: "[SOLVED] uodate manager always tell me 148 days ago"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by broekskw on 2008-11-26
can someone:lolflag: tell me if this is ok, every time i update my ubuntu 7.10 updated to 8.04 i think?,about 2 hours later it keep telling me that i still have update to install and that it's been 148 days since the last update; see screen shot

the only error that i get is about my cd rom not loaded and you should try the command (it think this is the command, did not wright it down( apt-cdrom

---

### Post by SunnyRabbiera on 2008-11-26
a bit strange, but I would not worry about it if its not interfering with your functionality.

---

### Post by bapoumba on 2008-11-26
Please post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by broekskw on 2008-11-26
thanks for the replies just got home from work
here is my output for that command

eb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe #Added by software-properties
#deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
#deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
#deb [http://ftp.debian.org](http://ftp.debian.org) etch main
#deb [http://ftp.debian.org](http://ftp.debian.org) etch main
broekskw@broekskw-desktop:~$ 

looks like i only have 7.10 i thought that i updated to 8.04
:lolflag:

---

### Post by oldos2er on 2008-11-27
Comment out the first line, then run "sudo aptitude update".

---

### Post by broekskw on 2008-11-27
oldos2er what do you mean by 

"Comment out the first line,"

delete the first line

"eb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted"

not to sure if this is what you mean:confused:

---

### Post by k3lt01 on 2008-11-27
He means that you need to make this
```
eb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```look like this
```
# eb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
``` The # (hash) is what he is calling a "comment".

---

### Post by broekskw on 2008-11-27
k3lt01 thanks for your reply, trying to understand all of this again (going to try learn this all over again) so thats what comment is

ok change this and then save file correct??

thanks

---

### Post by k3lt01 on 2008-11-28
Thats it. Let us know how you go with the commenting out bit.

As an aside, my laptop did a similar thing to me the other day. Not 148 days though. Anyway what I did was untick everything in the Software Sources dialog box and close it. Then rebooted Ubuntu. Then went back into software sources and reticked everything that had been ticked before. Closed that and it checked everything. Reboot Ubuntu and it has been ok ever since. That was about 1 week ago.

---

### Post by broekskw on 2008-11-29
hey k3lt01 this my be a stupid question but how do i edit this line in a terminal??
and also when i cut and pasted this line it looks like i  deleted the fist letter on that first line it is "deb" not "eb" dose this make a diff

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe #Added by software-properties
#deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
#deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
#deb [http://ftp.debian.org](http://ftp.debian.org) etch main
#deb [http://ftp.debian.org](http://ftp.debian.org) etch main
broekskw@broekskw-desktop:~$ edit cat /etc/apt/sources.list
Warning: unknown mime-type for "cat" -- using "application/*"
Warning: unknown mime-type for "/etc/apt/sources.list" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no write permission for file "/etc/apt/sources.list"
:lolflag:

---

### Post by plucky on 2008-11-29
> hey k3lt01 this my be a stupid question but how do i edit this line in a terminal??


```
gksudo gedit /etc/apt/sources.list
``` and put a **#** in front of the ```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
``` This will stop the update manager asking you to insert the Ubuntu CD whenever you are installing packages.


or from a GUI **System > Administration > Software Sources** and untick the CDrom as a source.

Either will do the same job.

Good Luck

---

### Post by k3lt01 on 2008-11-29
> **broekskw said:**
> hey k3lt01 this my be a stupid question but how do i edit this line in a terminal??Cut and paste this into your terminal
```
gksudo gedit /etc/apt/sources.list 
```This will open your sources list file in gedit and you can edit it from there.

> **broekskw said:**
> and also when i cut and pasted this line it looks like i  deleted the fist letter on that first line it is "deb" not "eb" dose this make a diffI didn't actually notice that. It should be "deb" as software source wont recognise it if it isn't.

Little bit of advice when you have a heap of code, or any code actually, to post put it in a code box. To do this cut just type, without the " and spaces between the brackets and words "[ code ]" goes at the beginning and "[ /code ]" goes at the end of the code your posting. This will make it look like this and it will take up much less space.
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe #Added by software-properties
#deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
#deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
#deb [http://ftp.debian.org](http://ftp.debian.org) etch main
#deb [http://ftp.debian.org](http://ftp.debian.org) etch main
broekskw@broekskw-desktop:~$ edit cat /etc/apt/sources.list
Warning: unknown mime-type for "cat" -- using "application/*"
Warning: unknown mime-type for "/etc/apt/sources.list" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no write permission for file "/etc/apt/sources.list"
```

---

### Post by broekskw on 2008-11-29
hey k3lt01 and plucky thats for your replies just got up and going to work, will try when i get home:popcorn:

again thanks or all your helps:lolflag:

will advise if this gets it fixed:guitar:

---

### Post by broekskw on 2008-11-30
looks like this solved my update manager message (148 days)
great and thanks all for your kind help:guitar:

ps i forget how to input the "solved" at the front of the post??

ok just found out how

---

### Post by drs305 on 2008-11-30
> **broekskw said:**
> 
the only error that i get is about my cd rom not loaded and you should try the command (it think this is the command, did not wright it down( apt-cdrom

The message may be telling you that the install CD is not inserted. You can eliminate this by opening Synaptic or Software Sources. Go to Repositories > Third Party and untick the CDROM reference in the bottom window. 

Unless you have this unticked, you must have the original install CD inserted when you update your sources or your will get the message.

---

