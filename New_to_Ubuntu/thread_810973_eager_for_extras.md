---
title: "eager for extras"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by westentertainer on 2008-05-28
im up and running now 7.10 i would like a dock on desktop and them cracking beryl fx  how do i get them and install ive noticed its a lot different from windows   thanks in advance

---

### Post by SunnyRabbiera on 2008-05-28
well if you are using 7.10 then you already have compiz installed, compiz fusion is installed by default in gutsy as beryl has been dis continued and merged back with compiz.
as for a dock, there is always AWN.

---

### Post by doorknob60 on 2008-05-28
This should be the best way to get AWN (dock) wokring (with applets, which for some reason aren't in the official repositories, and are pretty important). [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

---

### Post by Joeb454 on 2008-05-28
To edit the Compiz-Fusion settings, install compizconfig-settings-manager (which can then be found in System > Preferences > Advanced Desktop Effects) from synaptic, or by typing ```
sudo apt-get install compizconfig-settings-manager
``` in a terminal.

Then you may want to look into AWN (It's the easiest dock to install, yet quite well featured :))

---

### Post by Mahinva on 2008-05-31
> **doorknob60 said:**
> This should be the best way to get AWN (dock) wokring (with applets, which for some reason aren't in the official repositories, and are pretty important). [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

Hey there, thanks for that link - I think it's helped more than the other guides/information I've stumbled upon. I'm still having trouble installing the extras package though. I'm running Hardy Heron and am a new user so I may just be over-explaining things (sorry!)

In following [_this_]("http://http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive") guide (steps 1-9) I get stuck between 8-9 - in short, package material was downloaded and updated (step 8 ) but when I try to install the packages, I get nowhere.

In the Synaptic Package Manager, searching for "awn" gives a number of files.

If I try to install "awn-extras-applets-trunk" (version Hardy), I get a warning that asks if I want to "Mark additional required changes?" The change is installing "libwebkit-1.0-1" which is "Not Authenticated".

When I choose the "Mark" option, I get the following error: "Could not mark all packages for installation or upgrade". The error's description states: "awn-extras-applets-trunk: Depends: libawn0-trunk but it is not going to be installed". After closing out the window (only option), I'm back to the Package Manager.

I've also got awn-core-applets-bzr in the Package Manager, but that's for Gusty. If I mark this file for installation, it states that the following will be removed: "avant-window-navigator", "awn-manager" and libawn0. It will install "libawn0-brz".

According to _[this]("http://wiki.awn-project.org/Awn_Extras:Installation#Binary_Packages.2FRepositories")_, I've got the extras packages released by the Awn Testing Team AND reacocard in my Synaptic Package Manager, but neither have been installed.

What can I do at this junction to get the extras successfully installed? I installed Awn successfully without problems - I am running awn-manager 0.2.1 according to the Synaptic Package Manager.

Edit: I bumbled around some more and tried the Terminal command: "sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr". It worked; I've now got the core applets installed. :)

---

