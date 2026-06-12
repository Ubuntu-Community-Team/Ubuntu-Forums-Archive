---
title: "Banshee 1.2.1 install problems"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by homerwookey on 2008-10-14
Hi I have tried to install the latest Banshee version, and these are the results i'm getting on the terminal
sudo apt-get install banshee-1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  banshee-1: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
E: Broken packages

any help would be happily welcomed!

---

### Post by LowSky on 2008-10-14
The newest Banshee version is availible for Intrepid Ibex (8.10) to be realeased in 2 weeks
If you "really" want now it you can follow these instructions
[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

---

### Post by homerwookey on 2008-10-14
Have tried that but am getting same response
ps i am using hardy 8.04

---

### Post by ChildOfMana on 2008-10-14
Just a thought but did you make sure to change the drop-down box (on the page linked to in the post above) from Intrepid Ibex to Hardy Heron?

The line you added to sources.list should read;

> deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main

---

### Post by mc4100 on 2008-10-14
Seems like the **Hardy** PPA is having issues with unmet dependencies: try the **Gutsy** one.

---

### Post by mc4man on 2008-10-14
1.20.5 is the latest hardy version, maybe ck. why you haven't updated or are unable to update. See if in software sources the first 4 boxes are checked under 'ubuntu software' and the first 2 under 'updates'

Otherwise maybe go here, download and try to install, the error message could point to the reason.
[http://packages.ubuntu.com/hardy-updates/libpango1.0-0](http://packages.ubuntu.com/hardy-updates/libpango1.0-0)

---

### Post by homerwookey on 2008-10-15
Thankyou all, Took Mc4mans advice and downloaded the recommended updates (all 299 of them!) , tried again et voila!
Appreciate  all your help, until next time...

---

