---
title: "Reinstalling with complications... un-dual booting?"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by 25tom on 2012-08-19
Hi,
I am currently using a rather old laptop, with just over 400MB RAM and a Celeron processor. I am happily running (if a little slowly) Ubuntu Natty with the GNOME 2 desktop. I dual boot with Lubuntu Oneiric, which gives me some speed if I just want to do simple tasks.
However, I think that an update to Ubuntu Precise would be too much for my computer, and I'm wondering if it's possible to run it, in theory, with the GNOME desktop with my laptop's current specs.
If this is not possible, is it possible to install Lubuntu Precise, replacing both existing OSs, and keeping my programs?

Any help/advice much appreciated :)

---

### Post by 25tom on 2012-08-19
I'm quite new to Linux, so I posted this in the Beginner forum.

---

### Post by oldfred on 2012-08-19
I think the full Ubuntu's gui would be too much for a system with 400MB.

512MB  is suggested for use with desktop. 
[https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html](https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html)  

Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
I'd suggest to check amjjawad's thread (Lubuntu One Stop Thread) and you'll find many useful information.
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

You can export a text list of all installed applications. But if you have full Ubuntu it will install those applications which may be more than Lubuntu.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

It is a text file. I found with my new installs I was still installing python2.5. So you may want to review list and remove older or larger apps. You may have Openoffice which is now LIbreOffice but with Lubuntu  you may just want Gnumeric and AbiWord.

Full dpkg list is every app including all the support ones, so it is very long. This is a shorter list, but I do not think it is easy to use to reinstall:
Top level only - no depends
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

---

### Post by 25tom on 2012-08-20
1) OK, so using the first dpkg command with the options you specified will generate a list of packages, and the second one, with the apt-get commands, will reinstall them?

2) Also, if, in theory, one puts the install disc for Lubuntu in a computer running Ubuntu, and when it asks what to do with the existing Ubuntu OS, what happens if you tell it to upgrade the OS? Would that leave apps intact and convert the Ubuntu OS into a Lubuntu one? Or is it not that simple?

---

### Post by oldfred on 2012-08-20
Upgrade should work. 

It just that I did upgrades from 6.06 thru 9.04 each 6 months and always seemed to have some issue. And system then had a lot of cruft. New clean install of 9.10  then was an automatic houseclean, but I kept old install to reboot into in an emergency. The install of 9.10 was so good, that I only do clean installs to a new 25GB partition now and have data in separate partitions.

---

### Post by 25tom on 2012-08-21
Hmm, yes, I see what you mean about doing a clean install - problem for me is that my HDD is only 50GB. Ah well, I'm now experimenting with LXDE on top of Ubuntu - gives some speed yet leaves the GNOME desktop alone so I can still use it from time to time.
Thanks for advice - maybe I need a bigger HDD!

---

### Post by oldfred on 2012-08-21
I do not trust drives for any more than 3 or 4 years even those with 5 year warranties. So I then buy a new drive and they usually are a lot larger & I have lots of room to reorganize. I still use older drive but not for main system.

---

### Post by 25tom on 2012-08-21
Hmm, my HDD is about 7 years old as far as I know... I definitely need a new one then! Thanks again for advice, it is much appreciated!

---

### Post by black veils on 2012-08-21
if you are really reluctant to do a fresh install over the hdd, you could use the lxde over ubuntu as you now are, use gparted from live media (cd, dvd or usb) and delete the lubuntu partition, then expand the ubuntu partition. then upgrade ubuntu from within the system.

but in doing all this, you could make a mistake and need to fresh install. and upgrades seem like they can be more hassle than they are worth.

---

