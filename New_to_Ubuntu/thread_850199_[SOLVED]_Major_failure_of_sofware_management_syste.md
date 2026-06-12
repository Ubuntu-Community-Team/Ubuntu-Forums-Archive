---
title: "[SOLVED] Major failure of sofware management system"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by taminrob on 2008-07-05
Tried to open "add/remove" software and received the following:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

So, I opened a terminal and entered the sudo commands.

rob@robs-acer:~$ sudo apt-get update
[sudo] password for rob: 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                           
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]              
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [29.0kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [276kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6156B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [7567B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6626B]   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [79.1kB]        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [906B]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [20.8kB]    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [3308B]      
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [907B]    
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [69.5kB]   
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [3465B]   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]      
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [15.0kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [12.0kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [1943B]
Fetched 650kB in 3s (173kB/s)   
Reading package lists... Done

And:

rob@robs-acer:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org-core
The following NEW packages will be installed:
  openoffice.org-core
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
15 not fully installed or removed.
Need to get 0B/26.8MB of archives.
After this operation, 113MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 120462 files and directories currently installed.)
Unpacking openoffice.org-core (from .../openoffice.org-core_1%3a2.4.1-1ubuntu2_i386.deb) ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libpackage2.so')
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rob@robs-acer:~$ 

So, what needs to be fixed and how do I fix it?

---

### Post by rockerphil on 2008-07-05
first off i'd open up the Synaptic Package Manager, it should automatically fix any broken packages. then as the message said i'd check the content of your /etc/apt/sources.list file and make sure there's no errors, then run the same cods you ran again if you correct any errors in the /etc/apt/sources.list file, if you'd like plz plst the contents of the file and i'd be willing to help


Phil

---

### Post by taminrob on 2008-07-05
Bare with me if I get this wrong.  I think this is what you were asking for (this is /etc/apt/sources.list.save):

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

/etc/apt/sources.list opens my sources window, and that has pretty much everything checked it it.

Thanks for your help! 

If I am not doing this correctly, let me know how to get the info that you need and I'll do it that way.

---

### Post by taminrob on 2008-07-05
Also:   If I remove OpenOffice with synaptic manager, then I can open the "add/remove".  I just run into problems when I try to reinstall OpenOffice.

---

### Post by Vadi on 2008-07-05
Can you try installing OOo from Synaptic?

Also, do you remember any conditions that led to this? If you do, then reporting it as a bug would help fix such occurence in the future.

---

### Post by taminrob on 2008-07-05
Tried to install OO in synaptic and received the following error:

E: /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program /libpackage2.so')

This is the same error that I receive each time I try to install OO.   Each time it gets to installing openoffice.org-core I receive that error.

As far as what may have led to this, I do not know.  The only thing I did was try to install the updates that listed for todays update check.

---

### Post by taminrob on 2008-07-05
Received this post in another thread about the same problem in not quite as much detail-

________________________________________________________________________

 Re: OpenOffice "core" screwed up
Code:

sudo apt-get clean

This will get rid of any cached files - the openoffice ones seems to be corrupt.
Then you need to run apt-get update and then you can install openoffice

________________________________________________________________________

Following those instructions I installed OO with no other troubles.  Thanks for you suggestions...hopefully this will help others that may have this trouble.

---

