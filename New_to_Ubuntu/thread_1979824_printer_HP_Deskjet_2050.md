---
title: "printer HP Deskjet 2050"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by jrev on 2012-05-14
Is the HP deskjet 2050 compatible with the ubuntu 10.04 lucid Lynx ?
Did you get it working ?
thank you for your answer

---

### Post by ajgreeny on 2012-05-14
It certainly should be, though you may need to install a more up-to-date version of hplip than Lucid has in the repos as the minimum version for the 2050 is 3.10.6., and Lucid only has 3.10.2.

See [http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2050_j510_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2050_j510_series.html) for all info and downloads of hplip direct from HP.

---

### Post by mystmaiden on 2012-05-19
I'm having a terrible time getting my new hp2050 to print as well. When I try to print, it gives a popup that says the printing has begun, and immediately after saying it is completed but it does not print anything.

One major problem is that it is showing my printer 6 times even though I have had it uninstall the previous install each time I've tried to get it going. I also tried  
```
sudo apt-get remove hplip --purge
``` but that didn't help either.

Here is the output for hp-check
```
mystmaiden@hal:~$ hp-check

HP Linux Imaging and Printing System (ver. 3.12.4)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-14 Hewlett-Packard Development Company, LP
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
Linux hal 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
OK, version 4.7.2 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.3
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

Checking for dependency: CUPS devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: CUPS image - CUPS image development files...
OK, found.

Checking for dependency: DBus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
OK, found.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.12.4 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.12.4

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.12.4
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.12.4
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory

Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = Deskjet_2050_J510
working_dir = .
device_uri = "hp:/usb/Deskjet_2050_J510_series?serial=CN22933HGZ05D1"

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[upgrade]
notify_upgrade = false
last_upgraded_time = 1337412813
latest_available_version = 3.12.4
pending_upgrade_time = 0

[installation]
version = 3.12.4
date_time = 05/19/2012 03:02:19

[settings]
systray_messages = 0
systray_visible = 0

[fax]
email_address = 
voice_phone = 

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
device_list = 
interval = 5



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model                      
  --------------------------------  ---------------------------
  hp:/usb/Deskjet_2050_J510_series  HP Deskjet 2050 J510 series
  ?serial=CN22933HGZ05D1                                       

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Deskjet_2050_J510
-----------------
Type: Printer
Device URI: hp:/usb/Deskjet_2050_J510_series?serial=CN22933HGZ05D1
PPD: /etc/cups/ppd/Deskjet_2050_J510.ppd
PPD Description: HP Business Inkjet 2250 PS - Ver 1.6 Postscript (recommended)
Printer status: printer Deskjet_2050_J510 is idle.  enabled since Sat 19 May 2012 02:53:ready to print
Communication status: Good

Deskjet_2050_J510_2
-------------------
Type: Printer
Device URI: hp:/usb/Deskjet_2050_J510_series?serial=CN22933HGZ05D1
PPD: /etc/cups/ppd/Deskjet_2050_J510_2.ppd
PPD Description: HP Deskjet 2050 j510 Series, hpcups 3.12.4
Printer status: printer Deskjet_2050_J510_2 is idle.  enabled since Sat 19 May 2012 02:26:53 AM CDT
Communication status: Good

Deskjet_2050_J510_3
-------------------
Type: Printer
Device URI: hp:/usb/Deskjet_2050_J510_series?serial=CN22933HGZ05D1
PPD: /etc/cups/ppd/Deskjet_2050_J510_3.ppd
PPD Description: HP Deskjet 2050 j510 Series, hpcups 3.12.4
Printer status: printer Deskjet_2050_J510_3 is idle.  enabled since Sat 19 May 2012 02:26:53 AM CDT
Communication status: Good

Deskjet_2050_J510_4
-------------------
Type: Printer
Device URI: hp:/usb/Deskjet_2050_J510_series?serial=CN22933HGZ05D1
PPD: /etc/cups/ppd/Deskjet_2050_J510_4.ppd
PPD Description: HP Deskjet 2050 j510 Series, hpcups 3.12.4
Printer status: printer Deskjet_2050_J510_4 is idle.  enabled since Sat 19 May 2012 02:26:53 AM CDT
Communication status: Good

Deskjet_2050_J510_5
-------------------
Type: Printer
Device URI: hp:/usb/Deskjet_2050_J510_series?serial=CN22933HGZ05D1
PPD: /etc/cups/ppd/Deskjet_2050_J510_5.ppd
PPD Description: HP Deskjet 2050 j510 Series, hpcups 3.12.4
Printer status: printer Deskjet_2050_J510_5 is idle.  enabled since Sat 19 May 2012 02:46:41 AM CDT
Communication status: Good

Deskjet_2050_J510_6
-------------------
Type: Printer
Device URI: hp:/usb/Deskjet_2050_J510_series?serial=CN22933HGZ05D1
PPD: /etc/cups/ppd/Deskjet_2050_J510_6.ppd
PPD Description: HP Business Inkjet 2250 PS - Ver 1.6 Postscript (recommended)
Printer status: printer Deskjet_2050_J510_6 is idle.  enabled since Sat 19 May 2012 02:52:21 AM CDT
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/Deskjet_2050_J510_series?serial=CN22933HGZ05D1' is a Hewlett-Packard Deskjet_2050_J510_series all-in-one


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

HP Device 0x8711 at 002:003: 
    Device URI: hp:/usb/Deskjet_2050_J510_series?serial=CN22933HGZ05D1
    Device node: /dev/bus/usb/002/003
    Mode: 0664

---------------
| USER GROUPS |
---------------

mystmaiden adm lp dialout fax cdrom floppy tape dip video plugdev fuse lpadmin netdev admin sambashare vboxusers


-----------
| SUMMARY |
-----------

No errors or warnings.

Done.
mystmaiden@hal:~$ 

```I'd love to have some help sorting this out, I was so looking forward to having a printer again.

thanks, 

mystmaiden

EDIT - I checked it on a windows machine, the printer does work there.

---

### Post by agillator on 2012-05-19
For mystmaiden - try removing each copy of the printer through cups; i.e. go to localhost:631 with your browser, open the printers tab and delete the printers from there.

For both: how are you installing/did you install HPLIP? For some reason I always have problems when using apt-get to install it. The best thing to do is to totally uninstall it (sudo apt-get purge hplip) and then obtain and install it from HP. Detailed instructions can be found here: [http://ubuntuforums.org/showthread.php?t=1898845](http://ubuntuforums.org/showthread.php?t=1898845), message #9. For most people that seems to work.

---

### Post by mystmaiden on 2012-05-19
Thanks for the reply. I installed using the hp website and the instructions there.
(except for the one time right after I tried purging it the first time, then I tried synaptic - it didn't work needless to say). 

I can not seem to find a localhost:631 file anywhere. I tried deleting the extra ppds from hplip using gksudo nautilus but it did not have any effect. Where is localhost:631 (I know I've seen that somewhere!). Also is there a way to search the root folders? 

Edited to add: Though I have hp at the top of my screen and on the drop down menu in applications, purging via your instructions tells me that hplip is not installed....very odd. I went back and reinstalled via your instructions in the link you provided. The only thing I did differently was instead of right clicking and making the file executable, I followed your instructions and used chmod. I was able to print after that.

thanks again,

mystmaiden

---

### Post by agillator on 2012-05-19
A browser address of 'localhost:631' should give you the CUPS page. Actually, 'localhost:631/printers' should give you the printers page. From there you select a printer and can delete it on the next screen. I think the HPLIP installation takes care of installing CUPS if it is not already installed. You might try the browser address again and see what happens.

I'm very glad things are now working for you. Some day HP is going to let me down and there is going to be some HP printer that isn't supported, but no one I know of has found it yet. I'm not sure the Ubuntu installation of HPLIP installs the HP Device Manager. Perhaps that is the difference and why so many people have problems. At any rate, letting HP do the installation always seems to work. Just for your information, I have an HP-970 (now too old to qualify as an antique?) that still works fine under HPLIP. That impresses me. Good luck.

---

