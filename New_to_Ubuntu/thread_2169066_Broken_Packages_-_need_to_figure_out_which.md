---
title: "Broken Packages - need to figure out which"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by tyteen4a03 on 2013-08-20
Hi, trying to gnome 3.8 but got this message: [https://gist.github.com/tyteen4a03/76ec7914262e9fcf636d]("https://gist.github.com/tyteen4a03/76ec7914262e9fcf636d\")

Can anyone tell me what to do next?

---

### Post by bapoumba on 2013-08-20
> E: Unable to correct problems, you have held broken packages.

Have you placed some packages on hold ?

Other than that, please post your sources.list, **cat /etc/apt/sources.list** and give some details on how you got there, thanks.

---

### Post by Yougo on 2013-08-20
Do you have Synaptic installed?

if you do, start it (requires password)
on the lower left of the synaptic window, press the button second from the top, that says "Status"

the left panel now groups packages based on their status. one of these groups is called something like "broken packages" (my session is not in English...) select that group, and on the large panel, you should see a list of all the packages that are broken.

from there, we could try to figure out why they're broken and what to do about it :)

---

### Post by tyteen4a03 on 2013-08-20
> **Yougo said:**
> Do you have Synaptic installed?

if you do, start it (requires password)
on the lower left of the synaptic window, press the button second from the top, that says "Status"

the left panel now groups packages based on their status. one of these groups is called something like "broken packages" (my session is not in English...) select that group, and on the large panel, you should see a list of all the packages that are broken.

from there, we could try to figure out why they're broken and what to do about it :)
There are no broken packages group there.

sources.list
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted
deb-src [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring main restricted #Added by software-properties


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring main restricted
deb-src [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring universe multiverse main #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring-updates main restricted
deb-src [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring-updates universe multiverse restricted main #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring universe
deb [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring multiverse
deb [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring-backports main restricted universe multiverse #Added by software-properties


deb [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring-security main restricted
deb-src [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring-security universe multiverse restricted main #Added by software-properties
deb [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring-security universe
deb [http://mirror.easyspeedy.com/ubuntu/](http://mirror.easyspeedy.com/ubuntu/) raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main

I was just trying to install gnome 3.8 when this happened.

---

### Post by ibjsb4 on 2013-08-20
Your sources list look ok.  Try an update and upgrade.

```
sudo apt-get update

and

sudo apt-get upgrade
```

Get any errors?

Also how were you trying to install gnome 3.8?  With the software center or using a command?

---

### Post by tyteen4a03 on 2013-08-21
> **ibjsb4 said:**
> Your sources list look ok.  Try an update and upgrade.

```
sudo apt-get update

and

sudo apt-get upgrade
```

Get any errors?

Also how were you trying to install gnome 3.8?  With the software center or using a command?
No errors at all.

Was using apt-get. If it helps, the power once failed during a software upgrade earlier.

---

### Post by bapoumba on 2013-08-21
> **tyteen4a03 said:**
> No errors at all.

Was using apt-get. If it helps, the power once failed during a software upgrade earlier.

That probably is the explanation. It did complete the upgrade now, so you should be good to go :)

---

### Post by tyteen4a03 on 2013-08-21
> **bapoumba said:**
> That probably is the explanation. It did complete the upgrade now, so you should be good to go :)
Nope, still getting the same errors.

---

### Post by bapoumba on 2013-08-21
> **tyteen4a03 said:**
> Nope, still getting the same errors.

Could you please post them in here again ?

---

### Post by tyteen4a03 on 2013-08-21
The same packages I listed in my first post.

---

### Post by bapoumba on 2013-08-21
But you said that apt-get upgrade did not return any error, so in which context do you get the errors from the first post ?

---

### Post by tyteen4a03 on 2013-08-21
In the context of apt-get install ubuntu-gnome-desktop.

---

### Post by bapoumba on 2013-08-21
> **tyteen4a03 said:**
> In the context of apt-get install ubuntu-gnome-desktop.

```
apt-cache show ubuntu-gnome-desktop
Package: ubuntu-gnome-desktop
Priority: optional
Section: universe/metapackages
Installed-Size: 26
Maintainer: Ubuntu GNOME Developers <ubuntu-gnome@lists.ubuntu.com>
Architecture: i386
Source: ubuntu-gnome-meta
Version: 0.11
```

I'm not quite sure I understand.. ubuntu-gnome-desktop is installed on a standard raring.

If you want gnome 3.8, you need the gnome ppa and there are quite a few problems :
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

---

### Post by tyteen4a03 on 2013-08-25
> **bapoumba said:**
> ```
apt-cache show ubuntu-gnome-desktop
Package: ubuntu-gnome-desktop
Priority: optional
Section: universe/metapackages
Installed-Size: 26
Maintainer: Ubuntu GNOME Developers <ubuntu-gnome@lists.ubuntu.com>
Architecture: i386
Source: ubuntu-gnome-meta
Version: 0.11
```

I'm not quite sure I understand.. ubuntu-gnome-desktop is installed on a standard raring.

If you want gnome 3.8, you need the gnome ppa and there are quite a few problems :
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

Yes, I want GNOME 3.8 instead of Unity. I added the PPA in 13.04.

A few regressions is fine for me.

---

### Post by ibjsb4 on 2013-08-25
> **tyteen4a03 said:**
> The same packages I listed in my first post.

The link in your first post is broken.  You need to post the errors.

---

### Post by bapoumba on 2013-08-25
> **ibjsb4 said:**
> The link in your first post is broken.  You need to post the errors.

Probably something on your end, here is the error from post#1:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
 
The following packages have unmet dependencies:
 gnome-shell : Depends: gir1.2-clutter-1.0 (>= 1.11.11) but it is not going to be installed
               Depends: gir1.2-mutter-3.0 (>= 3.8.3) but it is not going to be installed
               Depends: gir1.2-telepathyglib-0.12 but it is not installable
               Depends: gir1.2-accountsservice-1.0 but it is not installable
               Depends: gir1.2-gkbd-3.0 but it is not installable
               Depends: gir1.2-ibus-1.0 (>= 1.4) but it is not installable
               Depends: gir1.2-nmgtk-1.0 but it is not installable
               Depends: gir1.2-polkit-1.0 but it is not installable
               Depends: gir1.2-telepathylogger-0.2 (>= 0.8.0) but it is not installable
               Depends: gir1.2-upowerglib-1.0 but it is not installable
 ubuntu-gnome-desktop : Depends: gnome-documents but it is not going to be installed
                        Depends: gnome-sushi but it is not going to be installed
                        Depends: gnome-tweak-tool but it is not going to be installed
                        Depends: itstool but it is not installable
                        Depends: yelp-tools but it is not installable
                        Recommends: cheese but it is not going to be installed
                        Recommends: deja-dup-backend-cloudfiles but it is not going to be installed
                        Recommends: deja-dup-backend-s3 but it is not going to be installed
                        Recommends: evolution but it is not going to be installed
                        Recommends: gnome-search-tool but it is not going to be installed
                        Recommends: plymouth-theme-ubuntu-gnome-logo but it is not going to be installed
                        Recommends: plymouth-theme-ubuntu-gnome-text but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by ibjsb4 on 2013-08-25
What ya got in your PPAs?

```
ls /etc/apt/sources.list.d
```

And thanks bapoumba

---

### Post by tyteen4a03 on 2013-08-26
> **ibjsb4 said:**
> What ya got in your PPAs?

```
ls /etc/apt/sources.list.d
```

And thanks bapoumba

gnome3-team-gnome3-raring.list
gnome3-team-gnome3-raring.list.save
google-chrome.list
google-chrome.list.save
nilarimogard-webupd8-raring.list
private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
skype-wrapper-ppa-raring.list
skype-wrapper-ppa-raring.list.save
steam.list
steam.list.save

---

### Post by ibjsb4 on 2013-08-26
I would like to see if any of the other PPAs are conflicting with gnome3 ppa.

Open your [software sources]("https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab") and **UN**check all PPAs except gnome3-team-gnome3 and then do another update.

---

### Post by Jonathan Precise on 2013-08-26
> **tyteen4a03 said:**
> Yes, I want GNOME 3.8 instead of Unity. I added the PPA in 13.04.

A few regressions is fine for me.

The GNOME 3.8 PPA can break some packages (I tried it myself, broke Ubuntu-Tweak and some other packages:(). Try:

```
sudo apt-get install ppa-purge
ppa-purge ppa:gnome3-team/gnome3
```

**In the last command, make sure you see which packages are going to be removed before you press Y (packages that should NOT be removed are stuff like 'ubuntu-desktop', 'ubuntu-branding', 'ubuntu-minimal',  'firefox', and others):!:!!!**

Edit: make sure you enable the gnome-3 ppa before running ppa-purge.

@bapoumba: No, 'ubuntu-gnome-desktop' should not be on a standard ubuntu raring. 'ubuntu-desktop', 'ubuntu-branding' and 'ubuntu-minimal' should though.

---

### Post by tyteen4a03 on 2013-08-28
> **ibjsb4 said:**
> I would like to see if any of the other PPAs are conflicting with gnome3 ppa.

Open your [software sources]("https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab") and **UN**check all PPAs except gnome3-team-gnome3 and then do another update.
Update what?

> **Jonathan Precise said:**
> The GNOME 3.8 PPA can break some packages (I tried it myself, broke Ubuntu-Tweak and some other packages:(). Try:

```
sudo apt-get install ppa-purge
ppa-purge ppa:gnome3-team/gnome3
```

**In the last command, make sure you see which packages are going to be removed before you press Y (packages that should NOT be removed are stuff like 'ubuntu-desktop', 'ubuntu-branding', 'ubuntu-minimal',  'firefox', and others):!:!!!**

Edit: make sure you enable the gnome-3 ppa before running ppa-purge.

@bapoumba: No, 'ubuntu-gnome-desktop' should not be on a standard ubuntu raring. 'ubuntu-desktop', 'ubuntu-branding' and 'ubuntu-minimal' should though.

The following packages have unmet dependencies:
 ppa-purge : Depends: aptitude (>= 0.6.6-1ubuntu1.2) but it is not installable
E: Unable to correct problems, you have held broken packages.

I'm about to just give up and reinstall Ubuntu for the 3rd time...

---

### Post by bapoumba on 2013-08-28
> **Jonathan Precise said:**
> 
@bapoumba: No, 'ubuntu-gnome-desktop' should not be on a standard ubuntu raring. 'ubuntu-desktop', 'ubuntu-branding' and 'ubuntu-minimal' should though.
Hmm, ok, just fresh installed 2 weeks ago, and have not changed much except adding some applications I'm used to (KeepassX, dropbox, xchat and such). I'm not sure with which one it came from. But you are correct (I'm not impliying I ever had a doubt ;))
[http://releases.ubuntu.com/raring/ubuntu-13.04-desktop-i386.manifest](http://releases.ubuntu.com/raring/ubuntu-13.04-desktop-i386.manifest)

---

### Post by Jonathan Precise on 2013-08-29
Disable the Gnome 3 PPA. Then run:

```
sudo apt-get update
sudo apt-get install ppa-purge
```

Enable the PPA again, then run:

```
ppa-purge ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install ubuntu-gnome-desktop
```

---

### Post by tyteen4a03 on 2013-08-30
> **Jonathan Precise said:**
> Disable the Gnome 3 PPA. Then run:

```
sudo apt-get update
sudo apt-get install ppa-purge
```

Enable the PPA again, then run:

```
ppa-purge ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install ubuntu-gnome-desktop
```
Still can't install ppa-purge even with all PPAs disabled.

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ppa-purge : Depends: aptitude (>= 0.6.6-1ubuntu1.2) but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by Jonathan Precise on 2013-08-30
Next time, post the result in code tags:
(CODE)Put your results here.(/CODE)

Replace the parenthesis with brackets to get:
```
Put your results here.
```

As for ppa-purge, try:

```
sudo apt-get install aptitude ppa-purge
```

That should fix the problem.

---

### Post by tyteen4a03 on 2013-08-31
> **Jonathan Precise said:**
> Next time, post the result in code tags:
(CODE)Put your results here.(/CODE)

Replace the parenthesis with brackets to get:
```
Put your results here.
```

As for ppa-purge, try:

```
sudo apt-get install aptitude ppa-purge
```

That should fix the problem.
I didn't because it wasn't very long, but OK.

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 aptitude:i386 : Depends: aptitude-common:i386 (= 0.6.8.1-2ubuntu2) but it is not installable
                 Depends: libept1.4.12:i386 (>= 1.0.9) but it is not going to be installed
                 Depends: libxapian22:i386 but it is not going to be installed
                 Recommends: apt-xapian-index:i386 but it is not installable
                 Recommends: libparse-debianchangelog-perl:i386 but it is not installable
E: Unable to correct problems, you have held broken packages.
tyteen4a03@T4-PC:~$ sudo apt-get install aptitude-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package aptitude-common:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'aptitude-common:i386' has no installation candidate
tyteen4a03@T4-PC:~$  

```

---

### Post by Jonathan Precise on 2013-08-31
> **tyteen4a03 said:**
> I didn't because it wasn't very long, but OK.

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 aptitude:i386 : Depends: aptitude-common:i386 (= 0.6.8.1-2ubuntu2) but it is not installable
                 Depends: libept1.4.12:i386 (>= 1.0.9) but it is not going to be installed
                 Depends: libxapian22:i386 but it is not going to be installed
                 Recommends: apt-xapian-index:i386 but it is not installable
                 Recommends: libparse-debianchangelog-perl:i386 but it is not installable
E: Unable to correct problems, you have held broken packages.
tyteen4a03@T4-PC:~$ sudo apt-get install aptitude-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package aptitude-common:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'aptitude-common:i386' has no installation candidate
tyteen4a03@T4-PC:~$  

```

Oh my! This may be serious!!!

Try:
```
gksu gedit /etc/apt/sources.list
```

Change:

```
... mirror._**the-name-of-your-mirror**_.net/ubuntu raring ...
```

to:

```
... us.archive.ubuntu.com/ubuntu raring ...
```

I have had personal experiences that mirrors do not contain every package.:(

Then try:

```
sudo apt-get update; sudo apt-get install aptitude-common aptitude ppa-purge
```

That should fix the problem.

---

