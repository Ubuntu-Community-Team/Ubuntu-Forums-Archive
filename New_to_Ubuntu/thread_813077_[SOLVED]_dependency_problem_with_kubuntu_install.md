---
title: "[SOLVED] dependency problem with kubuntu install"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by chin_chin on 2008-05-30
Hi, I have installed Ubuntu 7.10 Gutsy Gibbon which comes with an Install DVD and 5 Repository DVDs. I added all 6 DVDs to the Synaptic Package Manager, which now shows 23143 packages listed.
If I try to install either kubuntu-desktop or kde package, it won't go through due to dependency problems. I can install other programs without problems though. It doesn't work with command line either.
Thanks in advance for any help. What should I do or try out ?

This is what I get in shell konsole:

```
rock@Roadster:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kdebase-kio-plugins but it is not going to be installed
                   Depends: kdesktop but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: konq-plugins but it is not going to be installed
                   Recommends: amarok but it is not going to be installed
                   Recommends: digikam but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: kmailcvt but it is not going to be installed
                   Recommends: kmplayer-konq-plugins but it is not going to be installed
                   Recommends: konqueror but it is not going to be installed
                   Recommends: konqueror-nsplugins but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Recommends: strigi-applet but it is not going to be installed
E: Broken packages
rock@Roadster:~$
```

---

### Post by aysiu on 2008-05-31
Six DVDs?

You probably have conflicting repositories.

[Get a fresh repositories list](http://psychocats.net/ubuntu/sources#key) and then ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by chin_chin on 2008-05-31
Hi, I resolved the issue just by downloading all available updates using update manager. I had 218 packages. I disables that option right after the install. And now it works, I put KDE on the machine.

Thanks for your help.

---

