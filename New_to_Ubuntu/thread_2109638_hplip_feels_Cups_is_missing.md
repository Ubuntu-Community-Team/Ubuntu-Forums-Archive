---
title: "hplip feels Cups is missing"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by dugong_bud on 2013-01-28
Dear All, 

I tried to make my hp laserjet 1020 working on xubuntu 12.04. There are many posts regarding this, but none seemed to cover my issue. I started here:

[http://www.jroller.com/gmazza/entry/hp_laserjet_1020_with_ubuntu](http://www.jroller.com/gmazza/entry/hp_laserjet_1020_with_ubuntu)
and followed hplip instructions...

hplip installation aborts, as it cannot solve that **cups is missing**(although it is installed - checked in synaptic[I]) see end of the post for error message
[/I]
When starting:
sudo hp-setup -i


Clearly the ppd file for laserjet 1020 is  missing, so it cannot finish.

I tried to add the printer in Cups ([http://localhost:631/](http://localhost:631/)), it worked, and it prints the test page. 

Nevertheless the printer never appears as installed, so I cannot choose it for printing a eg. pdf.


I copy the code and the error I get, look for the error at the end.

abel@Majlis:~$ cd Desktop/
abel@Majlis:~/Desktop$ sh hplip-3.12.11.run
Creating directory hplip-3.12.11
Verifying archive integrity... All good.
Uncompressing HPLIP 3.12.11 Self Extracting Archive.........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 3.12.11)
HPLIP Installer ver. 5.1

Copyright (c) 2001-14 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Mon-28-Jan-2013_10:13:51.log

\
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.
-
 

INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : 
Initializing. Please wait...


INTRODUCTION
------------
This installer will install HPLIP version 3.12.11 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).
 

DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 12.04.

Is "Ubuntu 12.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER USER PASSWORD
-------------------
Please enter the sudoer (abel)'s password: 
Password accepted


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.  During the install process you will be added to the lp and lpadmin group, please quit the installer before the setup stage, log out, log back in, and run hp-setup to complete the install.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 3 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups (CUPS - Common Unix Printing System)
warning: Missing REQUIRED dependency: cups-image (CUPS image - CUPS image development files)
warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 1 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
A package manager '/bin/sh/usr/bin/synaptic-pkexec' appears to be running. Please quit the package manager and press enter to continue (i=ignore, r=retry*, f=force, q=quit) :r


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
**warning: An error occurred running 'sudo apt-get update'**
sudo apt-get update (Pre-depend step 3)
OK


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --assume-yes libcups2'
Please wait, this may take several minutes...
Running 'sudo apt-get install --assume-yes libcupsimage2-dev'
Please wait, this may take several minutes...
Running 'sudo apt-get install --assume-yes libjpeg62-dev'
Please wait, this may take several minutes...
Running 'sudo apt-get install --assume-yes libcupsimage2-dev'
Please wait, this may take several minutes...
Running 'sudo apt-get install --assume-yes libsane-dev'
Please wait, this may take several minutes...
[B]error: A required dependency 'cups (CUPS - Common Unix Printing System)' is still missing.
[/B]

RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
[B]error: A required dependency 'cups (CUPS - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.[/B]
abel@Majlis:~/Desktop$ 


---
btw I  also added myself as member to the lp group sucessfully. Several restarts tried s well.


----------------
**Bonus question:**

I found in a forum the following recommendation to resolve the printer problem:
( [http://ubuntuforums.org/showthread.php?t=1576589](http://ubuntuforums.org/showthread.php?t=1576589) )
[I]
sudo aptitude install --assume-yes libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane[/I]

now it actually started to remove packages completely unrelated (programs that I work with and has nothing to do with printing, desktop packages) at that point I broke  it up,  nevertheless synaptic did not work and indeed e.g copasi was removed. 
[B]
What happened? [/B]
I found nothing explicitly harmful in the code, but I will be very carefuly with "assume yes" from now on.

---

### Post by ccrs8 on 2013-01-28
I have that exact printer, and it is a pain in the you-know-what to get working.  I have been using it since Ubuntu 7.04.  I upgrade Ubuntu every 6 months, and only once did the printer remain working through an upgrade.

I have never been able to get any official HP software (HPLIP) working consistently.  Often I would go through the auto-install process that is launched when I first plug in the printer after upgrading (or a fresh install) and it will work the first time but then not again after rebooting the computer.

The problem is that every time this printer is turned on, a firmware package has to be uploaded to the printer from the computer it is attached to.  That is why, when the computer is working properly, there are two separate sounds when turning on the printer.  The first is the printer powering up, and the second is the printer ready to print after the firmware has been uploaded.  Using the official HP software that Ubuntu tries to get you to use, I either got a failed install or an install where the firmware wouldn't upload once the computer has been rebooted once.

The only way I ever got this printer to work properly is to use the foo2zjs drivers and instructions found here: [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

Even using the resources at the above website, I often had to reinstall after an Ubuntu upgrade.  And even when it was working, the packages provided by Ubuntu itself would often conflict with the packages that worked properly.

I finally got out of this whole mess by buying a router that had a print server built in.  Now the printer is attached to the router and the router uploads the firmware directly.  Works like a charm, and I finally didn't have to dread getting this printer to work again when I upgraded from 12.04 to 12.10.

---

### Post by dugong_bud on 2013-01-30
Hi, thanks for the link, sadly neither this worked for me.  I followed literarly the description.  

At this command: 
 ./getweb 1020	# Get HP LaserJet 1020 firmware file

I got back: DOnt know how to get ... whatever ... firmware (or sth like that)

Maybe that was ok.

Nevertheless the last command failed: 

   $ [system-config-printer]("http://foo2zjs.rkkda.com/fedora/")

It said it could not connect to the CUPS server (or sth similar)


thx anyway!

---

