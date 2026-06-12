---
title: "Help with HP3050a printer on Ubuntu 12.04"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by parducpiskota on 2012-06-28
Hi!

First, sorry for my not perfect english, I'm Hungarian :) I have an annoying problem. I want to install my HP3050a printer on Ubuntu 12.04. I have downloaded HPLIP, but it has so mny dependencies. I have found all package except one. GCC (GNU C or C++ Compiler) I've installed all package with similar name in Synaptic, but the installer is still misses this one.
Please help me, how can I get this package, or how can I ignore this request? (I think, this package is installed)

Thanks for the answers.

---

### Post by oldos2er on 2012-06-28
Post moved to its own thread.

---

### Post by mapes12 on 2012-06-29
If you installed HPLIP through Software Centre then you do not have the most up to date driver. Go to the HPLIP website and follow the instructions to install the latest driver. The file will probably download to your Download folder. Drag it to your Desktop then follow the instructions for running the script. Many people forget to run the script thinking just dowloading the driver is sufficient. It isn't. The script needs to be run to get the files into your system.

This should then solve your dependency problem.

---

### Post by Cheesemill on 2012-06-29
There is no need to manually find and install all of the dependencies, the installer takes care of that for you.

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by parducpiskota on 2012-06-29
I have to tell you: I'm a beginner. I have Linux since 1 week :)

What kindof script should I run? Where is that and what's the name?


Yes, I tought the installer downloads the dependencies, but doesn't. I have dovloaded HPLIP from that location, what Cheesemill wrote. I followed the intructions.
But first I filled out the Install Wizzard, and then Downloaded the suggested version of hplip.

The installer stucks here:

INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 1 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)

INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 6 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency for option 'gui_qt4': pyqt4-dbus (PyQt 4 DBus - DBus Support for PyQt4)
warning: Missing REQUIRED dependency for option 'gui_qt4': pyqt4 (PyQt 4- Qt interface for Python (for Qt version 4.x))
warning: Missing REQUIRED dependency for option 'fax': dbus (DBus - Message bus system)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'scan': xsane (xsane - Graphical scanner frontend for SANE)
CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.
RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo apt-get update (Pre-depend step 3)
OK
DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --assume-yes build-essential'
Please wait, this may take several minutes...
-

The line is just spinning and nothing happens.
I've waited for an hour, but nothing happens. I can't stop the process with Ctrl+D. 
By the way I tried to install gcc manually but terminal said I have the latest.

---

