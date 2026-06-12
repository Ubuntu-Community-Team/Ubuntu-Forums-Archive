---
title: "Can I upgrade Ubuntu by changing the sources.list  ?"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by MikeJParry on 2013-03-13
Hello, I would like to know what are the pros and cons of upgrading my Ubuntu by changing the sources.list file, like changing from precise to quantal and then update and upgrade.

---

### Post by tgalati4 on 2013-03-13
It will either work, or it won't work.  Either way, it will take some time.

Use *sudo apt-get dist-upgrade* after changing your repos.

I always advocate clean installs.  The time you save (configuration of all of your hardware and software) is often overrun by broken stuff--hardware and software.  It will probably take the same amount of time to accomplish a clean install and redo all of your configuration and installing additional packages.  Make a list of your existing packages--there are plenty of tutorials on how to do that.

Backup up /home and /etc in anycase.

---

### Post by schragge on 2013-03-13
Please take a look at [Release Notes for Debian 7.0 (wheezy)]("http://www.debian.org/releases/testing/amd64/release-notes/ch-upgrading.en.html"). Yes, it's about Debian, but most things there also apply to Ubuntu.

---

### Post by deadflowr on 2013-03-13
For the most part changing the sources.list should work.
But if you've added any ppa or third party repos, then they'd need to be disabled also.

---

### Post by snowpine on 2013-03-13
The various upgrade methods are compared [here]("https://help.ubuntu.com/community/Upgrades"). Here's what they have to say about doing it "the Debian way"  (editing souces.list).

> The Debian way of upgrading

Please be aware that this method is valid, yet not officially advised by the Ubuntu developers. 

For 90% of users I would recommend the simple and supported "Desktop / GUI upgrade" procedure. Do you have specific requirements why you prefer the Debian way?

---

### Post by MikeJParry on 2013-03-13
Thanks for responding so quickly, I was not aware about the Debian way.
So, there shouldn't be any major cons using the Debian way to upgrade Ubuntu right ?

---

### Post by snowpine on 2013-03-13
The Debian method is not as well-tested as the Ubuntu-advised method.
On the other hand, the Ubuntu-advised method is well tested, yet this testing has discovered many bugs. 
I tend to agree with tgalati4's advice that a fresh reinstall is an option worth considering.

---

### Post by schragge on 2013-03-13
To understand what the Debian way means, read the release notes for Debian I linked above. There's a full chapter there concerning distribution upgrade. Then decide for yourself.

---

### Post by quequotion on 2013-03-13
> **MikeJParry said:**
> Hello, I would like to know what are the pros and cons of upgrading my Ubuntu by changing the sources.list file, like changing from precise to quantal and then update and upgrade.In short, yes you can.
This is the way it is meant to be done; the Debian way.
"dist-upgrade" means distribution-upgrade and this is exactly what it's intended to do.

I usually upgrade by this method, but it does have it's complications.

pros:
-Not having to arbitrarily remove over half of your software and ditch all your configuration files with no explanation.
-PPAs (that are still active) can be upgraded along with official packages.
-Keep your current software configurations (mostly) intact.
-No need to reconfigure partitions, no formating, no need to reinstall a bootloader, etc and all those other things that *brick my machine* **every single time** I use Canonical's installer.

cons:
-Version conflicts abound (PPA packages and backport versions may be higher than the next distro's official packages; some packages will be obsoleted and replaced by packages with *different names*; some configuration files very likely need updates; etc)
-Convoluted dependency chains (Not everything will upgrade smoothly. Apt will find the safest route and hold back things that don't work--then you need to fix them by hand)
-On occasion, the Ubuntu sofware suite gets updated or reverted (shotwell or f-spot?; rhythmbox or banshee?; etc) and you'll probably end up with both installed.
-No one seems to believe me that this really is the best way. (Maybe I'm just a noob, maybe Canonical's installer doesn't destroy *everything* it touches...)

I have a proof-of-concept script, which you should *absolutely not* copy-> paste -> run.
Read through it, understand it, and then do these things one step at a time, by hand.
This process takes care of *most* of the version conflicts and dependency problems.
```
#!/bin/bash

# Ubuntu Upgrade, The Debian Way.

#PHASE ONE
#Downloads the upgradeable packages from the main repository.

# Ignore PPAs for phase one
for f in /etc/apt/sources.list.d/*.list;
    do
        mv "$f" "${f%list}list.ignore";
    done

# Set all main sources from Precise to Quantal
sed -i 's/precise/quantal/g' /etc/apt/sources.list

# Clean apt's cache and update package lists
apt-get clean
apt-get update

# Add pin to ensure Quantal packages (even downgrades)
echo -e "\nPackage: *\nPin: release v=12.10\nPin-Priority: 1001" >> /etc/apt/preferences

# Download packages from main sources
apt-get -d dist-upgrade

#PHASE TWO
#Downloads the upgradeable packages from user-added sources.

# Re-enable PPAs 
for f in /etc/apt/sources.list.d/*.list.ignore;
    do
        mv "$f" "${f%.list.ignore}.list";
    done

# Set all PPAs from Precise to Quantal
for f in /etc/apt/sources.list.d/*.list;
    do
        sed -i 's/precise/quantal/g' "$f";
    done

# Clean apt's cache and update again
apt-get clean
apt-get update

# Download packages from PPAs
apt-get -d dist-upgrade

#PHASE THREE
#Until this point, all changes can be reversed.

# Install the downloaded packages & upgrade the distribution
apt-get dist-upgrade

# Resolving dependency chains manually (not the only way):
# Force install new packages, overwriting old ones, with:
# dpkg -i --force overwrite /var/cache/apt/archives/NEW PACKAGE NAME
# Then remove old packages with:
# apt-get remove OLD PACKAGE NAME
# Then reinstall the new package
# dpkg -i /var/cache/apt/archives/NEW PACKAGE NAME

# Make sure everything is done
# apt-get dist-upgrade
# dpkg --config -a
# update-initramfs -u -k all

# Restore Quantal packages pin from /etc/apt/preferences
# Check thoroughly for leftover Precise packages.

# Leftover Precise packages can be found in Synaptic
# Sort the package list by "Origin" and look under "Local"
# These packages are not available in a repository.
# They could be hand-made, obsolete, temporarily unavailable, or discontinued.
# Some are probably obsolete Precise packages.
```

---

### Post by ManamiVixen on 2013-03-13
Yes you can install by changing the sources. I just did it and it works.

---

