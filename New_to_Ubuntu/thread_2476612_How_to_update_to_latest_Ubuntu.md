---
title: "How to update to latest Ubuntu?"
date: 2022-07-01
forum: New to Ubuntu
---

### Post by billy3xs on 2022-07-01
When i try:

sudo apt-get [COLOR=#417394]update[/COLOR]
sudo apt-get upgrade
sudo apt-get dist-upgrade

I get:
E: The repository 'https://deb.etcher.io stable Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


And I don't know how to get out of this box!  LOL    ):P

---

### Post by QIII on 2022-07-01
The commands you are using will not update your installation to the latest Ubuntu.  What you have there will upgrade the packages in your current release if there are any to upgrade.

Or are you attempting to get everything updated so you can upgrade to 22.04?

The error you are getting indicates that a third-party repo does not have a package or some file for your release.  Since that is not an official Ubuntu repo, there is little for you to do other than complain to the maintainer or remove that repo from you sources before you can update.

---

### Post by billy3xs on 2022-07-01
Yes it's kind of a mess. My goal is to be up to date with the current release and a clean setup.
most of this mess is because I was away for some time, I do like to keep it updated and obviously have to relearn how to do that.

Yes a clean install of [COLOR=#000000]22.04 would be nice...
thanks for your time, I'm really trying come over to the open source side!

So, I can look for the [/COLOR][COLOR=#000000]https://deb.etcher.io  and see if I can delete it...

[/COLOR]Ok removed [COLOR=#000000]etcher.io
ran that last stuff again with I think success:

[/COLOR][COLOR=#000000]sudo apt-get [/COLOR][COLOR=#417394]update[/COLOR]
[COLOR=#000000]sudo apt-get upgrade[/COLOR]
[COLOR=#000000]sudo apt-get dist-upgrade

[/COLOR]Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) focal InRelease       
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease              
Hit:4 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) focal InRelease           
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-security InRelease             
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease            
Hit:7 [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) stable InRelease                       
Ign:8 [https://repo.vivaldi.com/stable/deb](https://repo.vivaldi.com/stable/deb) stable InRelease               
Hit:9 [https://repo.vivaldi.com/stable/deb](https://repo.vivaldi.com/stable/deb) stable Release
Reading package lists... Done

So maybe I can update to 22.04 now, can someone tell me the command for that or if that is the way to proceed?

So...
~$ sudo apt full-upgrade
[sudo] password for billy2xs: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

~$ sudo apt --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

billy2xs@billy2xs-W150ER:~$ sudo apt install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version (1:20.04.10.10).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

billy2xs@billy2xs-W150ER:~$ lsb_release -a
[COLOR=#ff0000]No LSB modules are available.[/COLOR]
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.4 LTS
Release:    20.04
Codename:    focal

---

### Post by guiverc on 2022-07-01
The upgrade from Ubuntu 20.04 LTS to Ubuntu 22.04 LTS has not opened yet.

If you look at the release announcement for Ubuntu 22.04 LTS, (*eg. [here]("https://fridge.ubuntu.com/2022/04/21/ubuntu-22-04-lts-jammy-jellyfish-released/")*), you'll read

> Users of Ubuntu 21.10 will soon be offered an automatic upgrade to  22.04. Users of 20.04 LTS will be offered the automatic upgrade when  22.04.1 LTS is released, which is scheduled for the 4th of August. For  further information about upgrading, see:

Yes there are many links in the announcements (*I won't copy/paste them as you can read the link I provided yourself*) which include links and commands that allow the upgrade to be *forced*, but I'd not recommend doing that if you don't already know how.

If you prize *stability*, I'd recommend waiting until the *release-upgrade* process is open, which is a determination made by the *Ubuntu Release Team* to ensure *stability for existing users*.

---

### Post by billy3xs on 2022-07-01
Oh, great news, thank you

---

