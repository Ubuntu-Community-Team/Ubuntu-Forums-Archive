---
title: "moving from 15.10 to 16.04 and preserving application settings"
date: 2016-04-24
forum: New to Ubuntu
---

### Post by Mel_Blakey on 2016-04-24
If I do a fresh install. what is the best way to save program settings? 

Also, what is the benefit of upgrading? I tried out a live version on a usb and didn't see anything new except the software centre.

---

### Post by buzzingrobot on 2016-04-24
> **Mel_Blakey said:**
> If I do a fresh install. what is the best way to save program settings? 

Applications typically keep their settings, and a user's adjustments to them, in files/directories in that user's home directory.  Hence, the common recommendation to put /home on its own partition and preserve it over release upgrades. 

You could create an archive file of /home, copy it someplace safe, then extract the relevant files after the upgrade is complete and move them into place.

Bear in mind that applications sometimes do change the format and/or location of their configuration files. In those cases, using old config files may not work well.

If you haven't done an unusual amount of tweaking and configuration, and don't feel comfortable creating archives, etc., it might be simpler and no more time consuming to simply set up everything from scratch after the upgrade.

> Also, what is the benefit of upgrading? I tried out a live version on a usb and didn't see anything new except the software centre.

If you are on a non-LTS release, the advantage is that you avoid losing support when you hit the 9-month mark.

Upgrades roll up security patches, application and driver updates, use a newer kernel, add new features and usability fixes, etc.  If you are using one of the "flavors",  then you need to consider the changes specific to that. Unity in 16.04 is a mature product.

The upgrade process is not magic.  The more changes made to a baseline installation by the user, the greater the chance an upgrade will fail. In particular, users often forget to back out all PPA's they have installed.  That mean's both the PPA as a source repository and packages installed from that PPA.

---

### Post by T.J. on 2016-04-24
> **Mel_Blakey said:**
> If I do a fresh install. what is the best way to save program settings? 

Also, what is the benefit of upgrading? I tried out a live version on a usb and didn't see anything new except the software centre.

There are a few benefits.  16.04 is a long term support release - 5 years support, which means it is probably a lot more stable.  15.10 will only be supported for 9 months after release, which means you only have about 5 months of support left.  

There is a downside if you need AMD FGLRX support. 16.04 has none (and probably never will). AMD made the decision to not support the FGLRX driver anymore, not  Ubuntu.  They did so unilaterally, so eventually older Radeon cards won't work  in Windows either. 

Linux has its own Radeon driver, so you can still use your  older card for as long as you want.  

It is just that some Steam games might not work without  FGLRX.  The alternative for 16.04 users is to either use the open Radeon driver on 16.04 or buy a new video card with a GCN chipset. If you HAVE to use FGLRX, I would consider using Debian Stable or Ubuntu 14.04, at least until this gets settled.   Debian 8 was released in 2015 so it will be supported until at least 2020. Ubuntu 14.04 will be supported until 2019.  Both of which can support FGLRX.



===

The best way to preserve your settings is to backup your home directory, including the hidden files, to an external drive.  How you do that depends on how comfortable with Linux.

In order to backup my settings I might use: 

*tar -czvfp configs.tar.gz .[a-z,A-Z]**


Backup the gz file with the rest  as you normally would.  

Then when you need the settings, copy it to your home. 

To extract it:
[I]
tar -xvfp configs.tar.gz[/I]

---

### Post by DuckHook on 2016-04-24
Thread moved to *'New to Ubuntu'*

---

### Post by grahammechanical on 2016-04-24
The release notes itemise what is new.

As usual with every new release, what is new is not the sort of thing that can make ordinary users go, WOW! That is just the way it is. Most users should stick to an LTS release. Anyone with very new hardware might need the latest release because the boring bits of what is new might be the very hardware driver modules they need.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Regards

---

