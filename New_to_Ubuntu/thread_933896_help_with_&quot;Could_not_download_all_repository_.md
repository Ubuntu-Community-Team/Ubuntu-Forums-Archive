---
title: "help with &quot;Could not download all repository indexes&quot;"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Madwida on 2008-09-29
Hi

The update icon has been appearing in my panel.  I click on it and am told it's been 8 days since the last update.  The following message then appears.  Any thoughts?  Thanks a lot as always

GPG error: [http://apt.wicd.net](http://apt.wicd.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755AFailed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  multiversedeb/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Pelham123 on 2008-09-30
Have a look here which will help with the GPG part:

[http://amazing-development.com/archives/2006/02/24/fixing-gpg-errors-with-apt-get-for-dummies-like-me/](http://amazing-development.com/archives/2006/02/24/fixing-gpg-errors-with-apt-get-for-dummies-like-me/)

Could you also post your sources.list please. Found at /etc/apt/sources.list

Thanks

---

### Post by jemate18 on 2008-09-30
open a terminal

type
sudo apt-get update

and if you want to upgrade, type
sudo apt-get upgrade

---

### Post by Madwida on 2008-09-30
> **jemate18 said:**
> open a terminal

type
sudo apt-get update

and if you want to upgrade, type
sudo apt-get upgrade

Thanks.  I tried this, too, last night and it's the same message in the terminal that I posted here.  Upgrade installed 0 upgrades.  .So I will try post 2's suggestions

---

### Post by Madwida on 2008-09-30
> **Pelham123 said:**
> Have a look here which will help with the GPG part:

[http://amazing-development.com/archives/2006/02/24/fixing-gpg-errors-with-apt-get-for-dummies-like-me/](http://amazing-development.com/archives/2006/02/24/fixing-gpg-errors-with-apt-get-for-dummies-like-me/)

Could you also post your sources.list please. Found at /etc/apt/sources.list

Thanks

Hi 

I tried the instructions in the link but got the same message in the terminal--thanks for the suggestion, however.

Here's my sources list: 

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
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
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiversedeb [http://ppa.launchpad.net/m-buck/ubuntu](http://ppa.launchpad.net/m-buck/ubuntu) hardy main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
deb [http://ppa.launchpad.net/m-buck/ubuntu](http://ppa.launchpad.net/m-buck/ubuntu) hardy main

---

### Post by Elfy on 2008-09-30
Yopu have 2 problems here - the public key thing should be solved by running this in aterminal

```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

The other problem will be solved by editing the file, this is from close to the end of your sources list
```
deb http://security.ubuntu.com/ubuntu hardy-security [COLOR="Red"]multiversedeb[/COLOR] http://ppa.launchpad.net/m-buck/ubuntu hardy main
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://apt.wicd.net hardy extras
deb http://ppa.launchpad.net/m-buck/ubuntu hardy main
```

Edit the file with ```
gksudo gedit /etc/apt/sources.list
```

go to end of multiverse and enter for new line it should read

```
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/m-buck/ubuntu hardy main
```
save and close gedit, then run

```
sudo apt-get update
```

---

### Post by Madwida on 2008-09-30
A quick thanks.  I will try this when I get home.  A huge help--what would I do without the forum?!  Someday I will be able to offer help in return.

---

### Post by Madwida on 2008-10-01
> **Madwida said:**
> A quick thanks.  I will try this when I get home.  A huge help--what would I do without the forum?!  Someday I will be able to offer help in return.

Hi again,

Is this right?  

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/m-buck/ubuntu](http://ppa.launchpad.net/m-buck/ubuntu) hardy main
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
deb [http://ppa.launchpad.net/m-buck/ubuntu](http://ppa.launchpad.net/m-buck/ubuntu) hardy main

I just want to make sure; I've learned from hard experience that following instructions EXACTLY is the only way to go!  I was not sure if i should delete the first line or the redundant line.  

Thanks again.

---

### Post by Madwida on 2008-10-01
> **Madwida said:**
> Hi again,

Is this right?  

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/m-buck/ubuntu](http://ppa.launchpad.net/m-buck/ubuntu) hardy main
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
deb [http://ppa.launchpad.net/m-buck/ubuntu](http://ppa.launchpad.net/m-buck/ubuntu) hardy main

I just want to make sure; I've learned from hard experience that following instructions EXACTLY is the only way to go!  I was not sure if i should delete the first line or the redundant line.  

Thanks again.

I asked the above b/c I got this when I updated in the terminal:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  multiversedeb/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
christian@christian-laptop:~$

---

