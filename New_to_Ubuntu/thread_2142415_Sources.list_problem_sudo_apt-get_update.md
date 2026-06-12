---
title: "Sources.list problem sudo apt-get update"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by Liffxng on 2013-05-05
I have problem with updating.. :(

Thank for your helps.
 I use ubuntu 13.04 but why is it said 12.10 ? 

> W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


E: Some index files failed to download. They have been ignored, or old ones used instead.




---

### Post by BluNova on 2013-05-05
Have you updated already. Or is this in the update process

---

### Post by deadflowr on 2013-05-05
You need to into software sources.
System settings > software sources or software and updates and uncheck the cdrom options in the 'other software' sub-section.
They should be the top listed items.

Or

Open a text editor in root and open the file /etc/apt/sources.list and put a # symbol next to the cdrom listings.

Save and run sudo apt-get update or run check in update manager/software-updater.

---

### Post by Liffxng on 2013-05-05
> **BluNova said:**
> Have you updated already. Or is this in the update process
this is the process when i update.

> deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-proposed main restricted universe multiverse


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
this is my source.list but where should I add the #?




---

### Post by deadflowr on 2013-05-05
^ I would add the comment to any line with deb:cdrom.

Then go from there and see if any other errors pop up during apt-get update.

Edit and added: You might also want to add comments to any lines that contain quantal, as you're now running raring and the repos will conflict.

---

### Post by BluNova on 2013-05-05
> [COLOR=#000000]*deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted*[/COLOR]
This line change it to
> #[COLOR=#000000]*deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted*[/COLOR]

---

### Post by Liffxng on 2013-05-05
> **BluNova said:**
> This line change it to
[/I][/COLOR]


thanks it's worked xD Case close.

---

