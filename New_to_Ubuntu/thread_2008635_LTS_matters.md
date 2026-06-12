---
title: "LTS matters"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by czgirb on 2012-06-23
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) said:
LTS is we get free security updates for desktop and server version.

When our Ubuntu LTS terms is no longer supported, what is the differ between LTS and we type the following command at Terminal:
sudo apt-get update && sudo apt-get upgrade

Please guide me ...
Thank you

---

### Post by drpjkurian on 2012-06-23
I didn't understand your question.

---

### Post by ell02 on 2012-06-23
In previous releases, a Long Term Support (LTS) version had 3 years support on Ubuntu (Desktop) and 5 years on Ubuntu Server. Starting with Ubuntu 12.04 LTS, both versions will receive 5 years support.

---

### Post by hansdown on 2012-06-23
Hi czgirb.

That command will upgrade your system to the next release.

Upgrades sometimes work, but " a fresh install fixes all", especially, if the file system changes.

eg: EXT3>EXT4, etc.

---

### Post by bab1 on 2012-06-23
> **hansdown said:**
> Hi czgirb.

That command will upgrade your system to the next release.

Upgrades sometimes work, but " a fresh install fixes all", especially, if the file system changes.

eg: EXT3>EXT4, etc.

Almost, but not quite right.  The command *sudo apt-get update *refreshes the repositories and *sudo apt-get upgrade* then upgrades the current installation packages.  If you want to upgrade to the next version you need to use sudo apt-get dist-upgrade.

@czgirb,

The LTS only sets the length of the support (LTS=long term support).  When the support term runs out the supported repos are closed.  No more support at all.  This means that although the OS will continue to run you will only have access to the archived repos.  These archived repos are static (e.g not updated).

---

### Post by critin on 2012-06-23
> **czgirb said:**
> [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) said:
LTS is we get free security updates for desktop and server version.

When our Ubuntu LTS terms is no longer supported, **what is the differ between LTS and we type the following command at Terminal:**
sudo apt-get update && sudo apt-get upgrade

Please guide me ...
Thank you

Your question isn't clear.  All versions get free security updates, not only the LTS versions.

Updates and Upgrades are two different things.  If you ask for upgrade, (when it's offered on the update package manager) you will get the next dist. version.



Is this a test?  ;)

---

### Post by bab1 on 2012-06-23
> **critin said:**
> Your question isn't clear.  All versions get free security updates, not only the LTS versions.

Updates and Upgrades are two different things.  If you ask for upgrade, you will get the next dist. version.

hansdown's answer to your question was correct.
AND updates your packages.  Actually, sometimes you'll need to refresh the repositories manually.

Is this a test?  ;)

From the APT-GET(8 ) man pages ```
 **[COLOR="Red"]update[/COLOR]**
           update is used to resynchronize the package index files from their
           sources. 
```

^^^ These are the repos

Again from the APT-GET(8 ) man pages ```
**[COLOR="Red"]upgrade[/COLOR]**
           upgrade is used to install the newest versions of all packages
           **[COLOR="Red"]currently installed[/COLOR]** on the system from the sources enumerated in
           /etc/apt/sources.list.
```
^^^ This is for the currently installed packages.

[COLOR="Blue"]Edit:[/COLOR]> (**critin** - when it's offered on the update package manager)[COLOR="Blue"]
^^^ In apt-get this would be the command shown below[/COLOR]```
apt-get dist-upgrade
```

---

### Post by hansdown on 2012-06-23
Thanks for that, bab1.

---

### Post by critin on 2012-06-23
Thanks for the correction, bab1.  I thought the OP was asking how to (upgrade) to the next version when the version running could no longer supported and couldn't  be updated.    The answer to the question "The difference between LTS and the command?"  is a hard one to answer.  

> **When our Ubuntu LTS terms is no longer supported**, **what is the differ between LTS and we type the following command** 



I update through the terminal using only: 
> sudo apt-get update     
not using "&& sudo apt-get upgrade"    It works.  lol

---

### Post by bab1 on 2012-06-23
> **critin said:**
> Thanks for the correction, bab1.  I thought the OP was asking how to (upgrade) to the next version when the version running could no longer supported and couldn't  be updated.    The answer to the question "The difference between LTS and the command?"  is a hard one to answer.  

I update through the terminal using only: 
    
not using "&& sudo apt-get upgrade"    It works.  lol

The choice of terms; update and upgrade is unfortunate.  So all this time you have been refreshing the repos and not really updating?  Now you know; upgrade really is the one to do for updates to the apps.  But then we all use the GUI Update Manager anyway.  ;-)

---

### Post by czgirb on 2012-06-23
Dear all!
I ask this because I found there are so many people, which still used an older version of Ubuntu, 8.04 or 9.04, which the Support is no longer supported ... and the important thing, they are unwilling to used the newer version.
That's why I curious how can they maintain for staying with the old one.

PS:
I tried 12.04 already ... but I still prefer 10.04 better.
So, I wish to stay with Lucid. But I'm affraid to LTS terms, which WILL LAST only a YEAR.

Any suggestion?

---

### Post by coffeecat on 2012-06-23
> **bab1 said:**
> Almost, but not quite right.  The command *sudo apt-get update *refreshes the repositories and *sudo apt-get upgrade* then upgrades the current installation packages.  If you want to upgrade to the next version you need to use sudo apt-get dist-upgrade.

Almost, but not quite right. :wink: It's a common misunderstanding that apt-get dist-upgrade does an upgrade to the next version - it doesn't. It's needed for some dependency handling and is the default backend behaviour for synaptic when that is used for upgrading. From man apt-get:

> dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages. The /etc/apt/sources.list file
           contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.


For upgrading to the next release, you use "sudo do-release-upgrade". From the man page for do-release-upgrade:

> Upgrade  the  operating  system  to  the  latest  release from the com&#8208;
       mand-line.  This is the preferred command if the machine has no graphic
       environment  or  if the machine is to be upgraded over a remote connec&#8208;
       tion.


> **czgirb said:**
> Dear all!
I ask this because I found there are so many people, which still used an older version of Ubuntu, 8.04 or 9.04, which the Support is no longer supported ... and the important thing, they are unwilling to used the newer version.
That's why I curious how can they maintain for staying with the old one.


You cannot maintain an unsupported version in a secure state. No further support means no security patches, and no bugfixes.

> **czgirb said:**
> I tried 12.04 already ... but I still prefer 10.04 better.
So, I wish to stay with Lucid. But I'm affraid to LTS terms, which WILL LAST only a YEAR.

You have less than 1 year of support left for the desktop version of 10.04. What is it that you prefer about 10.04? Is it the classic desktop? There are ways of installing a desktop similar to the 10.04 one in 12.04 - see the middle link in my sig.

---

### Post by bab1 on 2012-06-23
> **czgirb said:**
> Dear all!
I ask this because I found there are so many people, which still used an older version of Ubuntu, 8.04 or 9.04, which the Support is no longer supported ... and the important thing, they are unwilling to used the newer version.
That's why I curious how can they maintain for staying with the old one.
There's certainly no reason to stop using a host with 10.04 when the technical support runs out.  The OS will always be at the state it is in on the last day of support.  It doesn't stop working after that date.  I have an old 8.04 host myself.  I'm about to re-purpose it into a 12.04 server.  But for now it runs fine.  The apps seem really ancient though.  Remember no updates or upgrades, everything is frozen at EOL.> 
PS:
I tried 12.04 already ... but I still prefer 10.04 better.
So, I wish to stay with Lucid. But I'm affraid to LTS terms, which WILL LAST only a YEAR.
Any suggestion?

This is an entirely different (although related) matter.  All Ubuntu versions will change. My personal workstation is 10.04 (Lucid) and I will be forced to upgrade the distribution to 12.04.  I'm going to try both the Gnome Shell and Unity with an open mind.  You can however try Linux Mint which is based on Ubuntu.  It uses a fork of Gnome2 (like what is on 10.04).  I have no idea what the Mint policy is on LTS or if they even have LTS however.

---

### Post by bab1 on 2012-06-23
> **coffeecat said:**
> Almost, but not quite right. :wink: It's a common misunderstanding that apt-get dist-upgrade does an upgrade to the next version - it doesn't. It's needed for some dependency handling and is the default backend behaviour for synaptic when that is used for upgrading. From man apt-get:



For upgrading to the next release, you use "sudo do-release-upgrade". From the man page for do-release-upgrade:




That's nice to know.  Although I don't upgrade releases.  I just install fresh.  ;-)> 
...
You have less than 1 year of support left for the desktop version of 10.04. What is it that you prefer about 10.04? Is it the classic desktop? There are ways of installing a desktop similar to the 10.04 one in 12.04 - see the middle link in my sig.
This is really Gnome3 anyway and it is a viable option to get the look and feel of Gnome2.  I wonder what is left out though.

Thank you @coffeecat for the info, especially the option of Gnome Classic.

---

