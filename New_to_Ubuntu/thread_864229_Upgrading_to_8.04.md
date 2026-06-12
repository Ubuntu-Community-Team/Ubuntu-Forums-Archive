---
title: "Upgrading to 8.04"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by maroonedsorrow on 2008-07-19
I have a laptop that has Ubuntu 7.04 loaded, that I have tried to upgrade first to 7.10, and then to 8.04, using the Update Manager. The process continued fine until about 10 minutes from the end, then it froze. When I looked at the terminal below, it said:

```
Setting up belocs-locales-bin (2.4.2ubuntu7) ...
Setting up locales (2.7.9-4) ...
Installing new version of config file /etc/belocs/iso-639.def ...
Generating locales...
  en_AU.UTF-8...
```

What does this mean and how can I solve it, because this is the third time this has happened (at this same place in the upgrade) in two days, and it is driving me spare.

---

### Post by bumanie on 2008-07-19
You can't upgrade two distro's ahead. You need to update 7.10 first, then to 8.04. I would advise downloading an 8.04 .iso and installing fresh. Save anything important first. Some people find upgrading every times works OK, others find more than one upgrade in a row causes beakages - up to you, but certainly to upgrade it is 7.04 --> 7.10 --> 8.04.

---

### Post by maroonedsorrow on 2008-07-19
> **bumanie said:**
> You can't upgrade two distro's ahead. You need to update 7.10 first, then to 8.04. I would advise downloading an 8.04 .iso and installing fresh. Save anything important first. Some people find upgrading every times works OK, others find more than one upgrade in a row causes beakages - up to you, but certainly to upgrade it is 7.04 --> 7.10 --> 8.04.

Sorry, I didn't put that in the original post; I did backup all important data and upgrade to 7.10 first, before trying to upgrade to 8.04.  Have edited the OP.

---

### Post by bumanie on 2008-07-19
Oh, that's OK, you've done it the correct way. I haven't got an answer and there is no bug reports inlaunchpad for this. There was a very old one, but it resolved (spontaneously apparently) before a fix was investigated and thus the bug went no further. Sorry, can't help other than suggesting downloading an 8.04 .iso and trying a fresh installation. Hope someone else may know.

---

### Post by phoenix_abhi on 2008-07-19
Manual upgrades to hardy

Please note - this method is less reliable. If you use this method, you MUST be prepared to fix problems manually, such as packages being unexpectedly removed, apt crashing unexpectedly, etc. It is highly recommended that you use the automatic upgrade instructions on Hardy Upgrades instead.

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

Edit your /etc/apt/sources.list as root. Change every occurrence of fiesty to hardy. It is also recommended that you remove or disable any extra repository that may have been added besides the Ubuntu repositories.
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

sudo sed -e 's/\sfiest/ hardy/g' -i /etc/apt/sources.list

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

If run a manual upgrade and you have apache2 and php5 installed, make sure to start apache before the upgrade (/etc/init.d/apache2 start). 
*

If you do not have the admin group on your system  it will be added during the upgrade. Make sure to add your sudo user(s) to it.
*

If you have pango-libthai installed, remove it before the upgrade
*

You may want to run /usr/lib/python2.5/site-packages/DistUpgrade/apt-autoinst-fixup.py (from the update-manager package) also to fix a common problem with the automatically installed information


**NOTE - Replace the version name according to ur requirement. Do not mind the warning, it worked or me fine.**

---

