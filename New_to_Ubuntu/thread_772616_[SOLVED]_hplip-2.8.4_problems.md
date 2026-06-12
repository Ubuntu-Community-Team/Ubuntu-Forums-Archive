---
title: "[SOLVED] hplip-2.8.4 problems"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by DamonChyld on 2008-04-28
The hplip-2.8.4 installer for my HP printer is telling me that I need to install cups. Libcups2 seems to be installed, both here when I run apt-get and in synaptic.

```
:~/Desktop$ sudo apt-get install --yes --force-yes libcupsys2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcupsys2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I have tried to reinstall it, but receive the same error.

```
RUNNING PRE-INSTALL COMMANDS
----------------------------


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 1 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups (cups - Common Unix Printing System)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 1 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - Shell scanning program)


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo apt-get update (Pre-depend step 3)


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes libcupsys2'
Please wait, this may take several minutes...
Running 'sudo apt-get install --yes --force-yes libsane'
Please wait, this may take several minutes...
 

RUNNING POST-PACKAGE COMMANDS
-----------------------------


RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'cups (cups - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.
```

I would really appreciate any help, I am not sure how to move forward on this.

---

### Post by bcn17 on 2008-05-02
I'm not sure if this will help-
I just tried installing hplip-2.8.4 by the command:
sh hplip-2.8.4.run

When ever I said a for automatic install it gave me an error 100. I know this is not your error however I was using automatic install

I eventually tried a manual install by selecting that option (still using the automatic installer) from [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html) select automatic installer and just answered its questions. Basically say yes to all of it. It did say i had unresolved dependencies and if i wanted to install it so I said yes. and everything worked. So- if you were trying automatic or got the file somewhere else try this one and use manual. GOOD LUCK! keep us informed.

---

### Post by DamonChyld on 2008-05-02
It was a bit hairy but I got this fixed. 

I went through the custom install and skipped CUPS (thanks bcn17). Hp-setup errored but that finally gave me something to work with (error: Print command failed with exit code 256! ;) ) which directed me to remove cupsys cupsys-client (which incidently remove A LOT including ubuntu-desktop :(). 

Reinstalled everything and dar she prints ;)

---

### Post by DamonChyld on 2008-05-03
Hmm, I tried printing something this morning from the laptop and found that CUPS was not running (I would get a "problem loading page error" at [http://localhost:631/admin](http://localhost:631/admin)). 

A quick sudo /etc/init.d/cupsys restart solved the problem but it seems that this is an indicator of another CUPS issue. How do I trouble shoot this further (as uninstalling/reinstalling everything didn't fix it I assume that there is a config file or some sort that needs to get looked at?)

---

