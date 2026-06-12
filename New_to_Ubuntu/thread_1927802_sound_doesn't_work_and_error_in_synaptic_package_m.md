---
title: "sound doesn't work and error in synaptic package manager"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by floben on 2012-02-18
I'm completely new to Linux. I installed Lubuntu 11.10 on an old Toshiba laptop which worked fine but the sound doesn't work. Working through the trouble shooting I tried to install the latest LinuxAlsaDriverModules through Synaptic Package Manager. Now, whenever I start the Synaptic Package Manager I get the following error message:

E: Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-audio-dev-ppa-oneiric.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Any help on how to correct that error and get the sound to work would be much appreciated.

---

### Post by Rodney9 on 2012-02-18
To fix Synaptic

Go to Menu - Preferences - Software Sources - Other Sources

and un-check ubuntu-audio-dev-ppa-oneiric.list

Then Menu - Accessories - LXTerminal 

and insert this code - ```
sudo apt-get update && sudo apt-get upgrade
```

To get sound working go to Menu - Accessories - LXTerminal and insert this code - ```
alsamixer
``` and check everything is checked, use the m key to to turn on or off.

If still having audio problems these two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by floben on 2012-02-18
Thank You Rodney!

I've unchecked two lines under the tab "other software" in "software sources" - they are:

[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) oneiric main
[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) oneiric main (Source Code)

but when I put in the code in LXTerminal the two Errors still appear:

E: Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-audio-dev-ppa-oneiric.list
E: The list of sources could not be read.

Anything else I need to do?

Thanks in advance!

---

### Post by androssofer on 2012-02-18
> **floben said:**
> Thank You Rodney!

I've unchecked two lines under the tab "other software" in "software sources" - they are:

[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) oneiric main
[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) oneiric main (Source Code)

but when I put in the code in LXTerminal the two Errors still appear:

E: Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-audio-dev-ppa-oneiric.list
E: The list of sources could not be read.

Anything else I need to do?

Thanks in advance!

looks to me as if your source list got corrupt...

post the first few lines of your file:

```
/etc/apt/sources.list.d/ubuntu-audio-dev-ppa-oneiric.list
```

and perhaps we can spot the corruption easily enough...

---

### Post by floben on 2012-02-18
When I type in the code

/etc/apt/sources.list.d/ubuntu-audio-dev-ppa-oneiric.list 

into LXTerminal the result is:

bash: /etc/apt/sources.list.d/ubuntu-audio-dev-ppa-oneiric.list: permission denied

Anything I did wrong?

---

### Post by Rodney9 on 2012-02-19
Go to Menu - Accessories - File Manager 

Click on Places 

Select Directory Tree go to etc then apt  

Right click on sources.list select Leafpad then copy that.

Rodney

---

### Post by floben on 2012-02-19
Thanks! 
Here is the copy of the sources.list file:


# deb cdrom:[Lubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

---

### Post by oldos2er on 2012-02-19
/etc/apt/sources.list is fine, it's /etc/apt/sources.list.d/ubuntu-audio-dev-ppa-oneiric.list we need to see. ```
cat /etc/apt/sources.list.d/ubuntu-audio-dev-ppa-oneiric.list
```

---

### Post by floben on 2012-02-19
For the file /etc/apt/sources.list.d/ubuntu-audio-dev-ppa-oneiric.list I get the following:

# deb [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) oneiric main
# deb-src [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) oneiric main
n

---

### Post by floben on 2012-02-19
Well - I got the sound to work, through alsamixer and also figured out that there is a little dial on the side of the laptop where I can adjust the volume - great - thanks for all the help!

Still no luck with synaptic package manager though. Please let me know if you need any more information.

---

### Post by cortman on 2012-02-19
> **floben said:**
> For the file /etc/apt/sources.list.d/ubuntu-audio-dev-ppa-oneiric.list I get the following:

# deb [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) oneiric main
# deb-src [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) oneiric main
n

Very simple- that "n" on a line by itself is what's fouling it up. Open a terminal and run

```
gksu leafpad /etc/apt/sources.list.d/ubuntu-audio-dev-ppa-oneiric.list
```

Delete that "n", save, and run

```
sudo apt-get update
```

That should fix that error.

---

### Post by floben on 2012-02-20
It's fixed - THANK YOU all for your help. And I learned a lot about getting around in what for me is still a new but maybe now not so unfamiliar system.

---

