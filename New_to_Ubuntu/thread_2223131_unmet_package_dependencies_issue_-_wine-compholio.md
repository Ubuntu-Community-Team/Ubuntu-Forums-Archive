---
title: "unmet package dependencies issue - wine-compholio"
date: 2014-05-09
forum: New to Ubuntu
---

### Post by jdix123 on 2014-05-09
I'm trying to update my wine-compholio package, but for some reason it won't highlight in the update manager, it just sits there.

As far as I can tell, this is the relevant error

```
The following packages have unmet dependencies:
 wine-compholio : Depends: wine-compholio-i386 (= 1.7.18~ubuntu12.04.1)
E: Unable to correct problems, you have held broken packages.
```

So I try to see if I can figure out the issue via dpkg

```
jasond@Natalie:~$ dpkg -l wine-compholio
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                              Description
+++-====================================-====================================-========================================================================================
un  wine-compholio                       <none>                               (no description available)
```

Don't know quite enough about it to figure it out.

I tried 

[COLOR="#008080"]sudo apt-get purge wine-compholio*
sudo apt-get install wine-compholio[/COLOR]

No dice.

How do I find and remove broken packages?  I tried

[COLOR="#008080"]sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove[/COLOR]

---

### Post by deadflowr on 2014-05-09
Which ppa do you have?

Perhaps review this
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)
look at the warning in section 1.1.

You can find the ppa by running
```
ls /etc/apt/sources.list.d/
```
it should list the ppa name.

---

### Post by jdix123 on 2014-05-09
Attempted to remove the suggested PPA(s)

```
jasond@Natalie:~$ sudo add-apt-repository --remove ppa:ehoover/compholio
You are about to remove the following PPA from your system:
 
 More info: https://launchpad.net/~ehoover/+archive/compholio
Press [ENTER] to continue or ctrl-c to cancel removing it

Error: 'deb http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main' doesn't exist in a sourcelist file
Error: 'deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main' doesn't exist in a sourcelist file
```

and

```
jasond@Natalie:~$ sudo add-apt-repository --remove ppa:mqchael/pipelight
You are about to remove the following PPA from your system:
 Pipelight allows one to run Silverlight inside a Linux browser using Wine.
For more information take a look at http://fds-team.de/cms/articles/2013-08/pipelight-using-silverlight-in-linux-browsers.html

 More info: https://launchpad.net/~mqchael/+archive/pipelight
Press [ENTER] to continue or ctrl-c to cancel removing it

Error: 'deb http://ppa.launchpad.net/mqchael/pipelight/ubuntu precise main' doesn't exist in a sourcelist file
Error: 'deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu precise main' doesn't exist in a sourcelist file

```

So, repositories and PPAs seem to be messed up somewhere.

I pulled my /etc/apt/sources.list and its looking rather small

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################
###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
```

so clearly ubuntu is updating from a different list somewhere

---

### Post by deadflowr on 2014-05-09
Did you follow the part after the warning on how to add the new ppa and update and install the packages?

---

### Post by jdix123 on 2014-05-09
I'm fairly certain, if you are talking about this: 

[COLOR="#008080"]sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update[/COLOR]

and just to clarify, I've been using netflix/pipelight/compholio successfully for months, I'm just unable to find the broken package that is holding up the update process and purge it.  So its not that I'm trying to get this working from scratch, just do a little housekeeping and clean up the package dependencies.

---

### Post by deadflowr on 2014-05-09
Any errors? 
If so post them, please.

---

### Post by jdix123 on 2014-05-09
```
jasond@Natalie:/etc/apt/sources.list.d$ sudo apt-get install wine-compholio:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-compholio:i386 : Depends: wine-compholio-i386:i386 (= 1.7.18~ubuntu12.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by deadflowr on 2014-05-09
Maybe try
```
sudo apt-get upgrade
```
maybe if that does nothing
```
sudo apt-get dist-upgrade
```
then if needed 
```
sudo apt-get -f install
```
Run these as is, do not add a package name to the end of the commands.

---

### Post by jdix123 on 2014-05-09
I'm not really interested in a distribution upgrade.  

I'd like to know how to find out which package is broken, remove it, and then reinstall it if necesary.

---

### Post by deadflowr on 2014-05-09
> **jdix123 said:**
> I'm not really interested in a distribution upgrade.  

I'd like to know how to find out which package is broken, remove it, and then reinstall it if necesary.

None of those do a distribution upgrade.They don't mean what you think.

---

### Post by jdix123 on 2014-05-09
```
jasond@Natalie:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  wine-compholio:i386
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jasond@Natalie:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  wine-compholio:i386
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jasond@Natalie:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jasond@Natalie:~$ 
```

---

### Post by deadflowr on 2014-05-09
Does anything in here
[http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124)
or here
[http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies)

help?

---

### Post by Ubi_one_2014 on 2014-05-10
download the requred package from
[https://launchpad.net/~pipelight/+archive/stable/+build/5972135](https://launchpad.net/~pipelight/+archive/stable/+build/5972135)

install it by dpkg -i

---

### Post by jdix123 on 2014-05-10
Ok, so I went through those pages and tried a few things, but I still can't seem to isolate the problem.

I found that one package is being held, the [COLOR="#FF0000"]wine-compholio:i386[/COLOR] package, so I try to remove the package and install it manually:

```
jasond@Natalie:~$ sudo apt-get remove --dry-run wine-compholio:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pipelight-multi wine-compholio:i386
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Remv pipelight-multi [0.2.6~ubuntu12.04.1]
Remv wine-compholio:i386 [1.7.14~ubuntu12.04.1]
jasond@Natalie:~$ sudo apt-get install wine-compholio:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-compholio:i386 : Depends: wine-compholio-i386:i386 (= 1.7.18~ubuntu12.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
jasond@Natalie:~$ sudo apt-get install wine-compholio-i386:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-compholio-i386:i386 : Depends: liblcms2-2:i386 (>= 2.2+git20110628-2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

So I try to install the liblcms2-2:i386 package manually, but no dice.

```
jasond@Natalie:~$ sudo apt-get install liblcms2-2:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 icedtea-netx : Depends: openjdk-6-jre (>= 6b23~pre10~) but it is not going to be installed or
                         openjdk-7-jre but it is not going to be installed
 libatk-wrapper-java : Depends: default-jre but it is not going to be installed or
                                java2-runtime
 libatk-wrapper-java-jni : Depends: default-jre but it is not going to be installed or
                                    java2-runtime
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

So now it looks like a java issue?  I don't even see a java repository

```
jasond@Natalie:~$ cat /etc/apt/sources.list.d/*
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main #Banshee Team PPA disabled on upgrade to precise
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu oneiric main #Banshee Team PPA
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main #Banshee Team PPA disabled on upgrade to precise
deb http://ppa.launchpad.net/chromium-daily/stable/ubuntu precise main #Ubuntu Chromium - Stable Channel PPA disabled on upgrade to precise
deb http://ppa.launchpad.net/chromium-daily/stable/ubuntu oneiric main #Ubuntu Chromium - Stable Channel PPA
deb http://ppa.launchpad.net/chromium-daily/stable/ubuntu precise main #Ubuntu Chromium - Stable Channel PPA disabled on upgrade to precise
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
# deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main #Libreoffice PPA disabled on upgrade to precise
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu oneiric main #Libreoffice PPA
# deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main #Libreoffice PPA disabled on upgrade to precise
deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main #Openshot Official PPA disabled on upgrade to precise
deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu oneiric main #Openshot Official PPA
deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main #Openshot Official PPA disabled on upgrade to precise
deb http://ppa.launchpad.net/pipelight/stable/ubuntu precise main
deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu precise main
deb http://ppa.launchpad.net/pipelight/stable/ubuntu precise main
deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu precise main
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam64/ubuntu precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam64/ubuntu precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
# deb http://debian.scribus.net/debian/ testing main non-free #Scribus Repository
# deb http://debian.scribus.net/debian/ testing main non-free #Scribus Repository
# deb http://debian.scribus.net/debian/ testing main non-free #Scribus Repository
# deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu oneiric main #Adobe Flash (x86-64)
# deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu oneiric main #Adobe Flash (x86-64)
# deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu oneiric main #Adobe Flash (x86-64)
# deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
# deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
# deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
deb http://repo.steampowered.com/steam/ precise steam
deb-src http://repo.steampowered.com/steam/ precise steam
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu precise main #Ubuntu Tweak Stable PPA disabled on upgrade to precise
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu oneiric main #Ubuntu Tweak Stable PPA
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu precise main #Ubuntu Tweak Stable PPA disabled on upgrade to precise
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main #Ubuntu Wine Team PPA disabled on upgrade to precise
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main #Ubuntu Wine Team PPA
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main #Ubuntu Wine Team PPA disabled on upgrade to precise
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main #X Updates disabled on upgrade to precise
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu oneiric main #X Updates
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main #X Updates disabled on upgrade to precise
deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source disabled on upgrade to precise
deb http://download.virtualbox.org/virtualbox/debian oneiric contrib #VirtualBox Offical Source
deb http://download.virtualbox.org/virtualbox/debian precise contrib #VirtualBox Offical Source disabled on upgrade to precise
```

So am I right in thinking I need to add a java repository, and perhaps that will fix it?

---

### Post by Ubi_one_2014 on 2014-05-11
you need  wine-compholio-i386:i386 (= 1.7.18~ubuntu12.04.1)
that can be found at [https://launchpad.net/~pipelight/+archive/stable/+build/5972135](https://launchpad.net/~pipelight/+archive/stable/+build/5972135)

---

### Post by jdix123 on 2014-05-11
Which one of those do I download/run?  Or can I add that site as a ppa, and just apt-get install?

---

### Post by Ubi_one_2014 on 2014-05-11
the 4th package, wine-compholio

---

### Post by jdix123 on 2014-05-11
Hmm.  It won't install, but I can't see any error messages.  Using the Software Center as I'm not sure how to do this particular task from the command line.  It just says "Cannot install"

---

### Post by jdix123 on 2014-05-18
Any other ideas?

---

### Post by jdix123 on 2014-06-17
So I've continued working on this, without any improvement.

I noticed that I had both Java 6 and Java 7 installed, and thinking that might be the cause, of the issue, I purged Java 6.  I also purged the two packages that were not upgrading, pipelight-multi and wine-compholio:i386

But now I can not reinstall either of those packages.

```

jasond@Natalie:~$ sudo apt-get install wine-compholio:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-compholio:i386 : Depends: wine-compholio-i386:i386 (= 1.7.20~ubuntu12.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
jasond@Natalie:~$ sudo apt-get install wine-compholio-i386:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-compholio-i386:i386 : Depends: liblcms2-2:i386 (>= 2.2+git20110628-2) but it is not going to be installed
                            Recommends: libgsm1:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
jasond@Natalie:~$ 

```

and if I continue to trace the unmet dependencies the rabbit hole just keeps going.  Isn't apt supposed to trace and fix these automatically?

I don't know what is broken, and I can't figure out how to fix it without reinstalling my operating system and then reinstalling every package by hand--not something I care to do.

Is there a process to go through my sources.list and ppas to figure out which are still operating correctly?  And then update whichever ones are broken?

---

