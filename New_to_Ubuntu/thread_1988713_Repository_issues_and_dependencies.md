---
title: "Repository issues and dependencies"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by jdix123 on 2012-05-28
I'm having trouble updating and upgrading due to unmet dependencies that are not in my repositories list (I think)

According to Synaptic, the packages are

libgegl-0.0-0
libgimp2.0
scribus

This is my sources.list

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports restricted main multiverse universe
```

What am I missing?

---

### Post by fantab on 2012-05-28
As far as I can tell there is nothing amiss about your sources.list.  You can use this [**LINK**]("http://repogen.simplylinux.ch/") to regenerate your repos. Delete all the contents of your sources.list and copy paste the list you have generated using above link.

$ sudo apt-get clean all
$ sudo apt-get update


If that doesn't fix... then try removing GIMP and Scribus and reinstall them.

---

### Post by jdix123 on 2012-05-28
Tried your suggestions.  I went to that link and rebuilt my sources.  Then I ran 

```
sudo apt-get remove scribus
sudo apt-get remove gimp
```

Then I tried this 

```
jasond@Natalie:/etc/apt$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: gimp-data (<= 2.6.11-z) but 2.7.5-2012020902~oo is to be installed
E: Unable to correct problems, you have held broken packages.

jasond@Natalie:/etc/apt$ sudo apt-get install scribus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 scribus : Depends: libtiff4 (> 3.9.5-3~) but 3.9.5-1ubuntu1.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

I don't get the message about broken packages, because synaptic says I have 0 broken.


And running this command still brings up these messages at the end

```
sudo apt-get update 

W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 7D2C7A23BF810CD5 Launchpad PPA for Awn Testing Team
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 4874D3686E80C6B7 Launchpad PPA for Banshee Team

W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 52165BD6B9BA26FA Launchpad OpenShot Development PPA
W: Failed to fetch http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/oneiric/Release  

W: Failed to fetch http://debian.scribus.net/debian/dists/testing/Release  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages  404  Not Found [IP: 209.170.117.56 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by fantab on 2012-05-28
I think you have added a some unnecessary repos. Just keep it like this:

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse 
```Then:[INDENT]```
$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update
 # exit

```Or

```
$ sudo rm /var/lib/apt/lists/* -vf
$ sudo apt-get update
```
[/INDENT]

---

### Post by jdix123 on 2012-05-28
Maybe my understanding of these repos is incorrect.  If I don't include the awn repo, for example, will I be notified and upgraded when a new version is released, just by running apt-get update && install ?  I thought I needed those repositories to be included?

Also, I appreciate the help.  So I know for the future, what is the purpose of clearing the /var/lib/apt/lists file?


Still getting errors on apt-get update

```
Fetched 17.5 MB in 4min 25s (65.8 kB/s)                                                                                                                                
W: Failed to fetch http://debian.scribus.net/debian/dists/testing/Release  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages  404  Not Found [IP: 66.171.225.19 80]

W: Failed to fetch http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

which I don't get, because those aren't even in my sources.list anymore

---

### Post by cortman on 2012-05-28
Check the directory /etc/apt/sources.list.d. There'll likely be a file for each missing repository in there- delete them.
/var/lib/apt/lists is where the files containing lists of all packages available on the repositories are located. Removing these and running apt-get update will give you fresh lists, in case one was corrupted or something.

---

### Post by jdix123 on 2012-05-28
can I just hose the whole directory to start fresh?  Or do I need some of them?

Alright, almost there I think.  One last error

```
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9
```

is there a similar directory I can purge of old keys?  Or some way to update this one?

---

### Post by cortman on 2012-05-28
Why would you just delete all of them? Like you said earlier, if you have awn, it's probably a good idea to keep the awn repository intact so you can get updates.
I would just find the ones that are missing and delete them, although you could just delete all of them if you wanted, I suppose.

---

### Post by Old_Grey_Wolf on 2012-05-28
You are  missing a GPG Key, so enter these commands to get it.

```
gpg --keyserver keyserver.ubuntu.com --recv 3B22AB97AF1CDFA9

gpg --export --armor 3B22AB97AF1CDFA9 | sudo apt-key add -
```

---

