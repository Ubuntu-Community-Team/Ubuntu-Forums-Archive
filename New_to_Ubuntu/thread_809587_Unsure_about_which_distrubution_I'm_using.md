---
title: "Unsure about which distrubution I'm using"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by decay85 on 2008-05-27
title says all. What do I do to find out?


All help will be much appreciated!

NOTE: Still need help!

---

### Post by Joeb454 on 2008-05-27
Well is it Ubuntu?

If so click System > About Ubuntu, that should tell you :)

---

### Post by PinkFloyd102489 on 2008-05-27
Open a terminal and enter:

```
uname -a 
```


For example, mine says:

Linux ubuntu 2.6.24-17-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

---

### Post by decay85 on 2008-05-27
Thanks much! I found out I'm running Edgy Eft. How do I upgrade (or whatever it's called in linux language) to the latest version of Ubuntu?

---

### Post by sayakb on 2008-05-27
```
lsb_release -a
```

How to upgrade:
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

---

### Post by decay85 on 2008-05-27
When I try to update my system, I get the message:


"Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz) 404 Not Found"

It says such problems happen because there's something wrong with the network connection. I really don't think that's the problem, as my internet connection is working just fine at the moment.

---

### Post by Joeb454 on 2008-05-27
Thats because Edgy is unsupported now, you will most likely need to download a new CD and burn that to install the latest version :)

This will of course require a clean install

---

### Post by sayakb on 2008-05-27
Download and burn the Hardy ISO on a disk. Now, insert the disk in Edgy and it would start an update manager that would prompt for distribution update. You might try upgrading from there. But it is much better to do a clean install rather than upgrading since upgrading does not work out well in most cases.

---

### Post by phoenix_abhi on 2008-05-27
> **Joeb454 said:**
> Thats because Edgy is unsupported now, you will most likely need to download a new CD and burn that to install the latest version :)

This will of course require a clean install

This will do for fiesty and GUTSY even for Hardy also. But I suggest u 2 do a GUTSY Upgrade in this way and automatically u will get the Hady from Fiesty

**Manual upgrades to Feisty**

Please note - this method is less reliable. If you use this method, you MUST be prepared to fix problems manually, such as packages being unexpectedly removed, apt crashing unexpectedly, etc. It is highly recommended that you use the automatic upgrade instructions on FeistyUpgrades instead.

1.

Make sure that you have the packages "ubuntu-minimal" and "ubuntu-standard" installed, regardless of whether you're using Ubuntu, Kubuntu, Xubuntu or Edubuntu:
*

Example:

sudo apt-get install ubuntu-minimal ubuntu-standard

2.

The appropriate desktop package for your version of Ubuntu must also be installed. They are "ubuntu-desktop" for Ubuntu, "kubuntu-desktop" for Kubuntu, "xubuntu-desktop" for Xubuntu, and "edubuntu-desktop" for Edubuntu:
*

Example:

For Ubuntu

sudo apt-get install ubuntu-desktop

For Kubuntu

sudo apt-get install kubuntu-desktop

For Xubuntu

sudo apt-get install xubuntu-desktop

For Edubuntu

sudo apt-get install edubuntu-desktop

3.

Edit your /etc/apt/sources.list as root. Change every occurrence of edgy to feisty. It is also recommended that you remove or disable any extra repository that may have been added besides the Ubuntu repositories.
*

Long route: Use your preferred editor. If you have a CD-ROM line in your file, then remove it.

For Ubuntu.

gksudo gedit /etc/apt/sources.list

For Kubuntu.

kdesu kate /etc/apt/sources.list

For Xubuntu.

gksudo mousepad /etc/apt/sources.list

In any terminal program.

sudo nano /etc/apt/sources.list
sudo vi /etc/apt/sources.list

*

Shortcut:

sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list

NOTE: This might not remove old CD-ROM lines. Manual inspection is suggested after running this command. (see Long Route)
4.

If you have the alternate install CD, you can save bandwidth by loading the CD into your CD-ROM drive and using:
*

sudo apt-cdrom add

5.

Perform the upgrade:
*

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade

OR, You can also use Aptitude:

sudo aptitude update && sudo aptitude dist-upgrade && sudo aptitude dist-upgrade

NOTE: The first run of dist-upgrade will upgrade everything except for upstart. After this a second dist-upgrade will finish the upgrade.
6.

Just to be totally sure that everything is installed properly, run these commands:
*

sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

Running dist-upgrade again is done to ensure that no packages are left to install or upgrade. In some cases, certain packages fail to install even after running dist-upgrade the second time.
7.

Reboot in order to effect all changes. (kernel upgrades, upstart, etc...)

Notes

*

IT IS WORKED FOR ME . IF U WANT GUTSY OR HARDY REPLACE ALL FIESTY WITH GUTSY OR HARDY

I do not remember the name of the version exactly, typed in the order of release
:guitar:

:lolflag:

---

### Post by philinux on 2008-05-27
Do some backing up first.:)

---

### Post by Joeb454 on 2008-05-27
@ **phoenix_abhi**

Why would I want to download the Fiesty or Gutsy CD to upgrade to Hardy - when I could just clean install Hardy?

---

### Post by sayakb on 2008-05-27
After getting hit hard on the face twice, I would say that that clean install is better than doing an upgrade.. ;)

---

### Post by Joeb454 on 2008-05-27
I'll agree with LinuxIsInnovation on this one ;)

---

### Post by philinux on 2008-05-27
Home on it's own partition then clean install.

---

### Post by phoenix_abhi on 2008-05-28
> **Joeb454 said:**
> @ **phoenix_abhi**

Why would I want to download the Fiesty or Gutsy CD to upgrade to Hardy - when I could just clean install Hardy?

A clean install is the best solution those who have nothing in UBUNTU partition or have a separate home. But most of the dual boot install Ubuntu in a single partition like I did :(

In that case upgrade is the only solution. :)

And this is not about d/l CD ?

---

