---
title: "Make cups run and the printer print"
date: 2017-04-17
forum: New to Ubuntu
---

### Post by namedesnutzers on 2017-04-17
Hello dear community,

recently i've set up my first linux system. System spec:

Acer Revo M1-601 Mini Pc
Ubuntu 16.04
HP Laser Jet M1005 MFP plugged via USB

Everything was fine for a couple days - until it came to printing. The simple problem was that the printer was recognized but did not print. So i went to google and began to try out all suggestions i found. I installed hplip, deleted the printer from system-printers and reinstalled it via cups as wells as via hp-setup and from the system-printer gui. To make it short: i did a damn lot of "sudo whatever i find on google". 

The best result was by changing the driver from foomatic to hpcups in system-printer gui. Doing so i could print short LibreOffice Writer documents (about a page long and only text - no pictures). But everything longer than a page or sometimes even only a half page still didnt work. So i kept on googling and found a thread that recommends to purge cups, delete everything from the /etc/cups folder and reinstall cups. So what i did was something like:

```
 sudo apt-get purge cups
cd /etc/cups
sudo rm * 
sudo apt-get install cups
 
```

Well ... here the things got worse. Although the re-installation of cups ran without failures i cannot use cups anymore. When i enter localhost:631 i see the starting page but nothing else works - no admin, no help, no jobs, etc. Trying to access one of this sections i get a "failed to connect" error. Im also no longer able to detect my printer. Whenever i go to system-printer interface it wants to connect to cups server (under /var/run/cups/cups.sock ) but the connection fails.

Now i kindly ask you for help :)

1. Please help me to resurrect cups
2. Please help me to get my printer printing again

Thanks in advance!

---

### Post by Autodave on 2017-04-17
What did you do to install printer before you tried to print for the very first time? Anything?

---

### Post by namedesnutzers on 2017-04-17
Its a couple days since then so maybe im wrong but as far as i can remember i did nothing. I hit the print icon in the LibreOffice Writer and my printer was listed in the print menu.

---

### Post by Autodave on 2017-04-17
Did the printer icon have a check-mark indicating that it was the default printer?

I have never had to do anything special to get an HP printer to work other than making sure it is turned on, plug the USB cable in, wait for Linux to recognize it, and then choose it as the default printer.

I am thinking that you may never have actually chosen (told Linux to use it) it to be the default printer.

You may try going to the printer section in settings and removing anything there. Then, with printer powered up, connect the cable and go from there: chose it as default when prompted.

---

### Post by Bucky Ball on 2017-04-17
Welcome. You are probably going to need to do more than nothing. ;) Make sure you have HPLip installed to start with. You can install from the repo [or here]("http://hplipopensource.com/hplip-web/install_wizard/index.html"). Installing it from the official repositories in Ubuntu Software should work fine.

Once that's done, you will need to go to Printers> Add Printer and add the HP printer. Print a test page to make sure it works and when it does, right click and set it as the default printer.

(You can add the printer via CUPS, yes, but do you know much about it? May be easiest to use the 'Printer' GUI. Either way, you are going to need to get HPLip into action and a driver installed first.)

---

### Post by namedesnutzers on 2017-04-18
> **Autodave said:**
> Did the printer icon have a check-mark indicating that it was the default printer?

I have never had to do anything special to get an HP printer to work other than making sure it is turned on, plug the USB cable in, wait for Linux to recognize it, and then choose it as the default printer.

I am thinking that you may never have actually chosen (told Linux to use it) it to be the default printer.

You may try going to the printer section in settings and removing anything there. Then, with printer powered up, connect the cable and go from there: chose it as default when prompted.

AFAIK it had the green tick that i interpret as the default  printer. But again, its several days ago so i might be wrong. Currently i cant remove anything from the printer section because whenever i click it, it wants to connect to cups but fails.

> **Bucky Ball said:**
> Welcome. You are probably going to need to do more than nothing. ;) Make sure you have HPLip installed to start with. You can install from the repo [or here]("http://hplipopensource.com/hplip-web/install_wizard/index.html"). Installing it from the official repositories in Ubuntu Software should work fine.

Once that's done, you will need to go to Printers> Add Printer and add the HP printer. Print a test page to make sure it works and when it does, right click and set it as the default printer.

(You can add the printer via CUPS, yes, but do you know much about it? May be easiest to use the 'Printer' GUI. Either way, you are going to need to get HPLip into action and a driver installed first.)

Ok, now ive done the following:

```

sudo apt-get install hplip  
hp-check >> hplip.txt

```

here is what hp-check got to say:

```


[01mSaving output in log file: /home/adler/hp-check.log[0m

[01mHP Linux Imaging and Printing System (ver. 3.16.11)[0m
[01mDependency/Version Check Utility ver. 15.1[0m

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

[01mNote: hp-check can be run in three modes:[0m
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Check types:                                                                    
a. EXTERNALDEP - External Dependencies                                          
b. GENERALDEP - General Dependencies (required both at compile and run time)    
c. COMPILEDEP - Compile time Dependencies                                       
d. [All are run-time checks]                                                    
PYEXT SCANCONF QUEUES PERMISSION                                                

Status Types:
    OK
    MISSING       - Missing Dependency or Permission or Plug-in
    INCOMPAT      - Incompatible dependency-version or Plugin-version


---------------
| SYSTEM INFO |
---------------

 Kernel: 4.8.0-46-generic #49~16.04.1-Ubuntu SMP Fri Mar 31 14:51:03 UTC 2017 GNU/Linux 
 Host: adler-Revo-M1-601 
 Proc: 4.8.0-46-generic #49~16.04.1-Ubuntu SMP Fri Mar 31 14:51:03 UTC 2017 GNU/Linux 
 Distribution: ubuntu 16.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.16.11
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  16.04 version 

[01mCurrent contents of '/etc/hp/hplip.conf' file:[0m
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.16.11

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip-3.16.11
html=/usr/share/doc/hplip-3.16.11
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp
bin=/usr/bin
apparmor=/etc/apparmor.d
# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
libusb01-build=no
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
internal-tag=3.16.11
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
qt5=no
policy-kit=no
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
apparmor_build=no


[01mCurrent contents of '/var/lib/hp/hplip.state' file:[0m
[plugin]
installed = 1
eula = 1
version = 3.16.11



[01mCurrent contents of '~/.hplip/hplip.conf' file:[0m
[upgrade]
notify_upgrade = true
last_upgraded_time = 1492104683
pending_upgrade_time = 0
latest_available_version = 3.16.11

[last_used]
device_uri = hp:/usb/HP_LaserJet_M1005?serial=KJ1D3Q2

[installation]
date_time = 04/18/17 18:31:39
version = 3.16.11


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------------------
|  External Dependencies |
--------------------------

[31;01m error: cups          CUPS - Common Unix Printing System                           REQUIRED        1.1             2.1.3           MISSING    'CUPS may not be installed or not running'[0m
 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.18            OK         -
 network              network -wget                                                OPTIONAL        -               1.17.1          OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.6.32          OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.25          OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.10.6          OK         -

-------------------------
|  General Dependencies |
-------------------------

 libpthread           libpthread - POSIX threads library                           REQUIRED        -               b'2.23'         OK         -
 python3-pyqt4        PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.11.4          OK         -
 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.0.2           OK         -
 python3-devel        Python devel - Python development files                      REQUIRED        2.2             3.5.2           OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               1.0.25          OK         -
 python3-reportlab    Reportlab - PDF library for Python                           OPTIONAL        2.0             3.3.0           OK         -
 python3-notify2      Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.3           OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 python3X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             3.5.2           OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               2.1.3           OK         -
 python3-pil          PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               1.0.25          OK         -
 python3-pyqt4-dbus   PyQt 4 DBus - DBus Support for PyQt4                         OPTIONAL        4.0             4.11.4          OK         -
 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 python3-xml          Python XML libraries                                         REQUIRED        -               2.1.0           OK         -
 python3-dbus         Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.0           OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               2.1.3           OK         -

---------------
|  COMPILEDEP |
---------------

 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               5.4.0           OK         -
 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.1             OK         -

----------------------
|  Python Extentions |
----------------------

 hpmudext             IO-Extension                                                 REQUIRED        -               3.16.11         OK         -
 cupsext              CUPS-Extension                                               REQUIRED        -               3.16.11         OK         -

-----------------------
|  Scan Configuration |
-----------------------

 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.16.11         OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.16.11         OK         -

-----------------------
|  Other Dependencies |
-----------------------


------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

device `hpaio:/usb/HP_LaserJet_M1005?serial=KJ1D3Q2' is a Hewlett-Packard HP_LaserJet_M1005 all-in-one 
device `hpljm1005:libusb:001:004' is a Hewlett-Packard LaserJet M1005 multi-function peripheral 


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model            
  --------------------------------  -----------------
  hp:/usb/HP_LaserJet_M1005?serial  HP LaserJet M1005
  =KJ1D3Q2                                           

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


[01mlpstat[0m
[01m------[0m
Type: Unknown
Device URI: Ungültiger Dateideskriptor


--------------
| PERMISSION |
--------------

USB             None                           Required        -        -        OK       Node:'/dev/bus/usb/001/004' Perm:'  root  lp rw- rw- rw- rw- rw- r--'

-----------
| SUMMARY |
-----------

[01mMissing Required Dependencies[0m
[01m-----------------------------[0m

[01mMissing Optional Dependencies[0m
[01m-----------------------------[0m
None


Total Errors: 1
Total Warnings: 0


Done.


```


The good thing is that my printer is recognized. The bad thing is the error about cups:

```


1;01m error: cups          CUPS - Common Unix Printing System                           REQUIRED        1.1             2.1.3           MISSING    'CUPS may not be installed or not running'


```

Also in the console, after the hp-check >> hplip.txt command is executed , there is the following error message:

```

error: 'libcups2' package is missing/incompatible 

```


If i do a 

```

hp-setup

```

The printer is recognized but in the console i see another error:

```


Searching... (bus=usb, search=(None), desc=0)
error: No PPD found for model laserjet_m1005 using old algorithm.
error: No appropriate print PPD file found for model hp_laserjet_m1005

Done.

```

I gues with the "rm *" in the "/etc/cups" folder ive grilled cups seriously.

---

### Post by namedesnutzers on 2017-04-20
does soebody have an advice for me?

---

