---
title: "Updating 5.10"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by jcounsel on 2008-08-22
I have a cli (no x-window system) ubuntu 5.10 installation on an old compaq, and I would like to upgrade this to the current 8.xx version.  I have downloaded the iso and burnt it to a CD.

The server I want to upgrade does contain files (SAMBA server) that I use.  If I upgrade using the CD, does that information get deleted and/or removed?  Yes, I have a backup, but I just want to know what to expect :)

I would appreciate any other information you could provide or think would be helpful...

---

### Post by Archmage on 2008-08-22
I think this is the webpage you are looking for:

[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

---

### Post by livestockPimp on 2008-08-22
if you change your apt repositories to look at the cd and do an "apt-get dist-upgrade && apt-get upgrade" then technically everything should be the same.

You will not loose any data, ect.

What to expect is things like samba changing the way the config files work. This will mean samba wont start or wont function properly until this is resolved.

Generally it is not too bad but it can break things like drivers, software raid, LVM, ect.

I would be very surprised if you lost data. it will most likely just be a few hours weeding through things that have broken and repairing configuration files.

---

### Post by jcounsel on 2008-08-22
heh...  it sort of helps...

The version that page starts with is 6.06.  So, here is my path then (correct?):

6.06 Dapper
6.10 Edgy
7.04 Fiesty
7.10 Gutsy
8.04 Hardy


OR, do I have to:

6.06.1
6.06.2
6.10
...


Thanks for the link and information.

---

### Post by livestockPimp on 2008-08-22
6.06 Dapper
6.10 Edgy
7.04 Fiesty
7.10 Gutsy
8.04 Hardy

is technically the correct method.

If you have broadband and a fast connection to the mirrors then I would just edit the /etc/apt/sources.list and change "breezy" to "dapper" and then do the "apt-get dist-upgrade && apt-get upgrade".

This will save you downloading every iso.

The only problem is that edgy has no repositories now since it is considered an "old" distro.

The only place I have found to have these repositories is "old-releases.ubuntu.com"

---

### Post by livestockPimp on 2008-08-22
note: after you change the sources.list you will need to do an "apt-get update" so it is reading the new repositories otherwise it will be using the original ones still...

---

### Post by Sand &amp; Mercury on 2008-08-22
Perhaps a better idea would be to do a clean install with format, then put your backed-up files back aftewards?

---

### Post by jcounsel on 2008-08-22
The reinstall would, likely, be best, but we have no official IT, and I do need to get other work done--while I can install, configure, etc. SAMBA, etc. I would/might save time by simply upgrading...  Of course, I might not...

Thanks for the ideas and info.

---

### Post by chrisccoulson on 2008-08-22
The technically correct upgrade path from Breezy to Hardy is actually:

5.10 -> 6.06 -> 8.04.

This is because you can upgrade LTS to LTS. You shouldn't go through Edgy (6.10) anyway, as support for it has ended and I don't think the mirrors exist for it any more.

---

### Post by LowSky on 2008-08-22
you can go from 6.06 to 8.04 

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by newlinux on 2008-08-22
I strongly recommend you just back up your configuration files, make note of the packages you have installed that you'll want in the new installation and just reinstall. So many things have changed since breezy that you might end up reconfiguring a lot anyway after going through 5.10-6.06-8.04. Also the upgrade will probably take longer than reinstalling (not configuring, just the process).

---

### Post by jcounsel on 2008-08-22
Ladies and Gentlemen:  

I appreciate all of the comments, and the updating/upgrading is underway.  Dapper is downloading, and Hardy is hanging around waiting...

Thanks for saving me time.

---

