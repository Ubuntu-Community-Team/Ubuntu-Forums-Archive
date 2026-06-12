---
title: "Screenlets problem"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by darkoblivion on 2008-06-22
Hi everyone,

I've been with Ubuntu for about a year now, despite my measly 2 posts, which is mainly due to this forum doing such a good job of providing me with solutions to my problems without me even having to ask =) Kudos

But this time I'm kinda stumped. I just upgraded to Hardy Heron, and everything is awesome, but when I tried to install screenlets, I cam up with problems multiple times. The most recent time, it wouldn't even let me install in synaptic manager. I get this:


Selecting previously deselected package screenlets.
(Reading database ... 163528 files and directories currently installed.)
Unpacking screenlets (from .../screenlets_0.1.2-1ubuntu1_all.deb) ...
Setting up screenlets (0.1.2-1ubuntu1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing screenlets (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 screenlets
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up screenlets (0.1.2-1ubuntu1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing screenlets (--configure):
 subprocess post-installation script returned error exit status 1


This might be residue from a previous screenlets install that I didn't properly remove? Because I have been trying to install it a buncha times, and uninstalled it each time due to another problem: when I go into the screenlets-manager, it has a format where the Install and all the buttons are on the left side while all the screenshots I have seen have those buttons on the right side. 

Anyway, when I choose any application to display, nothing happens at all. They don't display on my desktop at all.

I also should mention that I am using thunar and xfdesktop to draw my desktop instead of nautilus. I don't know if that might have anything to do with the screenlets. For a while other things wouldn't display on my desktop (when I didn't have xfdesktop, and I guess nothing was drawing my desktop).

Sorry for the long post! I hope someone can help me out!!

---

### Post by niyonk on 2008-06-25
Have you tried removing the screenlets program COMPLETELY from the synaptics package manager? (it will remove all configurations)

Cheers! :)

---

