---
title: "lucid and p1102w printer"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by DarinB on 2011-12-19
I have an hp p1102w printer, it is not listed in the printer drivers 
i am using the p1022nw driver it prints everything except pdf's I get a full black page each time. 
any help on this is it the driver. I have tried to add foomatic something but i still can't get pdfs to print.

---

### Post by DarinB on 2011-12-20
Now my printer won't work at all I added the upgrade to cups. and foomatic.  can anyone help me figure this out. 
these are the errors i am getting. I tried adding the foomatic and cups upgrade but it make it worse. what should I do????
[ATTACH]209458[/ATTACH]

[ATTACH]209459[/ATTACH]

[ATTACH]209460[/ATTACH]

---

### Post by LowSky on 2011-12-20
Do you have HPLIP installed?

there is also a glitch to HPLIP software that it needs python 2 to run in some cases. I can't speak for Ubuntu anymore directly, but most newer systems use python 3. changing the symlink to point to python 2 should fix the error.

---

### Post by DarinB on 2011-12-21
how do i do that?

---

### Post by DarinB on 2011-12-21
does this info help?

darin@darin-desktop ~ $ sudo hp-check
[sudo] password for darin: 

HP Linux Imaging and Printing System (ver. 3.11.5)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux darin-desktop 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux

Distribution:
linuxmint 9

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
error: NOT FOUND OR FAILED TO LOAD!

Checking for CUPS...
Status: scheduler is running
warning: Version: (cups-config) Not available. Unable to determine installed version of CUPS.)
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: CUPS image - CUPS image development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: DBus - Message bus system...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: libjpeg - JPEG library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: libusb - USB library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
error: NOT FOUND! This is a REQUIRED/RUNTIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.11.5 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.11.5

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip-doc/HTML
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=yes
foomatic-drv-install=yes
foomatic-ppd-install=yes
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.11.5
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[installation]
date_time = 12/19/2011 14:28:56
version = 3.11.12



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model                    
  --------------------------------  -------------------------
  hp:/usb/Photosmart_2570_series?s  HP Photosmart 2570 series
  erial=MY5AE2216S04B8                                       
  hp:/usb/Deskjet_6940_series?seri  HP Deskjet 6940 series   
  al=MY92DCK5XY04Q9                                          

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Deskjet-6940-series
-------------------
Type: Printer
Device URI: hp:/usb/Deskjet_6940_series?serial=MY92DCK5XY04Q9
PPD: /etc/cups/ppd/Deskjet-6940-series.ppd
PPD Description: HP Deskjet 6940 Series, hpcups 3.11.5
Printer status: printer Deskjet-6940-series is idle.  enabled since Tue 20 Dec 2011 08:33:47 PM EST
Communication status: Good

Hewlett-Packard-HP-LaserJet-Professional-P1102w
-----------------------------------------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000Q91PX2DPR1a
PPD: /etc/cups/ppd/Hewlett-Packard-HP-LaserJet-Professional-P1102w.ppd
PPD Description: HP LaserJet 1022n Foomatic/foo2zjs (recommended)
Printer status: printer Hewlett-Packard-HP-LaserJet-Professional-P1102w is idle.  enabled since Wed 21 Dec 2011 05:57:58 AM EST
error: Required plug-in status: Not installed
error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000Q91PX2DPR1a
error: Device not found
error: Communication status: Failed

HP-Photosmart-2570-series
-------------------------
Type: Printer
Device URI: hp:/usb/Photosmart_2570_series?serial=MY5AE2216S04B8
PPD: /etc/cups/ppd/HP-Photosmart-2570-series.ppd
PPD Description: HP Photosmart 2570 Series, hpcups 3.11.5
Printer status: printer HP-Photosmart-2570-series is idle.  enabled since Sat 19 Nov 2011 08:07:15 AM EST
Communication status: Good

Photosmart-2570-series
----------------------
Type: Printer
Device URI: hp:/usb/Photosmart_2570_series?serial=MY5AE2216S04B8
PPD: /etc/cups/ppd/Photosmart-2570-series.ppd
PPD Description: HP Photosmart 2570 Series, hpcups 3.11.5
Printer status: printer Photosmart-2570-series disabled since Mon 05 Dec 2011 09:41:15 A/usr/lib/cups/backend/hp failed
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/Photosmart_2570_series?serial=MY5AE2216S04B8' is a Hewlett-Packard Photosmart_2570_series all-in-one


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


 
-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0x8904 at 001:006: 
    Device URI: hp:/usb/Deskjet_6940_series?serial=MY92DCK5XY04Q9
    Device node: /dev/bus/usb/001/006
    Mode: 0664

HP Device 0x4e11 at 001:005: 
    Device URI: hp:/usb/Photosmart_2570_series?serial=MY5AE2216S04B8
    Device node: /dev/bus/usb/001/005
    Mode: 0664

HP Device 0x32a at 001:003: 
    Device URI: hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000Q91PX2DSI1c
    Device node: /dev/bus/usb/001/003
    Mode: 0664

---------------
| USER GROUPS |
---------------

root

error: User needs to be member of group 'lp' to enable print, scan & fax.
error: User needs to be member of group 'lpadmin' to manage printers.

-----------
| SUMMARY |
-----------

error: 16 errors and/or warnings.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
darin@darin-desktop ~ $

---

### Post by DarinB on 2011-12-21
I tried installing hplip 3.11.12
now I get this error. [ATTACH]209499[/ATTACH]

---

### Post by DarinB on 2011-12-21
solved using this website and tarball download 
[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

there is a bug the requires the ./configure to include some lines 

now everything works again but still get a solid black page when printing pdfs 

This is a problem with all printers that need foomatic to run.

---

