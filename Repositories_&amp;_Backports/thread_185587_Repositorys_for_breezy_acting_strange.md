---
title: "Repositorys for breezy acting strange ??"
date: 2006-05-31
forum: Repositories &amp; Backports
---

### Post by garenasix on 2006-05-31
the last few days if i run the update manager gets alota failures 

if i do a $sudo apt-get update ; sudo apt-get upgrade 

i get this

garenasix@dhcppc0:~$ $sudo apt-get update ; sudo apt-get upgrade
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
garenasix@dhcppc0:~$

also if i try to edit my source list it will not let me rewrite anything in it and i can't cut and paste another list in it

this got anything with dapper coming out and yous are redoing the servers or do i got a problem ??


heres my soruce list

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

---

### Post by Phlosten on 2006-06-01
whats the '$' at the start? I am not an expert in bash commands but I have not seen this.

I tend to run 'sudo apt-get update && sudo apt-get upgrade'. Try this and it should work.

---

### Post by garenasix on 2006-06-01
[QUOTE=Phlosten]whats the '$' at the start? I am not an expert in bash commands but I have not seen this.

I tend to run 'sudo apt-get update && sudo apt-get upgrade'. Try this and it should work.[/QUOTE]

thank you that worked better :) 
now to find out why i cant edit my soruce list like i useto  ??


garenasix@dhcppc0:~$ sudo apt-get update && sudo apt-get upgrade
Password:
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Get:1 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release.gpg
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Fetched 5B in 4s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
garenasix@dhcppc0:~$

---

