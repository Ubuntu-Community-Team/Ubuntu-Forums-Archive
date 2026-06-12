---
title: "Upgrade 10.04 to 12.04"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by gscratch on 2012-08-14
I am currently running 10.04 and have been for a while.  Update Manager starting saying that 11.(something, sorry, I'm not in front of the machine at this moment) was available a while ago, but after reading here, I decided to wait for 12.04.
 
Update Manager is still saying that 11 is available.  When I clicked on it (thinking it might just take me to 12.04), I got a message that that 11 is no longer available (which is ok with me, based on my previous comment about wanting to wait for 12.04)
 
So, shall I wait until Update Manager offers 12.04 ? or manually get to 12.04 ? (if so, how?) or just stay at 10.04, which has been fine for my modest needs.
 
thanks,

---

### Post by Kalanac on 2012-08-14
Hi there,

When you update more than one version, you kinda update through the versions in between.

Let's get this updgrade a cooking then :)

First hit ctrl+alt+t to open a terminal window.

You should then enter the following commands:

```
sudo apt-get update
```

This checks your current repositories and looks for any new updates.  You'll likely be asked to type in your password, this is because commands with sudo are ran as root.

```
sudo apt-get upgrade
```

This will install the new packages, but won't upgrade your distro version.  It's always best to begin by fully updating your current packages though.  This may or may not do stuff, depending on if there are any packages to update.  If no packages are updated, don't sweat it, it just means everything is up to date already.  This time, you should notice that you weren't asked for your password.  This is fine, sudo privilege persists for a while for convenience.  It'll lock up again after a few minutes or when you close the terminal.

Next, we'll clean away any packages that might be lurking about, but not used any more.  These tend to happen from time to time, nothing to worry about and easy to fix:

```
sudo apt-get autoremove
```

This'll clear away any useless packages, again, it might not do anything and again this is fine.

Right, now for the version upgrade:

```
sudo do-release-upgrade
```

This will then set about changing the repos to the next version and updating the packages.  This is the most important part, go pop the kettle on and make a cup of tea.  You should select a biscuit that dips well, about 3 should do it :D.  Wait for the upgrade to finish, it should just trundle on by itself.

You should run another autoremove after as some packages are made redundant by release upgrades.

That aught to do it, post if you have problems.

---

### Post by cryptotheslow on 2012-08-14
> **Kalanac said:**
> Hi there,

When you update more than one version, you kinda update through the versions in between.


True for non-LTS release versions. However there is a direct upgrade path between LTS versions - so in this case 10.04 to 12.04 is a single upgrade process. i.e. there is no need to go through 10.10, 11.04, 11.10 to get to 12.04.

**gscratch - **Have a look at your update manager settings for the option called something like "Notify me of a new Ubuntu version:" and try setting it to the LTS (long-term support) version only. Then hit Check again in Update Manager and see if it offers you the 12.04LTS version.

Backup your crucial files before doing the upgrade :)

---

### Post by wildmanne39 on 2012-08-14
Hi, if you are upgrading from 10.04 it would be best to backup your important data and install a fresh ubuntu because there are many differences between 10.04 and 11.04 thru 12.04 it will save you a lot of headaches.
Thanks

---

### Post by gscratch on 2012-08-14
Thanks for the quick replies.  I'm now at my machine and Update Manager offers 10.10 (not 11 as I said previously) and it does give the 'this version is no longer available' message as I said

Under Settings -> Updates tab, Release Upgrade,  I choose "LTS releases only" as suggested.  "10.10 is available" is still shown.  Click "Check" and I get this message:

W: GPG error: [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A4B44C2D2A2203E

I'm downloading the 12.04 ISO so I can do a complete new install, as recommended, if I decide to go that way.


Again, I'm not having any trouble (that I know of) wtih 10.04 I just want to stay current
thanks,


thanks,

---

### Post by cryptotheslow on 2012-08-14
That's odd, my 10.04 desktop offers me the 12.04 upgrade (I'm holding off for now as I use it daily).

10.04 is supported until April next year so there is no rush here.

> 
W: GPG error: [http://www.openprinting.org](http://www.openprinting.org)  lsb3.2 Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 7A4B44C2D2A2203E
This may well be a clue as to why you don't get offered the LTS upgrade - it suggests your sources list may have a problem - although one key being unavailable shouldn't nobble any others.

Can you open a Terminal and post up the response you get to this command:
```

sudo apt-get update

```That command just updates the software lists, it makes no changes to your system.

And also this one:
```

cat /etc/apt/sources.list

```That will list which repositories your system is checking for updates. Alternatively you could open that file in a text editor and post back the contents.

Please post the responses in [ CODE] tags (use the # button on the post toolbar).

---

### Post by wildmanne39 on 2012-08-14
Moved to own thread!

---

### Post by gscratch on 2012-08-16
I'm ok with you moving this discussion to its own thread.  Can you point me to that thread?  I don't see it in the Absolute Beginners

thanks

---

### Post by gscratch on 2012-08-16
thanks, I see it now.  I had to log out and back in a couple times.

In response to the help:
```

sudo apt-get update
...
Fetched 2,125kB in 4s (430kB/s)
Reading package lists... Done
W: GPG error: http://www.openprinting.org lsb3.2 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A4B44C2D2A2203E
W: Duplicate sources.list entry http://ppa.launchpad.net/pmcenery/ppa/ubuntu/ lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_pmcenery_ppa_ubuntu_dists_lucid_main_binary-i386_Packages)

(do you need the entire return?)

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu lucid main #deb-src http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu lucid main
deb http://ppa.launchpad.net/pmcenery/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/pmcenery/ppa/ubuntu lucid main


```

I have downloaded the 12.04 ISO and burned it onto a CD using Roxio on a Windows machine.  I did not select "make the disk bootable" thinking that that mean Windows.  However, my machine did not boot from that CD (confirmed that CDROM is the first boot source in the BIOS).  I will make another CD selecting 'bootable'

thanks for the help,

---

### Post by cryptotheslow on 2012-08-17
Can you remember why you added those last two sources lines?

These:
```
deb http://ppa.launchpad.net/pmcenery/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/pmcenery/ppa/ubuntu lucid main
```

I'd be inclined to comment them out in /etc/apt/sources.list before carrying out an upgrade.

And when you say you see it now - do you mean the upgrade is now offered by Update Manager?

You might want to consider holding off the upgrade until around 23rd August when version 12.04.1 is released.

---

### Post by gscratch on 2012-08-19
I have commented out the last two lines of sources.list as suggested

I don't recall ever touching this file before

by 'it' I meant my thread when it was moved.  Update Manager does not offer 12.04 but it no longer offers 10.10

I will wait until the end of August as suggested

thanks,

---

### Post by dodo3773 on 2012-08-20
> **Wild Man said:**
> Hi, if you are upgrading from 10.04 it would be best to backup your important data and install a fresh ubuntu because there are many differences between 10.04 and 11.04 thru 12.04 it will save you a lot of headaches.
Thanks

This ^^. Do not upgrade. Do a clean install. Seriously

---

### Post by aero23 on 2012-08-21
> **dodo3773 said:**
> This ^^. Do not upgrade. Do a clean install. Seriously

Ugh, wish I knew that yesterday. So, how does a noob do a fresh install? Is there a manual process for removing what's currently there first?

---

### Post by dodo3773 on 2012-08-21
> **aero23 said:**
> Ugh, wish I knew that yesterday. So, how does a noob do a fresh install? Is there a manual process for removing what's currently there first?

You download the ISO, burn it to a disk, boot from it and install. Just like you would normally install any fresh system.

---

### Post by aero23 on 2012-08-21
> **dodo3773 said:**
> You download the ISO, burn it to a disk, boot from it and install. Just like you would normally install any fresh system.

Figured so, but that seems too easy. Forgot to mention I have it as a dual boot; still that easy? Will it see the existing partition and reinstall over it? Also - I *think* I had installed it from Windows originally because it shows up in the program list and it has a folder on the C: drive. Don't know if that throws a wrench in the works.

Thanks for taking the time to help us know-nothings.):P

---

### Post by dodo3773 on 2012-08-21
> **aero23 said:**
> Also - I *think* I had installed it from Windows originally because it shows up in the program list and it has a folder on the C: drive. Don't know if that throws a wrench in the works.

Thanks for taking the time to help us know-nothings.):P

It sounds as if you did a wubi install. That may be part of why you are having such a hard time understanding all this. There should be some kind of way to remove it directly from Windows I am assuming. I am unsure though as I have never used Wubi. Look in your installed applications in Windows to verify. From there you can remove it and do a new Wubi install or a real dual boot.

---

### Post by gscratch on 2012-08-25
Thanks to all the help I got here, I have installed a brand-new 12.04
I won't mark this one 'solved' since there are other posters, but as far as I'm concerned, this one is sorted.

I have a couple questions, but I'll start a new thread.

---

### Post by PlasticArmyMan on 2013-05-29
I know i'm bumping an old thread....

at my workplace three of our machines are running 10.04 and Update Manager is telling me to update to 12.04...

if i click it and let it run...what kind of issues may i run into afterwards?...or will it work just like it does right now?....

I usually update my home machine with clean installs everytime, without backing anything up other than music pictures and game files...I have never updated through Update Manager before and I have never tried to do a dirty update before either...So I am wondering if I should let it do it's magic or just keep going on with 10.04

---

### Post by dodo3773 on 2013-05-29
> **PlasticArmyMan said:**
> I know i'm bumping an old thread....

at my workplace three of our machines are running 10.04 and Update Manager is telling me to update to 12.04...

if i click it and let it run...what kind of issues may i run into afterwards?...or will it work just like it does right now?....

I usually update my home machine with clean installs everytime, without backing anything up other than music pictures and game files...I have never updated through Update Manager before and I have never tried to do a dirty update before either...So I am wondering if I should let it do it's magic or just keep going on with 10.04

Always do a clean install.

---

