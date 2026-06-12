---
title: "cups server errors"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by tavidu on 2013-06-26
I am getting this error message when trying to connect a printer: [COLOR=#ff0000]There was an error during CUPS operation: "failed to connect to server"[/COLOR],  so I tried re-installing CUPS. This is what I have got. I could install and print before. Today I had to print something and all of the suddend there was this error.:confused: Thank you for helping.

sudo apt-get install cups
[sudo] password for tavituva: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cups is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cups (1.5.3-0ubuntu8) ...
start: Job failed to start
invoke-rc.d: initscript cups, action "start" failed.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of printer-driver-hpcups:
 printer-driver-hpcups depends on cups; however:
  Package cups is not configured yet.
dpkg: error processing printer-driver-hpcups (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of hplip:
 hplip depends on printer-driver-hpcups (= 3.12.2-1ubuntu3.1); however:
  Package printer-driver-hpcups is not configured yet.
 hplip depends on cups (>= 1.1.20); however:
  Package cups is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:No apport report written because the error message indicates its a followup error from a previous failure.

 printer-driver-postscript-hp depends on hplip (>= 3.12.2-1ubuntu3.1); however:
  Package hplip is not configured yet.
dpkg: error processing printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-pdf:No apport report written because MaxReports is reached already

 cups-pdf depends on cups; however:
  Package cups is not configured yet.
dpkg: error processing cups-pdf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip-gui:No apport report written because MaxReports is reached already

 hplip-gui depends on hplip (>= 3.12.2-1ubuntu3.1); however:
  Package hplip is not configured yet.
dpkg: error processing hplip-gui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-gutenprint:No apport report written because MaxReports is reached already

 printer-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.
dpkg: error processing printer-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 cups
 printer-driver-hpcups
 hplip
 printer-driver-postscript-hp
 cups-pdf
 hplip-gui
 printer-driver-gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dino99 on 2013-06-26
****7 not fully installed or removed. *****

that it; have you set some ppa(s) which could conflict ?
open synaptic to know about the broken packages, and try to fix them

---

### Post by doctorbighands on 2013-06-26
```
sudo dpkg --configure -a
```
or
```
sudo apt-get -f install
```
might do the trick. They often solve problems like this for me.

---

### Post by tavidu on 2013-06-27
I tried that no broken packages.


> **dino99 said:**
> ****7 not fully installed or removed. *****

that it; have you set some ppa(s) which could conflict ?
open synaptic to know about the broken packages, and try to fix them

---

### Post by tavidu on 2013-06-27
Did not work this time. I ahve no idea what other process could be. Could you point me in the right direction?

tavituva@tavituva-MM061:~$ sudo dpkg --configure -a
[sudo] password for tavituva: 
dpkg: error: dpkg status database is locked by another process
tavituva@tavituva-MM061:~$ sudo apt-get -f install
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by tavidu on 2013-06-29
I upgraded from 12.04 to 12.10, and indeed were a few broken packages of which the installer took care. Now printers and CUPS are working fine

---

