---
title: "Updates and How to Do Them"
date: 2005-01-06
forum: Repositories &amp; Backports
---

### Post by mcollins on 2005-01-06
Hi You all,

I just made the switch to Linux, Ubuntu 4.10. I like it. My computer runs so quiet without the hard drive constantly spinning! It's like I'm on an IBM terminal.

During the install, it prompted me if I wanted to download software from the internet. I clicked "no" because I needed to configure my D-Link bridge from a web browser first (firmware). At the end it says you can run the base-config program to go back to the setup.

Ubuntu says it provides important upgrades for 18 months after each release. I want to install those upgrades. I don't necessarily need the latest version of every program, if it works don't mess with it. But the important stuff I want to upgrade. In Windows you just clicked on "Critical Updates". I read a post saying you just run Synaptic Package Manager, hit "reload", and "mark all upgrades". Well when I hit reload, it looks like it's just reading off my install CD. And by clicking "mark all upgrades", I don't want to install stuff I don't need. Is there something similar to Critical Updates such as in Windows? Should I try to run that base-config program? Or should I not mess with anything and just upgrade with each new CD release.

Matt

---

### Post by nocturn on 2005-01-06
Hi  Matt

Ubuntu 4.10 (Warty) is already 'frozen'.  That means that updates cover security only (critical updates).  This is unless you have added unofficial repositories like backports (not default).

You can use synaptic (like you posted).  or run in a terminal and type:
sudo aptitude update
sudo aptitude upgrade

When you do this, or the synaptic way, you will still see a dialog displaying what it is going to do.

Normally, this will not install newer versions of apps (unless it cannot be avoided) but rather patched versions of the ones you already have.

---

### Post by mcollins on 2005-01-06
I got you. So newer versions of software such as Firefox are just released with the new version of Ubuntu. There's no reason for me to start modifying the system doing backports and stuff. Now to get those patches, I need to switch repositories don't I? because currently it's just pulling stuff off my install CD (there's nothing new on it). Which repository should I do?

---

### Post by tiiim on 2005-01-06
[QUOTE=mcollins]I got you. So newer versions of software such as Firefox are just released with the new version of Ubuntu. There's no reason for me to start modifying the system doing backports and stuff. Now to get those patches, I need to switch repositories don't I? because currently it's just pulling stuff off my install CD (there's nothing new on it). Which repository should I do?[/QUOTE]
 the other repositories should be there by default when you mark updates it will use the cd but it also mainly use the internet does it download anything off the net when you update?

---

### Post by mcollins on 2005-01-06
I clicked Reload (it always says downloading file 4 of 4) but it didn't look like it downloaded anything from the internet. I went ahead and hit "Mark All Upgrades", then "Default Upgrade". In the bottom pane it said "No Package is Selected", so the Apply button was blanked out.

---

### Post by jbh on 2005-01-06
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

terminal:
sudo apt-get update
sudo apt-get upgrade

---

### Post by mcollins on 2005-01-07
This time I unchecked the CD repository, I figured I've got everything I need off it. I checked the Security-Binary Repository. I hit reload and many new packages appeared. I hit Mark All Upgrades, then Default, and this time it actually installed stuff. It brought up a terminal window. I think I did my first Linux upgrade! Wait till I brag about this to my Windows friends and relatives.

Matt

---

### Post by jdodson on 2005-01-07
[QUOTE=mcollins]This time I unchecked the CD repository, I figured I've got everything I need off it. I checked the Security-Binary Repository. I hit reload and many new packages appeared. I hit Mark All Upgrades, then Default, and this time it actually installed stuff. It brought up a terminal window. I think I did my first Linux upgrade! Wait till I brag about this to my Windows friends and relatives.

Matt[/QUOTE]

cool, welcome to the club :D

---

