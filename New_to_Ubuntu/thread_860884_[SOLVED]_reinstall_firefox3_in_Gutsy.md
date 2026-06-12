---
title: "[SOLVED] reinstall firefox3 in Gutsy"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-07-16
as my java doesn't work and firefox sometimes switches back to  2. 0 version when i click the launch icon, anyone would tell me how get a completely new installation of firefox 3.0 in ubuntu 7.10?

---

### Post by NikoC on 2008-07-16
Hmmmz I'm not on my ubuntu machine but how a about typing in a terminal:
sudo aptitude reinstall firefox

Hope this does the trick...

Cheers.

---

### Post by mempman on 2008-07-16
try this:
```

sudo apt-get remove --purge firefox-2.0 && sudo apt-get install --reinstall firefox-3.0 


```

---

### Post by iaculallad on 2008-07-16
> **afeasfaerw23231233 said:**
> as my java doesn't work and firefox sometimes switches back to  2. 0 version when i click the launch icon, anyone would tell me how get a completely new installation of firefox 3.0 in ubuntu 7.10?

Try:

```
sudo apt-get install firefox-3.0
```

---

### Post by framinglory on 2008-07-16
edit: someone posted faster than me, ignore this, sorry.

---

### Post by aysiu on 2008-07-16
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
ls /usr/bin/firefox -l
cat /etc/lsb-release
cat /etc/apt/sources.list
```

---

### Post by afeasfaerw23231233 on 2008-07-16
> **aysiu said:**
> Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
ls /usr/bin/firefox -l
cat /etc/lsb-release
cat /etc/apt/sources.list
```
```

wong@wong-desktop:~$ ls /usr/bin/firefox -l
lrwxrwxrwx 1 root root 22 2008-04-18 23:02 /usr/bin/firefox -> ../lib/firefox/firefox
wong@wong-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
wong@wong-desktop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
##newly added
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb [http://ppa.launchpad.net/daou/ubuntu](http://ppa.launchpad.net/daou/ubuntu) DISTRO main
deb-src [http://ppa.launchpad.net/daou/ubuntu](http://ppa.launchpad.net/daou/ubuntu) DISTRO main
wong@wong-desktop:~$
```

---

### Post by afeasfaerw23231233 on 2008-07-16
> **mempman said:**
> try this:
```

sudo apt-get remove --purge firefox-2.0 && sudo apt-get install --reinstall firefox-3.0 


```

i run your command and it said "Couldn't find package firefox-2.0
"
```
sudo apt-get remove --purge firefox-2.0 && sudo apt-get install --reinstall firefox-3.0 
[sudo] password for wong:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firefox-2.0

```

---

### Post by afeasfaerw23231233 on 2008-07-16
> **iaculallad said:**
> Try:

```
sudo apt-get install firefox-3.0
```

i run your command and restart my computer. but it still shows the firefox is version 2.0 by clicking "help -- about". i start the firefox by cliking the quick launch icon or "application - internet - firefox web browser ".

---

### Post by aysiu on 2008-07-16
You can't install Firefox 3 from the repositories in Gutsy (there's a version of Firefox 3 in the Universe repositories, but it's still alpha - Gran Paradiso).

You should follow [these instructions](http://www.psychocats.net/ubuntu/firefox#terminal).

---

### Post by oldsoundguy on 2008-07-16
or you could go to ubuntuzilla (source forge) and run their script.  It will remove the old, install FF3 and set it up so that the system updates automatically. (but you will be running the Mozilla version of FF and Ubuntu will no longer update nor will the packages be valid.)  
It works as I have done three Gutsy machines with the program.
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by afeasfaerw23231233 on 2008-07-16
> **aysiu said:**
> You can't install Firefox 3 from the repositories in Gutsy (there's a version of Firefox 3 in the Universe repositories, but it's still alpha - Gran Paradiso).

You should follow [these instructions](http://www.psychocats.net/ubuntu/firefox#terminal).

thanks for the link! i have installed ff3 successfully but java doen't work on in. would anyone tell me how to get java work in ff3?

---

### Post by gandaran on 2008-07-16
> **afeasfaerw23231233 said:**
> thanks for the link! i have installed ff3 successfully but java doen't work on in. would anyone tell me how to get java work in ff3?

just copy the sun-java firefox 2 plugin and paste to firefox 3 plugins folder!
look for a **libjavaplugin.so** file in your file system, then just copy this file to where firefox 3 is installed.

---

### Post by afeasfaerw23231233 on 2008-07-16
> **gandaran said:**
> just copy the sun-java firefox 2 plugin and paste to firefox 3 plugins folder!
look for a **libjavaplugin.so** file in your file system, then just copy this file to where firefox 3 is installed.

i type "locate libjavaplugin.so" in the terminal and nothing returns. where's that libjavaplugin.so?

---

### Post by tuxxy on 2008-07-16
I use GCJ, make sure you are using GCJ with this command in terminal,

```
sudo update-alternatives --config java
```

Next simply locate the GCJ java folder usually /usr/lib/ dir and find the plugin named libgcjwebplugin.so move this to your firefox plugins folder and you should be away :)

---

### Post by gandaran on 2008-07-17
> **afeasfaerw23231233 said:**
> i type "locate libjavaplugin.so" in the terminal and nothing returns. where's that libjavaplugin.so?

you will find this libjavaplugin.so file if you have the **sun-java6-plugin** package installed, check in synaptic for that, if it's already installed try reinstalling it again, as you just installed a new firefox package reinstalling java plugin could fix your problem. I recommend you use sun-java and not open java, if you have both installed remove one of them.
this is for 32-bits systems, if you running ubuntu 64-bits , you'll have to stick with open java.
I'm not using ubuntu 7.10, so I don't know exactly where the plugin is installed, but check /usr/lib/firefox/plugins or /usr/lib/mozilla/plugins
it should be somewhere in a /usr/lib folder
do you still have firefox 2 installed?

edit
if you installed firefox using these instructions [http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal) then you'll also find  there instructions on how to make the links to the firefox 2 plugins.

---

### Post by afeasfaerw23231233 on 2008-07-17
> **tuxxy said:**
> I use GCJ, make sure you are using GCJ with this command in terminal,

```
sudo update-alternatives --config java
```

Next simply locate the GCJ java folder usually /usr/lib/ dir and find the plugin named libgcjwebplugin.so move this to your firefox plugins folder and you should be away :)
what is GCJ? i run your command and 
```
sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/bin/gij-4.2). Nothing to configure.

```
what to do now? thanks!

---

### Post by gandaran on 2008-07-17
what is GCJ?

GCJ is open java, you have to make up you mind which one you want to use.

sudo update-alternatives --config java
 
this command is only useful if you have both open-java and sun-java installed, it just sets-up which java firefox will use.

as you can see none of this will fix your problem, it's best you follow the same instructions you used to install mozillas-firefox (if that is what you really installed?) or make up you mind, choose only one java install and try to copy the plugin to the new firefox, it's easy!
I could give you a command to run to make a link to java, but I need to know exactly where the plugin is in your system and where is this new firefox installed, only you can give these details.

edit
I also believe you haven't installed java, because when you run the command **sudo update-alternatives --config java** it just list one package that is neither open-java or sun-java. (its just the default java installed for open office)
If I can remenber right, there is no open-java package for ubuntu 7.10, the open-java only came out in ubuntu 8.04!
so just install the sun-java6 or sun-java5-plugin, open synaptic find it and install! or look for the sun-java6 web-start package in add/remove programs, check for install and click the apply button.

---

### Post by afeasfaerw23231233 on 2008-07-17
> **gandaran said:**
> you will find this libjavaplugin.so file if you have the **sun-java6-plugin** package installed, check in synaptic for that, if it's already installed try reinstalling it again, as you just installed a new firefox package reinstalling java plugin could fix your problem. I recommend you use sun-java and not open java, if you have both installed remove one of them.
this is for 32-bits systems, if you running ubuntu 64-bits , you'll have to stick with open java.
I'm not using ubuntu 7.10, so I don't know exactly where the plugin is installed, but check /usr/lib/firefox/plugins or /usr/lib/mozilla/plugins
it should be somewhere in a /usr/lib folder
do you still have firefox 2 installed?

edit
if you installed firefox using these instructions [http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal) then you'll also find  there instructions on how to make the links to the firefox 2 plugins.
firefox 2 seems disappear now. i only want ff3.
my old box is 32-bit. i just install java 6 from synaptic and it works fine in firefox3. thanks all of you for help!
problem solved

---

### Post by sadicote on 2009-04-18
Sorry to rake this up, but i have java enabled in firefox preferences, there is a libjavaplugin.so in my usr/lib/firefox/plug-ins folder, and yet i cannot create a web page on the geocities site. When i try to use the yahoo pagemaker, i get an error message like "You do not have java enabled on the browser".

---

