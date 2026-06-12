---
title: "Can't update/upgrade Ubuntu Gutsy or Hardy!"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by karlo on 2008-08-16
Last March or April, I upgraded my Ubuntu Gutsy to Ubuntu Hardy, the preview version. Then right now, Aug. 16, 2008, I was able to connect to the internet. I received a message that I can update/upgrade it, partially. I even tried disabling the backports etc.. Just download the stable version of the packages. Nothing happened.

Then I followed this thread: [http://ubuntuforums.org/showthread.php?t=838761&page=2](http://ubuntuforums.org/showthread.php?t=838761&page=2) and [http://www.ubuntugeek.com/upgrade-ubuntu-710-gutsy-gibbon-to-ubuntu-804-lts-hardy-heron.html](http://www.ubuntugeek.com/upgrade-ubuntu-710-gutsy-gibbon-to-ubuntu-804-lts-hardy-heron.html)

Well, at least no partial upgrade message. I'm downloading 700mb worth of packages. Unfortunately I had to disconnect by 400MB, have to go home.

Will my Ubuntu OS work? And will the method I used, will it work?

sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

---

### Post by Malta paul on 2008-08-16
You could give this link a try:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

But it might me an idea if you download Hardy 8.04-1 an ISO file and burn it as a live CD and do a clean install, Just back up the files you need from your old system _first_, then you can reinstall them on you new system.

:)

---

### Post by karlo on 2008-08-22
Is there a possibility to just update/upgrade the whole system? because I can't do a clean install as off the moment, also, all of the configurations and personalizations i made here at my ubuntu OS will be gone, right?

> **Malta paul said:**
> You could give this link a try:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

But it might me an idea if you download Hardy 8.04-1 an ISO file and burn it as a live CD and do a clean install, Just back up the files you need from your old system _first_, then you can reinstall them on you new system.

:)

---

### Post by mrprogle on 2010-05-31
i can't update my ubuntu too. when i want it, i get a error message like below.

[IMG]http://img257.imageshack.us/img257/3593/screenshotja.png[/IMG]

how can i fix it??

---

### Post by dannyjmh on 2010-06-02
Hey everybody! Need your help. I'm trying to update my Jaunty to Karmic from a local repository, in my partner's hd, which is mounted in mine. But it seems that the command *apt-get update* is skipping (or somehow not finding) the content of the file sources.list. So when i run:

 *sudo apt-get update* 

i get:

[I] apt-get: update
Get: [http://ftp.debian.org](http://ftp.debian.org) sid/main Sources[/I]

and the system gets stuck trying to get the main source from the internet. When i type:


  [I]sudo aptitude update

[/I]i get:

Ign file: karmic Release.gpg
Ign file: karmic/main Translation-en_US
Ign file: karmic/multiverse Translation-en_US
Ign file: karmic/universe Translation-en_US
Ign file: karmic/restricted Translation-en_US
Ign file: karmic-backports Release.gpg
Ign file: karmic-backports/main Translation-en_US
Ign file: karmic-backports/multiverse Translation-en_US
Ign file: karmic-backports/universe Translation-en_US
Ign file: karmic-backports/restricted Translation-en_US
Ign file: karmic-proposed Release.gpg
Ign file: karmic-proposed/main Translation-en_US
Ign file: karmic-proposed/multiverse Translation-en_US
Ign file: karmic-proposed/universe Translation-en_US
Ign file: karmic-proposed/restricted Translation-en_US
Ign file: karmic-security Release.gpg
Ign file: karmic-security/main Translation-en_US
Ign file: karmic-security/multiverse Translation-en_US
Ign file: karmic-security/universe Translation-en_US
Ign file: karmic-security/restricted Translation-en_US
Ign file: karmic-updates Release.gpg
Ign file: karmic-updates/main Translation-en_US
Ign file: karmic-updates/multiverse Translation-en_US
Ign file: karmic-updates/universe Translation-en_US
Ign file: karmic-updates/restricted Translation-en_US
Ign file: karmic Release.gpg        
Ign file: karmic/free Translation-en_US
Ign file: karmic/non-free Translation-en_US
Ign file: karmic Release            
Ign file: karmic-backports Release  
Ign file: karmic-proposed Release   
Ign file: karmic-security Release   
Ign file: karmic-updates Release    
Ign file: karmic Release            
Ign file: karmic/main Packages      
Ign file: karmic/multiverse Packages
Ign file: karmic/universe Packages  
Ign file: karmic/restricted Packages
Ign file: karmic-backports/main Packages
Ign file: karmic-backports/multiverse Packages
Ign file: karmic-backports/universe Packages
Ign file: karmic-backports/restricted Packages
Ign file: karmic-proposed/main Packages
Ign file: karmic-proposed/multiverse Packages
Ign file: karmic-proposed/universe Packages
Ign file: karmic-proposed/restricted Packages
Ign file: karmic-security/main Packages
Ign file: karmic-security/multiverse Packages
Ign file: karmic-security/universe Packages
Ign file: karmic-security/restricted Packages
Ign file: karmic-updates/main Packages
Ign file: karmic-updates/multiverse Packages
Ign file: karmic-updates/universe Packages
Ign file: karmic-updates/restricted Packages
Ign file: karmic/free Packages      
Ign file: karmic/non-free Packages  
Ign file: karmic/main Packages      
Ign file: karmic/multiverse Packages
Ign file: karmic/universe Packages  
Ign file: karmic/restricted Packages
Ign file: karmic-backports/main Packages
Ign file: karmic-backports/multiverse Packages
Ign file: karmic-backports/universe Packages
Ign file: karmic-backports/restricted Packages
Ign file: karmic-proposed/main Packages
Ign file: karmic-proposed/multiverse Packages
Ign file: karmic-proposed/universe Packages
Ign file: karmic-proposed/restricted Packages
Ign file: karmic-security/main Packages
Ign file: karmic-security/multiverse Packages
Ign file: karmic-security/universe Packages
Err [http://linux.dropbox.com](http://linux.dropbox.com) jaunty Release.gpg
  Could not resolve 'yourproxyaddress'
Err [http://linux.dropbox.com](http://linux.dropbox.com) jaunty/main Translation-en_US
  Could not resolve 'yourproxyaddress'
Ign file: karmic-security/restricted Packages
Ign file: karmic-updates/main Packages
Ign file: karmic-updates/multiverse Packages
Ign file: karmic-updates/universe Packages
Ign file: karmic-updates/restricted Packages
Ign file: karmic/free Packages
Ign file: karmic/non-free Packages
Err file: karmic/main Packages
  File not found
Err file: karmic/multiverse Packages
  File not found
Err file: karmic/universe Packages
  File not found
Err file: karmic/restricted Packages
  File not found
Err file: karmic-backports/main Packages
  File not found
Err file: karmic-backports/multiverse Packages
  File not found
Err file: karmic-backports/universe Packages
  File not found
Err file: karmic-backports/restricted Packages
  File not found
Err file: karmic-proposed/main Packages
  File not found
Err file: karmic-proposed/multiverse Packages
  File not found
Err file: karmic-proposed/universe Packages
  File not found
Err file: karmic-proposed/restricted Packages
  File not found
Err file: karmic-security/main Packages
  File not found
Err file: karmic-security/multiverse Packages
  File not found
Err file: karmic-security/universe Packages
  File not found
Err file: karmic-security/restricted Packages
  File not found
Err file: karmic-updates/main Packages
  File not found
Err file: karmic-updates/multiverse Packages
  File not found
Err file: karmic-updates/universe Packages
  File not found
Err file: karmic-updates/restricted Packages
  File not found
Err file: karmic/free Packages
  File not found
Err file: karmic/non-free Packages
  File not found
Reading package lists... Done

Here's the content of my *sources.list* file:

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy main restricted
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy universe
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy universe
# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-updates universe
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy multiverse
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy multiverse
# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# deb [http://debyrpms.mes.edu.cu:8080/ubuntu](http://debyrpms.mes.edu.cu:8080/ubuntu) hardy main multiverse universe restricted
# deb [http://debyrpms.mes.edu.cu:8080/ubuntu](http://debyrpms.mes.edu.cu:8080/ubuntu) hardy-backports main multiverse universe restricted
# deb [http://debyrpms.mes.edu.cu:8080/ubuntu](http://debyrpms.mes.edu.cu:8080/ubuntu) hardy-proposed main multiverse universe restricted
# deb [http://debyrpms.mes.edu.cu:8080/ubuntu](http://debyrpms.mes.edu.cu:8080/ubuntu) hardy-security main multiverse universe restricted
# deb [http://debyrpms.mes.edu.cu:8080/ubuntu](http://debyrpms.mes.edu.cu:8080/ubuntu) hardy-updates main multiverse universe restricted

deb file:///mnt/data_zeus/Ubuntu karmic main multiverse universe restricted
deb file:///mnt/data_zeus/Ubuntu karmic-backports main multiverse universe restricted
deb file:///mnt/data_zeus/Ubuntu karmic-proposed main multiverse universe restricted
deb file:///mnt/data_zeus/Ubuntu karmic-security main multiverse universe restricted
deb file:///mnt/data_zeus/Ubuntu karmic-updates main multiverse universe restricted
deb file:///mnt/data_zeus/Ubuntu/medibuntu karmic free non-free


Help wanted please!! Thank you all in advance.

---

### Post by VarshaJaikumar on 2010-08-21
> **mrprogle said:**
> i can't update my ubuntu too. when i want it, i get a error message like below.

[IMG]http://img257.imageshack.us/img257/3593/screenshotja.png[/IMG]

how can i fix it??

Public key missing.
Try the following: [http://varshamyspace.blogspot.com/2009/11/rectifying-apt-get-gpg-error.html](http://varshamyspace.blogspot.com/2009/11/rectifying-apt-get-gpg-error.html)

---

