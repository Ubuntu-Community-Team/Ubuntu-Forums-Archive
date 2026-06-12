---
title: "KDE Installation"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by jotnarta on 2008-06-16
Hi
I am trying to install KDE on my ubuntu installation. I used the following command: **sudo apt-get install kubuntu-desktop**, and I got the following errors:
zabin@zabin-laptop:~$ sudo apt-get install kubuntu-desktop
Password:
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
  kubuntu-desktop: Depends: adept but it is not going to be installed
                   Depends: amarok but it is not going to be installed
                   Depends: ark but it is not going to be installed
                   Depends: hwdb-client-kde but it is not going to be installed
                   Depends: k3b but it is not going to be installed
                   Depends: kaffeine-xine but it is not going to be installed
                   Depends: kamera but it is not going to be installed
                   Depends: kate but it is not going to be installed
                   Depends: kcontrol but it is not going to be installed
                   Depends: kcron but it is not going to be installed
                   Depends: kde-guidance but it is not going to be installed
                   Depends: kde-style-polyester but it is not going to be installed
                   Depends: kde-systemsettings but it is not going to be installed
                   Depends: kdeadmin-kfile-plugins but it is not going to be installed
                   Depends: kdebase-kio-plugins but it is not going to be installed
                   Depends: kdegraphics-kfile-plugins but it is not going to be installed
                   Depends: kdemultimedia-kfile-plugins but it is not going to be installed
                   Depends: kdemultimedia-kio-plugins but it is not going to be installed
                   Depends: kdenetwork-filesharing but it is not going to be installed
                   Depends: kdenetwork-kfile-plugins but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: kdeprint but it is not going to be installed
                   Depends: kdesktop but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: kdnssd but it is not going to be installed
                   Depends: keep but it is not going to be installed
                   Depends: kfind but it is not going to be installed
                   Depends: kghostview but it is not going to be installed
                   Depends: khelpcenter but it is not going to be installed
                   Depends: kicker but it is not going to be installed
                   Depends: kio-apt but it is not going to be installed
                   Depends: kio-locate but it is not going to be installed
                   Depends: klipper but it is not going to be installed
                   Depends: kmailcvt but it is not going to be installed
                   Depends: kmenuedit but it is not going to be installed
                   Depends: kmix but it is not going to be installed
                   Depends: kmplayer-konq-plugins but it is not going to be installed
                   Depends: knetworkconf but it is not going to be installed
                   Depends: konq-plugins but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: konversation but it is not going to be installed
                   Depends: kooka but it is not going to be installed
                   Depends: kopete but it is not going to be installed
                   Depends: kpdf but it is not going to be installed
                   Depends: kpf but it is not going to be installed
                   Depends: kppp but it is not going to be installed
                   Depends: krdc but it is not going to be installed
                   Depends: krfb but it is not going to be installed
                   Depends: ksmserver but it is not going to be installed
                   Depends: ksnapshot but it is not going to be installed
                   Depends: ksplash but it is not going to be installed
                   Depends: ksplash-engine-moodin but it is not going to be installed
                   Depends: ksvg but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
                   Depends: ksystemlog but it is not going to be installed
                   Depends: ktorrent but it is not going to be installed
                   Depends: kubuntu-default-settings but it is not going to be installed
                   Depends: kwin but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: software-properties-kde but it is not going to be installed
                   Recommends: akregator but it is not going to be installed
                   Recommends: apport-qt but it is not going to be installed
                   Recommends: digikam but it is not going to be installed
                   Recommends: gwenview but it is not going to be installed
                   Recommends: kaddressbook but it is not going to be installed
                   Recommends: karm but it is not going to be installed
                   Recommends: katapult but it is not going to be installed
                   Recommends: kbstate but it is not going to be installed
                   Recommends: kde-guidance-powermanager but it is not going to be installed
                   Recommends: kdebluetooth but it is not going to be installed
                   Recommends: kdepim-kio-plugins but it is not going to be installed
                   Recommends: kdepim-wizards but it is not going to be installed
                   Recommends: kexi but it is not going to be installed
                   Recommends: kipi-plugins but it is not going to be installed
                   Recommends: kmag but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: kmilo but it is not going to be installed
                   Recommends: kmousetool but it is not going to be installed
                   Recommends: knetworkmanager but it is not going to be installed
                   Recommends: knotes but it is not going to be installed
                   Recommends: konqueror but it is not going to be installed
                   Recommends: konqueror-nsplugins but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: korganizer but it is not going to be installed
                   Recommends: kscreensaver but it is not going to be installed
                   Recommends: kubuntu-docs but it is not going to be installed
                   Recommends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Recommends: kwalletmanager but it is not going to be installed
                   Recommends: networkstatus but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed
                   Recommends: skim but it is not going to be installed



Any Ideas to resolve this please?
Jotnarta

---

### Post by akiratheoni on 2008-06-16
Can you post the output of the following command:

```
cat /etc/apt/sources.list
```

---

### Post by iaculallad on 2008-06-16
Try:

```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

---

### Post by jotnarta on 2008-06-16
This is the output of sources.list file:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

---

### Post by jotnarta on 2008-06-16
Thank you Buddy, your command solved the problem, it a problem of updating , then installing kde :), Thanx..

Jotnarta

---

### Post by yo_pandabear on 2008-06-27
Thanks

---

### Post by Xiong Chiamiov on 2008-06-27
> **iaculallad said:**
> Try:

```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```
Of particular note is that aptitude is recommended in this case, rather than apt-get.  This way, if you uninstall using aptitude
```

sudo aptitude remove kubuntu-desktop

```
then it will remove all of the extra packages it installed with it, which apt-get will not do.

If you just want kde, and not all of the stuff that comes with kubuntu-desktop, you can install the kde-core package.

---

### Post by iaculallad on 2008-06-27
Added Info:

The command aptitude too has better dependency handling and has it's own console-GUI (executed via aptitude with no parameters).

---

