---
title: "I Need Help Installing Plymouth Manager"
date: 2015-12-07
forum: New to Ubuntu
---

### Post by Darth4212 on 2015-12-07
I am currently running Ubuntu 15.10 Wily Werewolf, and I want to install Plymouth Manager so I can change my splash screen.
I followed the instructions that were listed it won't install. I am going to list the inputs and outputs that I get and hope that you guys can find the problem.
First I typed ```
sudo apt-add-repository ppa:mefrio-g/plymouthmanager
```
Then it gave me the output;
 ```
 In this ppa you can find the latest stable release of Plymouth Manager

To add it type in a terminal:


- sudo apt-add-repository ppa:mefrio-g/plymouthmanager
- sudo apt-get update
- sudo apt-get install plymouth-manager




 More info: https://launchpad.net/~mefrio-g/+archive/ubuntu/plymouthmanager
Press [ENTER] to continue or ctrl-c to cancel adding it

```
I then pressed enter and then it said:
```
gpg: keyring `/tmp/tmpf_iu__fl/secring.gpg' createdgpg: keyring `/tmp/tmpf_iu__fl/pubring.gpg' created
gpg: requesting key 849919D3 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpf_iu__fl/trustdb.gpg: trustdb created
gpg: key 849919D3: public key "Launchpad PPA for Mario Guerriero" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

```
After I typed ```
sudo apt-get update
```
And it gave me the output
```
Hit http://security.ubuntu.com wily-security InReleaseHit http://archive.canonical.com wily InRelease
Ign http://ppa.launchpad.net wily InRelease
Hit http://security.ubuntu.com wily-security/main Sources
Hit http://security.ubuntu.com wily-security/restricted Sources
Hit http://security.ubuntu.com wily-security/universe Sources
Ign http://ppa.launchpad.net wily Release.gpg
Hit http://archive.canonical.com wily/partner Sources
Hit http://security.ubuntu.com wily-security/multiverse Sources
Hit http://security.ubuntu.com wily-security/main amd64 Packages
Ign http://ppa.launchpad.net wily Release
Hit http://archive.canonical.com wily/partner amd64 Packages
Hit http://security.ubuntu.com wily-security/restricted amd64 Packages
Hit http://security.ubuntu.com wily-security/universe amd64 Packages
Hit http://security.ubuntu.com wily-security/multiverse amd64 Packages
Hit http://archive.canonical.com wily/partner i386 Packages
Hit http://security.ubuntu.com wily-security/main i386 Packages
Hit http://security.ubuntu.com wily-security/restricted i386 Packages
Hit http://security.ubuntu.com wily-security/universe i386 Packages
Hit http://archive.canonical.com wily/partner Translation-en
Hit http://security.ubuntu.com wily-security/multiverse i386 Packages
Hit http://security.ubuntu.com wily-security/main Translation-en
Hit http://security.ubuntu.com wily-security/multiverse Translation-en
Hit http://security.ubuntu.com wily-security/restricted Translation-en
Hit http://security.ubuntu.com wily-security/universe Translation-en
Hit http://us.archive.ubuntu.com wily InRelease
Hit http://us.archive.ubuntu.com wily-updates InRelease
Hit http://us.archive.ubuntu.com wily-backports InRelease
Hit http://us.archive.ubuntu.com wily-proposed InRelease
Hit http://us.archive.ubuntu.com wily/main Sources
Hit http://us.archive.ubuntu.com wily/restricted Sources
Hit http://us.archive.ubuntu.com wily/universe Sources
Hit http://us.archive.ubuntu.com wily/multiverse Sources
Hit http://us.archive.ubuntu.com wily/main amd64 Packages
Hit http://us.archive.ubuntu.com wily/restricted amd64 Packages
Hit http://us.archive.ubuntu.com wily/universe amd64 Packages
Hit http://us.archive.ubuntu.com wily/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com wily/main i386 Packages
Hit http://us.archive.ubuntu.com wily/restricted i386 Packages
Hit http://us.archive.ubuntu.com wily/universe i386 Packages
Hit http://us.archive.ubuntu.com wily/multiverse i386 Packages
Hit http://us.archive.ubuntu.com wily/main Translation-en
Hit http://us.archive.ubuntu.com wily/multiverse Translation-en
Hit http://us.archive.ubuntu.com wily/restricted Translation-en
Hit http://us.archive.ubuntu.com wily/universe Translation-en
Hit http://us.archive.ubuntu.com wily-updates/main Sources
Hit http://us.archive.ubuntu.com wily-updates/restricted Sources
Hit http://us.archive.ubuntu.com wily-updates/universe Sources
Hit http://us.archive.ubuntu.com wily-updates/multiverse Sources
Hit http://us.archive.ubuntu.com wily-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com wily-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com wily-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com wily-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com wily-updates/main i386 Packages
Hit http://us.archive.ubuntu.com wily-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com wily-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com wily-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com wily-updates/main Translation-en
Hit http://us.archive.ubuntu.com wily-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com wily-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com wily-updates/universe Translation-en
Hit http://us.archive.ubuntu.com wily-backports/main Sources
Hit http://us.archive.ubuntu.com wily-backports/restricted Sources
Hit http://us.archive.ubuntu.com wily-backports/universe Sources
Hit http://us.archive.ubuntu.com wily-backports/multiverse Sources
Hit http://us.archive.ubuntu.com wily-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com wily-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com wily-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com wily-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com wily-backports/main i386 Packages
Hit http://us.archive.ubuntu.com wily-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com wily-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com wily-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com wily-backports/main Translation-en
Hit http://us.archive.ubuntu.com wily-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com wily-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com wily-backports/universe Translation-en
Err http://ppa.launchpad.net wily/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net wily/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net wily/main Translation-en_US
Ign http://ppa.launchpad.net wily/main Translation-en
Hit http://us.archive.ubuntu.com wily-proposed/universe amd64 Packages
Hit http://us.archive.ubuntu.com wily-proposed/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com wily-proposed/restricted amd64 Packages
Hit http://us.archive.ubuntu.com wily-proposed/main amd64 Packages
Hit http://us.archive.ubuntu.com wily-proposed/universe i386 Packages
Hit http://us.archive.ubuntu.com wily-proposed/multiverse i386 Packages
Hit http://us.archive.ubuntu.com wily-proposed/restricted i386 Packages
Hit http://us.archive.ubuntu.com wily-proposed/main i386 Packages
Hit http://us.archive.ubuntu.com wily-proposed/main Translation-en
Hit http://us.archive.ubuntu.com wily-proposed/multiverse Translation-en
Hit http://us.archive.ubuntu.com wily-proposed/restricted Translation-en
Hit http://us.archive.ubuntu.com wily-proposed/universe Translation-en
W: Failed to fetch http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/wily/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

```
After I typed in ```
sudo apt-get install plymouth-manager
```
And then it gave me the output
```
Reading package lists... DoneBuilding dependency tree
Reading state information... Done
E: Unable to locate package plymouth-manager

```
So now what do I do. What is the problem and try to be specific as possible I am new to Ubuntu.
I am also sorry if this is in the wrong section of the forums I am new.

---

### Post by chili555 on 2015-12-07
> W: Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/wily/main/binary-amd64/Packages)  [COLOR="#FF0000"]404  Not Found[/COLOR]It appears that the PPA hasn't been updated in a long time; at least since 2011. That's a hundred Ubuntu-years! I am quite confident that there are no packages for Wily.

I suggest you look elsewhere for plymouth-manager. Sorry.

---

### Post by Dennis N on 2015-12-07
You can install Plymouth themes manually without too much effort. Here is a thread dealing with this:

[http://ubuntuforums.org/showthread.php?t=2279649](http://ubuntuforums.org/showthread.php?t=2279649)

There are specific instructions in posts #3 and #5.

Some of these themes (like Earth Sunrise that is mentioned there) that are animated are probably not so desirable any more, since computers boot so quickly with SSD. I am not sure how Earth Sunrise for example would work with an SSD. Would it complete (takes 20 seconds or so) or just abort to the login? I don't know.

---

### Post by Darth4212 on 2015-12-07
Is there anyway to use a program that is from an older version of ubuntu?

---

### Post by Dennis N on 2015-12-07
> **codyslimshady9 said:**
> Is there anyway to use a program that is from an older version of ubuntu?

In general, you can install programs from .deb files. I install from .deb files using gdebi package installer to make that easier - gdebi is in the Ubuntu repositories. gdebi retrieves any dependencies for you if they are available. If these dependencies are not available in your sources, or other package conflicts exist, then it informs you and aborts the install. Even if you get it installed, there is no guarantee how well it will work.

---

### Post by Darth4212 on 2015-12-07
chili555 I have a new issue what should I do about this error * The application gtk-qt-engine (java-gtk-tqt-application) crashed and caused the signal 11 (SIGSEGV)*

---

### Post by Portaro on 2015-12-07
In my case I have Plymouth manager installed on Lubuntu 14.04, as you can see in pctures screen.

[https://launchpad.net/plymouth-manager](https://launchpad.net/plymouth-manager)

[IMG]http://s25.postimg.org/kkph6mogf/2015_12_07_211501_1280x1024_scrot.png[/IMG]

I download the .deb file of launchpad account and works at this time, but in past I have a problem with this program to lauch , I think is a gtk problem that is solved with the update - upgrade of system .

You have in the following my lsb_release -a command output ->

LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:core-4.1-ia32:core-4.1-noarch:security-4.0-ia32:security-4.0-noarch:security-4.1-ia32:security-4.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty

In my case I use Flavitu 14.04 version of Lubuntu, derivative project.

---

### Post by chili555 on 2015-12-07
> **codyslimshady9 said:**
> chili555 I have a new issue what should I do about this error * The application gtk-qt-engine (java-gtk-tqt-application) crashed and caused the signal 11 (SIGSEGV)*I am very sorry. Plymouth and themes, etc. are not my specialty. I have no further suggestions. 

I am sure that Portaro knows far more about this than I do.

---

