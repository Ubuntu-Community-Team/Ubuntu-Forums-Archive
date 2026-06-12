---
title: "An error occured"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by TheLittleNapoleon on 2012-04-14
The error reads as below when i try opening Synaptic packet Manager:

E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I used the terminal /etc/apt/sources.list But responds permission denied. I used terminal as administrator : gksudo gedit /etc/apt/sources.list. And the output was as follows:

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric main restricted
deb-src [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-updates main restricted
deb-src [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric universe
deb-src [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric universe
deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-updates universe
deb-src [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric multiverse
deb-src [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric multiverse
deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-updates multiverse
deb-src [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-security main restricted
deb-src [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-security main restricted
deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-security universe
deb-src [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-security universe
deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-security multiverse
deb-src [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://mirror.nus.edu.sg/ubuntu/](http://mirror.nus.edu.sg/ubuntu/) oneiric-proposed restricted main multiverse universe
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://dl.google.com/linux/deb/stable](http://dl.google.com/linux/deb/stable) non-trees
deb-src [http://dl.google.com/linux/deb/stable](http://dl.google.com/linux/deb/stable) non-trees

Line 56 is the last line. Please help what is wrong here. i cannot install or update software.

---

### Post by arochester on 2012-04-14
deb [http://dl.google.com/linux/deb/stable](http://dl.google.com/linux/deb/stable) non-trees
deb-src [http://dl.google.com/linux/deb/stable](http://dl.google.com/linux/deb/stable) non-trees

**non-free**

---

### Post by TheLittleNapoleon on 2012-04-14
I changed both non-trees to non-free but i still cannot access synaptic Package manager or update and install software

---

### Post by arochester on 2012-04-14
Did you save and close your sources list? And then try again?

Try the following commands: 
> sudo apt-get update 
sudo apt-get upgrade

EXACTLY what error messages do you get now. Can you copy and paste the results here?

---

### Post by TheLittleNapoleon on 2012-04-14
I am using an Oracle virtual box to run this OS, can that have an effect to the problem i am facing.

---

### Post by TheLittleNapoleon on 2012-04-14
This is what am getting when i run the above commands

cliftnet@cliftnet-VirtualBox:~$ apt-get update
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
cliftnet@cliftnet-VirtualBox:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
cliftnet@cliftnet-VirtualBox:~$

---

### Post by arochester on 2012-04-14
There's a space missing. (DUH!)

It is not 
deb [http://dl.google.com/linux/deb/stable](http://dl.google.com/linux/deb/stable) non-trees
deb-src [http://dl.google.com/linux/deb/stable](http://dl.google.com/linux/deb/stable) non-trees

It should be
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

A space between deb/ and stable

Have you got the Google key? In a Terminal run
wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -

---

### Post by TheLittleNapoleon on 2012-04-14
Thank you so much. Its working now. Its been a week trying to fix this problem on my own.

---

