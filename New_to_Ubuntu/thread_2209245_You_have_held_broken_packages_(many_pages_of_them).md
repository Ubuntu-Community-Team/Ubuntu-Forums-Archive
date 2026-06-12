---
title: "You have held broken packages (many pages of them)"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by sparker12 on 2014-03-04
I upgraded from 12.10 to 13.10 and synaptic reports that I have held broken packages. There are reams of them! Things I have done to try and fix them:
sudo apt-get dist-upgrade
sudo apt-get clean 
sudo dpkg --configure -a 
sudo apt-get -f install 
sudo apt-get update
sudo apt-get autoremove
sudo apt-get update && sudo apt-get upgrade
There were also some aptitude commands I tried but I honestly can't remember them now. I also tried the procedure here: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure) but no change noted. 
This is the output of ubuntu-support-status:

You have 2016 packages (67.2%) supported until July 2014 (9m)  
  You have 45 packages (1.5%) that can not/no-longer be downloaded  
 You have 940 packages (31.3%) that are unsupported  

I could manually delete all the broken packages but I get warnings that my system will no longer function. I am losing hair on a daily basis but this is definitely speeding up the process. 
Any ideas how I can fix this problem?

---

### Post by vasa1 on 2014-03-04
Could you describe in a little detail **how** you **upgraded** from 12.10 to 13.10? My impression is that if you choose the upgrade route, you **first must** upgrade to 13.04 and **then** to 13.10.

---

### Post by monkeybrain20122 on 2014-03-04
You should not "upgrade'. Should have done a clean install.

---

### Post by sparker12 on 2014-03-04
Yes, you're right. It was 13.04 to 13.10.

---

### Post by sparker12 on 2014-03-04
> **monkeybrain20122 said:**
> You should not "upgrade'. Should have done a clean install.

20/20 hindsight is great but it doesn't help fix my current problem. The next LTS will definitely be a clean install.

---

### Post by QIII on 2014-03-04
Hello!

Could you please post the contents of /etc/apt/sources.list and list the names of the files in /etc/apt/sources.list.d?

You probably have a hodgepodge of things in there.  If we can start clearing out some of those, we may be able to get you to a point where you can do an update and then take your time removing some things.

---

### Post by sparker12 on 2014-03-05
> **QIII said:**
> Hello!

Could you please post the contents of /etc/apt/sources.list and list the names of the files in /etc/apt/sources.list.d?

You probably have a hodgepodge of things in there.  If we can start clearing out some of those, we may be able to get you to a point where you can do an update and then take your time removing some things.
Thank you very much for trying to help. Here is the /etc/apt/sources.list :
```

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
deb [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy main restricted
deb-src [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-updates main restricted
deb-src [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy universe
deb-src [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy universe
deb [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-updates universe
deb-src [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy multiverse
deb-src [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy multiverse
deb [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-updates multiverse
deb-src [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main

deb [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-security main restricted
deb-src [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-security main restricted
deb [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-security universe
deb-src [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-security universe
deb [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-security multiverse
deb-src [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-security multiverse

deb [http://mirror.netspace.net.au/pub/ubuntu/](http://mirror.netspace.net.au/pub/ubuntu/) saucy-proposed restricted main multiverse universe

```
**And here is the list of names in this directory ( **/etc/apt/sources.list.d)
```

alexmurray-indicator-sensors-quantal.list
alexmurray-indicator-sensors-quantal.list.distUpgrade
alexmurray-indicator-sensors-quantal.list.save
cnav-ppa-precise.list
cnav-ppa-precise.list.distUpgrade
cnav-ppa-precise.list.save
cnijfilter.list
cnijfilter.list.distUpgrade
cnijfilter.list.save
danielrichter2007-grub-customizer-precise.list
danielrichter2007-grub-customizer-precise.list.distUpgrade
danielrichter2007-grub-customizer-precise.list.save
ferramroberto-sopcast-precise.list
ferramroberto-sopcast-precise.list.distUpgrade
ferramroberto-sopcast-precise.list.save
ffmulticonverter-stable-precise.list
ffmulticonverter-stable-precise.list.distUpgrade
ffmulticonverter-stable-precise.list.save
gnome3-team-gnome3-next-saucy.list
gnome3-team-gnome3-next-saucy.list.save
gnome3-team-gnome3-saucy.list
gnome3-team-gnome3-saucy.list.save
jfi-psensor-unstable-quantal.list
jfi-psensor-unstable-quantal.list.distUpgrade
jfi-psensor-unstable-quantal.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
michael-gruz-canon-2012-precise.list
michael-gruz-canon-2012-precise.list.save
michael-gruz-canon-precise.list
michael-gruz-canon-precise.list.save
michael-gruz-canon-trunk-precise.list
michael-gruz-canon-trunk-precise.list.save
phablet-team-tools-precise.list
phablet-team-tools-precise.list.distUpgrade
phablet-team-tools-precise.list.save
pinta-maintainers-pinta-stable-precise.list
pinta-maintainers-pinta-stable-precise.list.distUpgrade
pinta-maintainers-pinta-stable-precise.list.save
r5u87x-loader-ppa-precise.list
r5u87x-loader-ppa-precise.list.distUpgrade
r5u87x-loader-ppa-precise.list.save
ubuntu-x-swat-x-updates-saucy.list
ubuntu-x-swat-x-updates-saucy.list.save
venerix-blug-precise.list
venerix-blug-precise.list.distUpgrade
venerix-blug-precise.list.save
webupd8team-java-precise.list
webupd8team-java-precise.list.distUpgrade
webupd8team-java-precise.list.save
webupd8team-unstable-precise.list
webupd8team-unstable-precise.list.distUpgrade
webupd8team-unstable-precise.list.save
yannubuntu-boot-repair-precise.list
yannubuntu-boot-repair-precise.list.distUpgrade
yannubuntu-boot-repair-precise.list.save

```
Over to you. I just don't know where to start. Funny thing is I am still able to update etc.

---

### Post by artie3 on 2014-03-05
I'm a newbie here, but I LOVE Ubuntu! My mentor got me up and running fast, without his tech support, I'd still be running Windows!! 

Anyway, one of the first things he taught me is to do a clean install every time-no exceptions. Maybe some day an 'upgrade' will work, but today a clean install is the best policy.

GL to you.

Artie

---

### Post by deadflowr on 2014-03-05
You have a rather long list of ppas.
When you run
```
sudo apt-get update
```
do you get any errors?

I think you should disable and remove all the ppas that are not for saucy.

Open the program called " Software and Updates"
Go to the section(tab) "Other Software"
Uncheck every line except the one for gnome3 team and x swat
(those are the ones for saucy)

Upgrading works fine, and suggestions of doing a clean install are rather quick to judge.

It seems from my take that it is possible you might not have fully followed the advice of some of the ppa you have installed and purged them before running the release-upgrade.
By not purging, you might get a workable system, but are sorts of package conflicts can arise, as seen here.
Well, my two cents anyway.

---

### Post by sparker12 on 2014-03-05
Hi deadflowr, I ran sudo apt-get update and there were no errors. I also did a test - One of the items in the broken package list was Banshee 2.6.1-2 ubuntu1. I tried a re-install and that didn't work as it remained in the broken package list. I then did a "complete removal" and then reinstalled it. I thought all the dependencies etc would have been installed and it would have fixed it but it didn't. It showed up again in the broken package list! Banshee works but won't shut down from its controls. I wonder what's wrong there. 

I have done many upgrades in the past without problems. Clean installs don't always go well either.

---

### Post by Bashing-om on 2014-03-05
sparker12; Hi !

It is not a good thing to mix releases ( all those others in your /etc/apt/sources.list.d directory).
Concur with deadflowr's apt advisement to disable all non-suacy sources, run the update/upgrade routine and at that time I bet it runs clean.
Then is the painstaking process trying to update those older sources to what might be available for suacy - one at a time. Dealing with the dependency problems - one at a time.

[INDENT][INDENT]just my 2 pounds worth
[/INDENT][/INDENT]

---

### Post by oldos2er on 2014-03-05
Just FYI if you ever do a version upgrade again, disable all PPAs first.

---

### Post by sparker12 on 2014-03-05
Thanks oldos2er, I will remember next time. My thanks goes out to all that helped. Happily I don't have any more broken packages. I disabled other PPA's as advised and ran sudo apt-get update and upgrade-there were no problems-and then had a closer look at some of the broken ones through synaptic. I  looked at the properties of some of them and noted the things they "broke" and replaced. Nearly all of them belonged to empathy. I use Thunderbird anyway as my mail client so I completely removed empathy and all the broken packages went away. Another noob victory! Once again I love the help Ubuntu users can get from experienced and knowledgable people.


Edit: Spoke too soon. Empathy removal cleaned up a lot but there are heaps more.

---

### Post by QIII on 2014-03-05
... and uninstall any proprietary drivers.

---

