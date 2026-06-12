---
title: "Error Message: Requires installation of untrusted packages...."
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Randallflagg on 2012-06-11
Hi Ubuntu comunity
Am unable to update my software packages with the update manager. I receive the following error message: "Requires installation of untrusted packages. The action would require the installation of packages from unauthenticated sources."

My system info is: Ubuntu 11.10 OS type 32 bit

Following advice I read on related threads  I ran  the command: 

gksudo gedit /etc/apt/sources.list

As per thread advice I deleted some of the comments in the sources list 
(e.g. "## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team.")


  and saved the below version. When I ran the update manager again I got the same above error message. 

Here is my current sources list:
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ .Trash-1000/files/dists/jaunty/restricted/binary-i386/
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ .Trash-1000/files/dists/jaunty/main/binary-i386/
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates restricted main multiverse universe #Added by software-properties

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates universe

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'backports'
## repository.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-backports restricted main multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-backports restricted main multiverse universe #Added by software-properties
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-proposed restricted main multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-proposed restricted main multiverse universe #Added by software-properties

Any advice would be appreciated

---

### Post by wilee-nilee on 2012-06-11
You have jaunty natty and oneric in the sources.list, make sure they are all the release your running to begin with.

All the cd references need a # to comment them out at the top of the list. You probably have doubled repos start with commenting out the not up to date highlighted with a #

[COLOR=Red]You might look here for a proper basic source list.[/COLOR]
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

[B]
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ .Trash-1000/files/dists/jaunty/restricted/binary-i386/
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ .Trash-1000/files/dists/jaunty/main/binary-i386/[/B]
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates restricted main multiverse universe #Added by software-properties

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates universe

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
[B]deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse[/B]

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
[B]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner[/B]

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'backports'
## repository.
[B]deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse[/B]


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
[B]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner[/B]

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-backports restricted main multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-backports restricted main multiverse universe #Added by software-properties
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-proposed restricted main multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-proposed restricted main multiverse universe #Added by software-properties

---

### Post by Randallflagg on 2012-06-11
Hi wilee-nilee

Thank you for your reply. I commented out the lines with Natty and Jaunty (my system is Oneric) by adding '#' in front of those lines. When I ran the update manager I got the same error message. I generated a new source list (I checked off everything that was available) from the site you suggested [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) . The update manager has done only a partial update because there was an error authenticating some packages. This could be due to software I have not installed yet?

The packages that had an error authenticating are:
compiz-plugins-main
compiz-plugins-main-default
language-pack-en
language-pack-en-base
language-pack-gnome-en
language-pack-gnome-en-base
libboo2.0.9-cil
libcommon-sense-perl
libjson-perl
libjson-xs-perl
libkarma0
libmono-compilerservices-symbolwriter4.0-cil
libnautilus-extension1
libpath-class-perl
libtagc0
mousetweaks
nautilus
nautilus-data

END

---

### Post by wilee-nilee on 2012-06-11
Partial updates are common, and generally you don't run them.

A partial means all the pkgs are not in the repos yet best to wait till they are to run the upgrade.

But post the output from running this in the terminal.
```
sudo apt-get update
```Generally there are missing keys mentioned with a authentication problem that can be loaded with this command.
                                  ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys "missing key here"
```When ever you change the sources.list you have to run a update command to sync it as well, sounds like you did just mentioning it. You might just need to change the mirror as well, in software sources.

---

### Post by Randallflagg on 2012-06-11
Hi wilee-nilee

Thank you again for your time and effort

Re: sudo apt-get update
I ran the sudo apt-get update and got too many lines to copy here.  
I received many 'HIT' lines that seemed OK, e.g. "Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release " 

and many 'IGN' that seemed OK too, e.g. "Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex"

I also rcvd about 20 lines starting with Err, e.g. "Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/main Sources Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)"


About 75 lines starting with 'W' One is 'W: Failed to Fetch', e.g. "W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)"

The other is 'W: GPG error', e.g. " W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA"

One line started with E, e.g. "E: Some index files failed to download. They have been ignored, or old ones used instead."

I ran the other command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys "missing key here" and the terminal print out is below.

randy@randy-System-Product-Name:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys "missing key here"
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.gL9aFgVEBJ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys missing key here
gpg: "missing" not a key ID: skipping
gpg: "key" not a key ID: skipping
gpg: "here" not a key ID: skipping
randy@randy-System-Product-Name:~$

P.s. From the list 'packages that had an error authenticating' on our previous thread, I doublechecked my software installed and found 'mousetweaks' and 'compiz' were indeed already installed.

I reran the update manager and received the same error message, i.e. "Requires installation of untrusted packages. The action would require  the installation of packages from unauthenticated sources."

---

### Post by Randallflagg on 2012-06-11
Adding to my last message I noticed I didn't reply to the rest of your points.

You said: When ever you change the sources.list you have to run a update command  to sync it as well, sounds like you did just mentioning it. REPLY: What do you mean by sync it as well? I did save the changes in the sources list. Is there something else I have to do?

Your said: You might  just need to change the mirror as well, in software sources.     REPLY: I'm not sure how to do that.

---

### Post by wilee-nilee on 2012-06-11
First of all when I asked for evrey line that means everyline your explanation does not make this easier.

Second for an example of a missing key, from your explanation run the command for every one you see a example of yours below

The other is 'W: GPG error', e.g. " W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net)  oneiric Release: The following signatures couldn't be verified because  the public key is not available: [COLOR=Red]NO_PUBKEY[/COLOR] **464AD83D4631BBEA**"

Run this command.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 464AD83D4631BBEA
```

Sync means that you have changed the list, in order to synchronize your computer and what ever mirror you calling to get packages a update is needed, it is a two way hanshake of what yiou have installed and what is available for updating.

Changing the mirror in software center is opening the ubuntu software center hitting edit-sopftwrae sources and on the firsy tab is download from, and opening that and choosing a mirror close by or letting the computer find the fastest ping with, other-select best server.

---

### Post by Randallflagg on 2012-06-12
Hi wilee-nilee

Ooops, I misread your writing and did not understand you meant for me to paste every line. I've posted the  results in full below. Thank you for taking the time to scroll through it.

First I changed the mirror to the best server in my area. I save it and leave it open. When I change my mirror to the best server. I'm not sure if it is synced properly with my source list.  I close both the source list and the software sources. When I reopen my software sources the mirror has reverted back to 'Server Canada'. When I choose the best server again the sources list reverts back to the previous outdated sources list. Then when I run a new sudo apt-get updaate I get a different print-out showing all the old NATTY references.

       Second I ran the command sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys for every missing key example. Only one of the key commands was processed. The rest of the keys were not processed according to the report.

  Here is the terminal print-out. The top part shows the commands for receiving the missing keys and then follows with the sudo apt-get update. I also posted my Source List below it.


[LIST]
[*]Missing key and sudo update print-out starts here
[/LIST]
 randy@randy-System-Product-Name:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com –recv-keys 74A941BA219EC810
[sudo] password for randy: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.nlVkmgNKTf --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com –recv-keys 74A941BA219EC810
usage: gpg [options] [filename]
randy@randy-System-Product-Name:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 464AD83D4631BBEA
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.PClVPEBlY6 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 464AD83D4631BBEA
gpg: requesting key 4631BBEA from hkp server keyserver.ubuntu.com
gpg: key 4631BBEA: "Launchpad equinoxart" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
randy@randy-System-Product-Name:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com –recv-keys 483881FD2506E8CC
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.P06GNXdn9d --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com –recv-keys 483881FD2506E8CC
usage: gpg [options] [filename]
randy@randy-System-Product-Name:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com –recv-keys B5FC5445BA702101
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.VoToEfGGWO --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com –recv-keys B5FC5445BA702101
usage: gpg [options] [filename]
randy@randy-System-Product-Name:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com –recv-keys 5EC48884BB901940
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.WUBQ2ObMvS --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com –recv-keys 5EC48884BB901940
usage: gpg [options] [filename]
randy@randy-System-Product-Name:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com –recv-keys B302120208A255AF
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.9YwTntrQhZ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com –recv-keys B302120208A255AF
usage: gpg [options] [filename]
randy@randy-System-Product-Name:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com –recv-keys 2EBC26B60C5A2783
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.jIaU9xZzEH --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com –recv-keys 2EBC26B60C5A2783
usage: gpg [options] [filename]

```
[LIST]
[*] randy@randy-System-Product-Name:~$ sudo apt-get update
[/LIST]
 randy@randy-System-Product-Name:~$ sudo apt-get update
[sudo] password for randy: 
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist InRelease
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric InRelease                                 
Hit [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist Release.gpg                       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric InRelease                             
Hit [http://download.virtualbox.org](http://download.virtualbox.org) oneiric InRelease                           
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://www.fbreader.org](http://www.fbreader.org) stable InRelease                                   
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://dl.google.com](http://dl.google.com) testing InRelease                                     
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease [7,096 B]                
Hit [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist Release                           
Ign [http://deb.opera.com](http://deb.opera.com) lenny InRelease                                       
Ign [http://deb.opera.com](http://deb.opera.com) lenny InRelease                                       
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric InRelease                               
Ign [http://update.yuuguu.com](http://update.yuuguu.com) hardy InRelease                                   
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release.gpg                               
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security InRelease                    
Ign [http://repo.palatinus.cz](http://repo.palatinus.cz)  InRelease                                        
Ign [http://www.bunkus.org](http://www.bunkus.org) ./ InRelease                                         
Ign [http://download.webmin.com](http://download.webmin.com) sarge InRelease                                 
Get:2 [http://update.yuuguu.com](http://update.yuuguu.com) hardy Release.gpg [197 B]                       
Get:3 [http://www.fbreader.org](http://www.fbreader.org) stable Release.gpg [189 B]                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease                            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable InRelease                                
Get:4 [http://deb.torproject.org](http://deb.torproject.org) oneiric InRelease [3,483 B]                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release                                   
Get:5 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189 B]                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates InRelease                     
Hit [http://download.virtualbox.org](http://download.virtualbox.org) oneiric/contrib i386 Packages               
Hit [http://update.yuuguu.com](http://update.yuuguu.com) hardy Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release.gpg                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://deb.torproject.org](http://deb.torproject.org) oneiric InRelease                                
Hit [http://repo.palatinus.cz](http://repo.palatinus.cz)  Release.gpg                                      
Get:6 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189 B]                         
Hit [http://www.fbreader.org](http://www.fbreader.org) stable Release                                     
Ign [http://update.yuuguu.com](http://update.yuuguu.com) hardy Release                                     
Hit [http://www.bunkus.org](http://www.bunkus.org) ./ Release.gpg                                       
Ign [http://www.fbreader.org](http://www.fbreader.org) stable Release                                     
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable InRelease                                  
Hit [http://apt.mucommander.com](http://apt.mucommander.com) stable Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen i386 Packages               
Ign [http://download.virtualbox.org](http://download.virtualbox.org) oneiric/contrib TranslationIndex            
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb InRelease                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://download.webmin.com](http://download.webmin.com) sarge Release.gpg                               
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed InRelease                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main i386 Packages                        
Ign [http://update.yuuguu.com](http://update.yuuguu.com) hardy/multiverse i386 Packages/DiffIndex          
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main i386 Packages                      
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release.gpg                                     
Hit [http://repo.palatinus.cz](http://repo.palatinus.cz)  Release                                          
Ign [http://deb.torproject.org](http://deb.torproject.org) oneiric/main Sources/DiffIndex                   
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen TranslationIndex            
Hit [http://www.bunkus.org](http://www.bunkus.org) ./ Release                                           
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main Sources/DiffIndex                      
Hit [http://deb.paissad.net](http://deb.paissad.net) unstable Release.gpg                                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Sources/DiffIndex               
Hit [http://apt.mucommander.com](http://apt.mucommander.com) stable Release                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable InRelease                      
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing InRelease                     
Ign [http://update.yuuguu.com](http://update.yuuguu.com) hardy/multiverse TranslationIndex                 
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release                                         
Hit [http://repo.palatinus.cz](http://repo.palatinus.cz)  Packages                                         
Ign [http://deb.torproject.org](http://deb.torproject.org) oneiric/main i386 Packages/DiffIndex             
Ign [http://deb.torproject.org](http://deb.torproject.org) oneiric/main TranslationIndex                    
Hit [http://deb.paissad.net](http://deb.paissad.net) unstable Release                                    
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main TranslationIndex                   
Hit [http://www.bunkus.org](http://www.bunkus.org) ./ Sources                                           
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main i386 Packages/DiffIndex                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://download.webmin.com](http://download.webmin.com) sarge Release                                   
Get:7 [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable Release.gpg [191 B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://apt.mucommander.com](http://apt.mucommander.com) stable/main i386 Packages                       
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main TranslationIndex                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release                                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Sources/DiffIndex           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://deb.paissad.net](http://deb.paissad.net) unstable/main Sources                               
Hit [http://www.bunkus.org](http://www.bunkus.org) ./ Packages                                          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports InRelease                   
Get:8 [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing Release.gpg [191 B]         
Hit [http://apt.mucommander.com](http://apt.mucommander.com) stable/non-free i386 Packages                   
Hit [http://apt.mucommander.com](http://apt.mucommander.com) stable/contrib i386 Packages                    
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/contrib TranslationIndex                 
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/main TranslationIndex                    
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/non-free TranslationIndex                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://deb.opera.com](http://deb.opera.com) lenny/non-free i386 Packages                          
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free TranslationIndex                       
Hit [http://deb.paissad.net](http://deb.paissad.net) unstable/contrib Sources                            
Hit [http://deb.paissad.net](http://deb.paissad.net) unstable/non-free Sources                           
Hit [http://deb.paissad.net](http://deb.paissad.net) unstable/personal Sources                           
Hit [http://deb.paissad.net](http://deb.paissad.net) unstable/main i386 Packages                         
Hit [http://deb.paissad.net](http://deb.paissad.net) unstable/contrib i386 Packages                      
Hit [http://download.webmin.com](http://download.webmin.com) sarge/contrib i386 Packages                     
Hit [http://deb.paissad.net](http://deb.paissad.net) unstable/non-free i386 Packages                     
Hit [http://deb.paissad.net](http://deb.paissad.net) unstable/personal i386 Packages                     
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/contrib TranslationIndex                   
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/main TranslationIndex                      
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/non-free TranslationIndex                  
Hit [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable Release                        
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric Release.gpg                           
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://deb.opera.com](http://deb.opera.com) lenny/non-free i386 Packages                          
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free TranslationIndex                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages/DiffIndex         
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/personal TranslationIndex                  
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release.gpg                       
Hit [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing Release                       
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing Release                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib TranslationIndex                  
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security Release.gpg                  
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable/universe i386 Packages/DiffIndex
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable/universe TranslationIndex      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages/DiffIndex     
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates Release.gpg                   
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen Translation-en_CA           
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing/universe i386 Packages/DiffIndex
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing/universe TranslationIndex     
Hit [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable/universe i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                    
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen Translation-en              
Hit [http://update.yuuguu.com](http://update.yuuguu.com) hardy/multiverse i386 Packages                    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en_CA                    
Ign [http://download.virtualbox.org](http://download.virtualbox.org) oneiric/contrib Translation-en_CA           
Hit [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing/universe i386 Packages        
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed Release.gpg                  
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en                       
Ign [http://download.virtualbox.org](http://download.virtualbox.org) oneiric/contrib Translation-en              
Ign [http://repo.palatinus.cz](http://repo.palatinus.cz)  Translation-en_CA                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://deb.torproject.org](http://deb.torproject.org) oneiric/main Sources                             
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports Release.gpg                 
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://update.yuuguu.com](http://update.yuuguu.com) hardy/multiverse Translation-en_CA                
Ign [http://repo.palatinus.cz](http://repo.palatinus.cz)  Translation-en                                   
Ign [http://www.bunkus.org](http://www.bunkus.org) ./ Translation-en_CA                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex            
Hit [http://deb.torproject.org](http://deb.torproject.org) oneiric/main i386 Packages                       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric Release                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_CA                    
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main Translation-en_CA                  
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_CA             
Ign [http://www.bunkus.org](http://www.bunkus.org) ./ Translation-en                                    
Ign [http://update.yuuguu.com](http://update.yuuguu.com) hardy/multiverse Translation-en                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release                           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security Release                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Hit [http://www.fbreader.org](http://www.fbreader.org) stable/main Sources                                
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/contrib Translation-en_CA                
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/contrib Translation-en                   
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main Translation-en                     
Hit [http://www.fbreader.org](http://www.fbreader.org) stable/main i386 Packages                          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Sources                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://deb.torproject.org](http://deb.torproject.org) oneiric/main Translation-en_CA                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates Release                       
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/main Translation-en_CA                   
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/main Translation-en                      
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/non-free Translation-en_CA               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://deb.torproject.org](http://deb.torproject.org) oneiric/main Translation-en                      
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-en_CA                      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed Release                      
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/non-free Translation-en                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Sources                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports Release                     
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/contrib Translation-en_CA                  
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/contrib Translation-en                     
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-en                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main Sources/DiffIndex                
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/main Translation-en_CA                     
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/main Translation-en                        
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/non-free Translation-en_CA                 
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/non-free Translation-en                    
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/personal Translation-en_CA                 
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-en_CA                      
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-en                         
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted Sources/DiffIndex          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages                   
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/personal Translation-en                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe Sources/DiffIndex            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse Sources/DiffIndex          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main Translation-en_CA                      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex    
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable/universe Translation-en_CA     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages               
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main TranslationIndex                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources/DiffIndex                    
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main Translation-en                         
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games i386 Packages               
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps TranslationIndex             
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games TranslationIndex            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages/DiffIndex              
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable/universe Translation-en        
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing/universe Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe TranslationIndex             
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib Translation-en_CA                 
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing/universe Translation-en       
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib Translation-en                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Get:11 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Get:12 [http://dl.google.com](http://dl.google.com) stable Release [2,544 B]                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Get:13 [http://dl.google.com](http://dl.google.com) testing Release [2,513 B]                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps Translation-en_CA            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps Translation-en               
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games Translation-en_CA           
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games Translation-en              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/main TranslationIndex        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/multiverse TranslationIndex  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/restricted TranslationIndex  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/universe TranslationIndex    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main Sources/DiffIndex        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted Sources/DiffIndex  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe Sources/DiffIndex    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse Sources/DiffIndex  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main i386 Packages/DiffIndex  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages/DiffIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/main TranslationIndex        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/multiverse TranslationIndex  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/restricted TranslationIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/universe TranslationIndex    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en_CA           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en_CA           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Get:14 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                           
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/main Sources       
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/restricted Sources 
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/universe Sources
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/multiverse Sources
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/main i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/restricted i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/universe i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/multiverse i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/main Sources       
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/restricted Sources 
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/universe Sources
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/multiverse Sources
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/main i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/restricted i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/universe i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/multiverse i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main Sources
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted Sources
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe Sources
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse Sources
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main Sources
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted Sources
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe Sources
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse Sources
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse i386 Packages
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main Translation-en_CA                
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main Translation-en                   
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse Translation-en_CA          
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse Translation-en             
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted Translation-en_CA          
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted Translation-en             
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe Translation-en_CA            
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe Translation-en               
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/main Translation-en_CA       
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/main Translation-en          
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/multiverse Translation-en_CA 
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/multiverse Translation-en    
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/restricted Translation-en_CA 
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/restricted Translation-en    
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/universe Translation-en_CA   
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-security/universe Translation-en      
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main Sources                  
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted Sources            
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe Sources              
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse Sources            
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main i386 Packages            
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main Translation-en_CA        
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main Translation-en           
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse Translation-en_CA  
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted Translation-en_CA  
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe Translation-en_CA    
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe Translation-en       
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/main Translation-en_CA       
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/main Translation-en          
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/multiverse Translation-en_CA 
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/multiverse Translation-en    
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/restricted Translation-en_CA 
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/restricted Translation-en    
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/universe Translation-en_CA   
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-proposed/universe Translation-en      
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main Translation-en_CA      
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main Translation-en         
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse Translation-en_CA
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse Translation-en   
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted Translation-en_CA
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe Translation-en_CA  
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe Translation-en     
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Get:15 [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages [1,010 B]            
Ign [http://dl.google.com](http://dl.google.com) stable/non-free TranslationIndex                      
Get:16 [http://dl.google.com](http://dl.google.com) testing/non-free i386 Packages [793 B]
Ign [http://dl.google.com](http://dl.google.com) testing/non-free TranslationIndex
Get:17 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [769 B]
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_CA                     
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en                        
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_CA                    
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Fetched 21.5 kB in 51s (419 B/s)                                               
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://deb.torproject.org](http://deb.torproject.org) oneiric InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810
W: GPG error: [http://update.yuuguu.com](http://update.yuuguu.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 483881FD2506E8CC
W: GPG error: [http://www.fbreader.org](http://www.fbreader.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B5FC5445BA702101
W: GPG error: [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 670C48C26A11800F
W: GPG error: [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 670C48C26A11800F
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5EC48884BB901940
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B302120208A255AF
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/Release.gpg)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en_CA](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en_CA)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en](http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
randy@randy-System-Product-Name:~$ 



[LIST]
[*] Sudo apt-get update ends here.
[/LIST]
 

[LIST]
[*] Source list starts here:
[/LIST]
 
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric main restricted universe multiverse 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-security main restricted universe multiverse 
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted universe multiverse 
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-proposed main restricted universe multiverse 
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-security main restricted universe multiverse 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted universe multiverse 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-proposed main restricted universe multiverse 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Audacity - [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys     1024R/BB901940
deb [http://ppa.launchpad.net/audacity-team/daily/ubuntu](http://ppa.launchpad.net/audacity-team/daily/ubuntu) oneiric main 

#### AWN (Avant Window Navigator) Testing Packages - [http://awn-project.org/](http://awn-project.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) oneiric main

#### Banshee - [https://edge.launchpad.net/~banshee-team]("https://edge.launchpad.net/%7Ebanshee-team")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) oneiric main

#### Chromium Project - [http://code.google.com/chromium/](http://code.google.com/chromium/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) oneiric main

#### Cortina - [https://launchpad.net/~cs-sniffer/+archive/cortina]("https://launchpad.net/%7Ecs-sniffer/+archive/cortina")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CA186228
deb [http://ppa.launchpad.net/cs-sniffer/cortina/ubuntu](http://ppa.launchpad.net/cs-sniffer/cortina/ubuntu) oneiric main

#### DeaDBeeF - [http://deadbeef.sourceforge.net/](http://deadbeef.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
deb [http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu](http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu) oneiric main

#### Equinox - [https://launchpad.net/~tiheum/+archive/equinox]("https://launchpad.net/%7Etiheum/+archive/equinox")
## Run this command: sudo apt-get update && sudo apt-get install faenza-icon-theme && sudo apt-get install equinox-theme    
deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) oneiric main

#### Esmska - [http://code.google.com/p/esmska/](http://code.google.com/p/esmska/) 
## Run this command: wget -q -O - [http://repo.palatinus.cz/repo.key](http://repo.palatinus.cz/repo.key) | sudo apt-key add -
deb [http://repo.palatinus.cz/stable](http://repo.palatinus.cz/stable) / 

#### FBReader - [http://www.fbreader.org/desktop/](http://www.fbreader.org/desktop/)
## Run this command: [http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc](http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc) -O- | sudo apt-key add -
deb [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) stable main 

#### Flacon - [http://kde-apps.org/content/show.php?content=113388](http://kde-apps.org/content/show.php?content=113388)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
deb [http://ppa.launchpad.net/flacon/ppa/ubuntu](http://ppa.launchpad.net/flacon/ppa/ubuntu) oneiric main

#### GetDeb - [http://www.getdeb.net](http://www.getdeb.net)
## Run this command: wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps

#### Gimp SVN - [https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn]("https://launchpad.net/%7Ematthaeus123/+archive/mrw-gimp-svn")
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 405A15CB
deb [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) oneiric main 

#### Glx-Dock / Cairo-Dock - [http://www.glx-dock.org](http://www.glx-dock.org)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu) oneiric main

#### GNUzilla and IceCat - [http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 
deb [http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu](http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu) oneiric main  

#### Google Linux Software Repositories - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

#### Google Linux Software Repositories (Testing) - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add  -
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free

#### Gwibber (Daily) - [https://launchpad.net/gwibber](https://launchpad.net/gwibber)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) oneiric main

#### HandBrake Snapshots - [http://handbrake.fr/](http://handbrake.fr/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu) oneiric main

#### Ironhide - [https://launchpad.net/~mj-casalogic/+archive/ironhide/]("https://launchpad.net/%7Emj-casalogic/+archive/ironhide/")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ECF7E0B3
deb [http://ppa.launchpad.net/mj-casalogic/ironhide/ubuntu](http://ppa.launchpad.net/mj-casalogic/ironhide/ubuntu) oneiric main

#### Kubuntu Backports - [https://edge.launchpad.net/~kubuntu-ppa/+archive/backports]("https://edge.launchpad.net/%7Ekubuntu-ppa/+archive/backports")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) oneiric main

#### Kubuntu Beta Backports - [https://launchpad.net/~kubuntu-ppa/+archive/beta]("https://launchpad.net/%7Ekubuntu-ppa/+archive/beta")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) oneiric main

#### Kubuntu Experimental - [https://launchpad.net/~kubuntu-ppa/+archive/experimental]("https://launchpad.net/%7Ekubuntu-ppa/+archive/experimental")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 493B3065
deb [http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu) oneiric main

#### Kubuntu Updates - [https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa]("https://edge.launchpad.net/%7Ekubuntu-ppa/+archive/ppa")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) oneiric main 

#### Lazarus - [http://www.lazarus.freepascal.org/](http://www.lazarus.freepascal.org/)
## Run this command:  gpg --keyserver hkp://pgp.mit.edu:11371 --recv-keys 6A11800F  && gpg --export --armor 0F7992B0  | sudo apt-key add -
deb [http://www.hu.freepascal.org/lazarus/](http://www.hu.freepascal.org/lazarus/) lazarus-stable universe

#### Lazarus (Testing) - [http://www.lazarus.freepascal.org/](http://www.lazarus.freepascal.org/)
## Run this command:  gpg --keyserver hkp://pgp.mit.edu:11371 --recv-keys 6A11800F  && gpg --export --armor 0F7992B0  | sudo apt-key add -
 deb [http://www.hu.freepascal.org/lazarus/](http://www.hu.freepascal.org/lazarus/) lazarus-testing universe

#### LibreOffice - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) oneiric main

#### Medibuntu - [http://www.medibuntu.org/](http://www.medibuntu.org/) 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free

#### Midori - [https://launchpad.net/~midori/+archive/ppa]("https://launchpad.net/%7Emidori/+archive/ppa")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) oneiric main

#### Miro HD Video Player - [http://www.getmiro.com/](http://www.getmiro.com/)
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D75E850
deb [http://ppa.launchpad.net/pcf/miro-releases/ubuntu](http://ppa.launchpad.net/pcf/miro-releases/ubuntu) oneiric main

#### MKVToolnix - [http://www.bunkus.org/videotools/mkvtoolnix/](http://www.bunkus.org/videotools/mkvtoolnix/)
## Run this command: wget -q [http://www.bunkus.org/gpg-pub-moritzbunkus.txt](http://www.bunkus.org/gpg-pub-moritzbunkus.txt) -O- | sudo apt-key add -
deb [http://www.bunkus.org/ubuntu/oneiric/](http://www.bunkus.org/ubuntu/oneiric/) ./

#### MongoDB - [http://www.mongodb.org/](http://www.mongodb.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
deb [http://downloads-distro.mongodb.org/repo/ubuntu-upstart](http://downloads-distro.mongodb.org/repo/ubuntu-upstart) dist 10gen

#### Mozilla Daily Build Team - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("http://edge.launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) oneiric main

#### muCommander - [http://www.mucommander.com/](http://www.mucommander.com/)
## Run this command: sudo wget -O - [http://apt.mucommander.com/apt.key](http://apt.mucommander.com/apt.key) | sudo apt-key add - 
deb [http://apt.mucommander.com](http://apt.mucommander.com) stable main non-free contrib  

#### OpenShot - [http://www.openshotvideo.com](http://www.openshotvideo.com)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA
deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) oneiric main

#### Opera - [http://www.opera.com/](http://www.opera.com/)
## Run this command: sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free

#### Opera Beta - [http://www.opera.com/](http://www.opera.com/)
## Run this command: sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -
deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) lenny non-free

#### Paissad's PS3 Media Server Repo - [http://deb.paissad.net](http://deb.paissad.net)
## Run this command: wget -q -O - [http://deb.paissad.net/public-key.asc](http://deb.paissad.net/public-key.asc) | sudo apt-key add -
deb [http://deb.paissad.net](http://deb.paissad.net) unstable main contrib non-free personal

#### Pidgin - [http://pidgin.im](http://pidgin.im)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) oneiric main

#### PlayDeb Beta 2 - [http://www.playdeb.net/](http://www.playdeb.net/)
## Run this command: wget -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games

#### PlayOnLinux - [http://www.playonlinux.com/en](http://www.playonlinux.com/en)
## Run this command: wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) oneiric main

#### qBittorrent - [http://qbittorrent.sourceforge.net/](http://qbittorrent.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 47B4D1C4
deb [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu) oneiric main

#### SABnzbd - [http://sabnzbd.org/](http://sabnzbd.org/)
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4BB9F05F
deb [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) oneiric main

#### Tor: anonymity online - [http://www.torproject.org/](http://www.torproject.org/)
## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 94C09C7F  | sudo apt-key add -
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) oneiric main

#### Ubuntu Tweak - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) oneiric main

#### UbuntuGIS (unstable) - [http://trac.osgeo.org/ubuntugis/wiki](http://trac.osgeo.org/ubuntugis/wiki)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 314DF160
deb [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu) oneiric main

#### UNetbootin - [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) oneiric main

#### VirtualBox - [http://www.virtualbox.org](http://www.virtualbox.org)
## Run this command: wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric contrib

#### WebKit Team PPA - [https://launchpad.net/~webkit-team/+archive/ppa]("https://launchpad.net/%7Ewebkit-team/+archive/ppa")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B
deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) oneiric main

#### Webmin - [http://www.webmin.com](http://www.webmin.com)
## Run this command: wget [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc) -O- | sudo apt-key add -
deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib

#### Wine - [https://launchpad.net/~ubuntu-wine/+archive/ppa/]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa/")
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) oneiric main

#### X Updates - [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) oneiric main

#### Xorg Edgers - [https://launchpad.net/~xorg-edgers]("https://launchpad.net/%7Exorg-edgers")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) oneiric main

#### Yuuguu - [http://yuuguu.com](http://yuuguu.com)
deb [http://update.yuuguu.com/repositories/apt](http://update.yuuguu.com/repositories/apt) hardy multiverse


####### 3rd Party Source Repos

#### Audacity (Source) - [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys     1024R/BB901940
deb-src [http://ppa.launchpad.net/audacity-team/daily/ubuntu](http://ppa.launchpad.net/audacity-team/daily/ubuntu) oneiric main 

#### AWN (Avant Window Navigator) Testing Packages (Source) - [http://awn-project.org/](http://awn-project.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb-src [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) oneiric main

#### Banshee (Source) - [https://edge.launchpad.net/~banshee-team]("https://edge.launchpad.net/%7Ebanshee-team")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) oneiric main

#### Chromium Project (Source) - [http://code.google.com/chromium/](http://code.google.com/chromium/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) oneiric main

#### Cortina (Source) - [https://launchpad.net/~cs-sniffer/+archive/cortina]("https://launchpad.net/%7Ecs-sniffer/+archive/cortina")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CA186228
deb-src [http://ppa.launchpad.net/cs-sniffer/cortina/ubuntu](http://ppa.launchpad.net/cs-sniffer/cortina/ubuntu) oneiric main

#### DeaDBeeF (Source) - [http://deadbeef.sourceforge.net/](http://deadbeef.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
deb-src [http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu](http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu) oneiric main

#### Equinox (Source) - [https://launchpad.net/~tiheum/+archive/equinox]("https://launchpad.net/%7Etiheum/+archive/equinox")
## Run this command: sudo apt-get update && sudo apt-get install faenza-icon-theme && sudo apt-get install equinox-theme    
deb-src [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) oneiric main

#### FBReader (Source) - [http://www.fbreader.org/desktop/](http://www.fbreader.org/desktop/)
## Run this command: [http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc](http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc) -O- | sudo apt-key add -
deb-src [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) stable main 

#### Flacon (Source) - [http://kde-apps.org/content/show.php?content=113388](http://kde-apps.org/content/show.php?content=113388)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
deb-src [http://ppa.launchpad.net/flacon/ppa/ubuntu](http://ppa.launchpad.net/flacon/ppa/ubuntu) oneiric main

#### Gimp SVN (Source) - [https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn]("https://launchpad.net/%7Ematthaeus123/+archive/mrw-gimp-svn")
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 405A15CB
deb-src [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu) oneiric main 

#### Glx-Dock / Cairo-Dock (Source) - [http://www.glx-dock.org](http://www.glx-dock.org)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb-src [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu) oneiric main

#### GNUzilla and IceCat (Source) - [http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 
deb-src [http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu](http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu) oneiric main  

#### Gwibber (Daily) (Source) - [https://launchpad.net/gwibber](https://launchpad.net/gwibber)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb-src [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) oneiric main

#### HandBrake Snapshots (Source) - [http://handbrake.fr/](http://handbrake.fr/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb-src [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu) oneiric main

#### Ironhide (Source) - [https://launchpad.net/~mj-casalogic/+archive/ironhide/]("https://launchpad.net/%7Emj-casalogic/+archive/ironhide/")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ECF7E0B3
deb-src [http://ppa.launchpad.net/mj-casalogic/ironhide/ubuntu](http://ppa.launchpad.net/mj-casalogic/ironhide/ubuntu) oneiric main 

#### Kubuntu Backports (Source) - [https://edge.launchpad.net/~kubuntu-ppa/+archive/backports]("https://edge.launchpad.net/%7Ekubuntu-ppa/+archive/backports")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb-src [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) oneiric main

#### Kubuntu Beta Backports (Source) - [https://launchpad.net/~kubuntu-ppa/+archive/beta]("https://launchpad.net/%7Ekubuntu-ppa/+archive/beta")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb-src [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) oneiric main

#### Kubuntu Experimental (Source) - [https://launchpad.net/~kubuntu-ppa/+archive/experimental]("https://launchpad.net/%7Ekubuntu-ppa/+archive/experimental")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 493B3065
deb-src [http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu) oneiric main

#### Kubuntu Updates (Source) - [https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa]("https://edge.launchpad.net/%7Ekubuntu-ppa/+archive/ppa")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb-src [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) oneiric main 

#### LibreOffice (Source) - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) oneiric main

#### Medibuntu (Source) - [http://www.medibuntu.org/](http://www.medibuntu.org/) 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free

#### Midori (Source) - [https://launchpad.net/~midori/+archive/ppa]("https://launchpad.net/%7Emidori/+archive/ppa")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb-src [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) oneiric main

#### Miro HD Video Player (Source) - [http://www.getmiro.com/](http://www.getmiro.com/)
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D75E850
deb-src [http://ppa.launchpad.net/pcf/miro-releases/ubuntu](http://ppa.launchpad.net/pcf/miro-releases/ubuntu) oneiric main

#### MKVToolnix (Source) - [http://www.bunkus.org/videotools/mkvtoolnix/](http://www.bunkus.org/videotools/mkvtoolnix/)
## Run this command: wget -q [http://www.bunkus.org/gpg-pub-moritzbunkus.txt](http://www.bunkus.org/gpg-pub-moritzbunkus.txt) -O- | sudo apt-key add -
deb-src [http://www.bunkus.org/ubuntu/oneiric/](http://www.bunkus.org/ubuntu/oneiric/) ./ 

#### Mozilla Daily Build Team (Source) - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("http://edge.launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) oneiric main

#### OpenShot (Source) - [http://www.openshotvideo.com](http://www.openshotvideo.com)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA
deb-src [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) oneiric main

#### Paissad's PS3 Media Server Repo (Source) - [http://deb.paissad.net](http://deb.paissad.net)
## Run this command: wget -q -O - [http://deb.paissad.net/public-key.asc](http://deb.paissad.net/public-key.asc) | sudo apt-key add -
deb-src [http://deb.paissad.net](http://deb.paissad.net) unstable main contrib non-free personal

#### Pidgin (Source) - [http://pidgin.im](http://pidgin.im)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) oneiric main

#### qBittorrent (Source) - [http://qbittorrent.sourceforge.net/](http://qbittorrent.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 47B4D1C4
deb-src [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu) oneiric main

#### Tor: anonymity online (Source) - [http://www.torproject.org/](http://www.torproject.org/)
## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 94C09C7F  | sudo apt-key add -
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) oneiric main

#### Ubuntu Tweak (Source) - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) oneiric main

#### UbuntuGIS (unstable) (Source) - [http://trac.osgeo.org/ubuntugis/wiki](http://trac.osgeo.org/ubuntugis/wiki)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 314DF160
deb-src [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu) oneiric main

#### UNetbootin (Source) - [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb-src [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) oneiric main

#### WebKit Team PPA (Source) - [https://launchpad.net/~webkit-team/+archive/ppa]("https://launchpad.net/%7Ewebkit-team/+archive/ppa")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B
deb-src [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) oneiric main

#### Wine (Source) - [https://launchpad.net/~ubuntu-wine/+archive/ppa/]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa/")
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) oneiric main 

#### X Updates (Source) - [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) oneiric main

#### Xorg Edgers (Source) - [https://launchpad.net/~xorg-edgers]("https://launchpad.net/%7Exorg-edgers")
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) oneiric main


[LIST]
[*] Source list ends here.
[/LIST]
```

---

### Post by philinux on 2012-06-12
Please use code tags for posts like the above. Highlight text and use the # button.

---

