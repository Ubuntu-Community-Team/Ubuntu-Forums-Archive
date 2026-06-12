---
title: "Printer may not be connected"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by bobheaps on 2008-10-05
I am still having problems with my hp 1315 printer.I have used system>admin>printing to set it up (several times now) it still will not print a test page. I have followed all the info I have gleaned from previous posts on sililar problems but no luck. HPLIP says it is there but it won't work. I have rebooted to windows xp and the printer works perfectly. I have connected the printer to my laptop and it works perfectly. I run 8.04 on both machines. A printer is the gateway to the outside world and I am stymied. God forbid i have to go back to windows, Ubuntu works so well otherwise.
Are there any further tests I can perform?
Is it a lot of trouble to re-install Ubuntu keeping all the programs already installed?
Please help

---

### Post by kansasnoob on 2008-10-05
I found this:

[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

It looks like that may require hpoj and some additional setup.

---

### Post by bobheaps on 2008-10-05
Thanks
I followed your instructions and got the following output (sorry its so long but i didn't want to cut any out)
What can I do now?
Thanks in advance
bobheaps@bobheaps-desktop:~$ sudo hp-check -r
sudo: unable to resolve host bobheaps-desktop

HP Linux Imaging and Printing System (ver. 2.8.2)
Dependency/Version Check Utility ver. 13.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
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
warning: Invalid ppd_dir value: /usr/share/ppd/hpijs/HP
warning: Invalid drv_dir value: /usr/share/cups/drv/hp/

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux bobheaps-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Distribution:
ubuntu 8.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: scheduler is running
Version: 1.3.7


------------------------
| RUNTIME DEPENDENCIES |
------------------------


Checking for dependency: cups - Common Unix Printing System...
OK, found.

Checking for dependency: cups-ddk - CUPS driver development kit...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt - Qt interface for Python...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 2.8.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.8.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
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
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
internal-tag=2.8.2.10


-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                                   Model                   
  -------------------------------------------  ------------------------
  hp:/usb/psc_1310_series?serial=MY4ADCC473O2  HP psc 1310 series      

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
PDF
---
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: cups-pdf:/
PPD: /etc/cups/ppd/PDF.ppd
PPD Description: Generic PDF file generator
Printer status: printer PDF is idle.  enabled since Sun 05 Oct 2008 06:06:39 PM EDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
psc_1310
--------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/psc_1310_series?serial=MY4ADCC473O2
PPD: /etc/cups/ppd/psc_1310.ppd
PPD Description: HP Mopier 320 Postscript (recommended)
Printer status: printer psc_1310 is idle.  enabled since Sun 05 Oct 2008 09:37:38 PM EDT
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
error: Not found. SANE backend 'hpaio' NOT properly setup (needs to be added to /etc/sane.d/dll.conf).

Checking output of 'scanimage -L'...
device `v4l:/dev/video0' is a Noname Generic Vimicro 303b virtual device
device `hpaio:/usb/psc_1310_series?serial=MY4ADCC473O2' is a Hewlett-Packard psc_1310_series all-in-one


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
 
HP Device 0x3f11 at 003:002: 
    Device URI: hp:/usb/psc_1310_series?serial=MY4ADCC473O2
    Device node: /dev/bus/usb/003/002
    Mode: 0660
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/003/002
# owner: lp
# group: scanner
user::rw-
user:bobheaps:rw-
group::rw-
mask::rw-
other::---



-----------
| SUMMARY |
-----------

error: 3 errors and/or warnings.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

bobheaps@bobheaps-desktop:~$

---

### Post by kansasnoob on 2008-10-05
> HPOJ running?
No, HPOJ is not running (OK).

Did you install hpoj?

```
sudo apt-get install hpoj
```

And as I look at dependencies lets also install hpijs:

```
sudo apt-get install hpijs
```

Then try again:(

Restart the desktop by pressing Ctrl - Alt - Backspace, and be sure to clear all previous installs.

---

### Post by bobheaps on 2008-10-06
:KS
Everything is now working fine - thanks for all your help, you guys are wonderful.

---

### Post by EAA webmaster on 2008-10-30
Hi there:
I have problems too.
I have passed the whole afternoon trying to fix it but I can't, I'm not good enough.

In my little company, we migrate from windows to ubuntu. We needed a pinter with fax, scanner and wireless. We have bought the HP officejet J6400. I installed the HPLIP. HPlip run but the printer is still without working. The problem is the 'cups-missing-filter' because of the "foomatic-rip-hplip".

I ran "sudo hp-check -r" and these are the problems that I can't fix.

Initializing. Please wait...
warning: Invalid drv_dir value: /usr/share/cups/drv/hp/

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux alf-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

Distribution:
ubuntu 8.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
[COLOR="Red"]error: SIP not installed or version not found.[/COLOR]

Checking for CUPS...
Status: scheduler is running
[COLOR="Red"]error: Version: (Not available. CUPS may not be installed or not running.)[/COLOR]


------------------------
| RUNTIME DEPENDENCIES |
------------------------


Checking for dependency: cups - Common Unix Printing System...
OK, found.

Checking for dependency: cups-ddk - CUPS driver development kit...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt - Qt interface for Python...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 2.8.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.8.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
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
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
internal-tag=2.8.2.10


-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Officejet_J6400
---------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/net/Officejet_J6400_series?ip=192.168.0.114
PPD: /etc/cups/ppd/Officejet_J6400.ppd
[COLOR="Red"]PPD Description: HP OfficeJet J6400 Foomatic/hpijs, hpijs 2.8.4.2
Printer Filter "foomatic-rip-hplip" for printer "Officejet_J6400" not available: No such file or directory
error: Unsupported model: Officejet_J6400_series[/COLOR]

PDF
---
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: cups-pdf:/
PPD: /etc/cups/ppd/PDF.ppd
PPD Description: Generic PDF file generator
Printer status: printer PDF is idle.  enabled since Wed 23 Apr 2008 04:12:00 EST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
[COLOR="Red"]error: Not found. SANE backend 'hpaio' NOT properly setup (needs to be added to /etc/sane.d/dll.conf).[/COLOR]

Checking output of 'scanimage -L'...
device `v4l:/dev/video0' is a Noname USB2.0 1.3M UVC WebCam  virtual device


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
 
-----------
| SUMMARY |
-----------

[COLOR="Red"]error: 5 errors and/or warnings.[/COLOR]

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


I tryed to go to [http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html) but today is not workng at all (Murphis laws). I tryed to look for this problem and I found some post. This one almost helped ([http://www.kero.valesti.net/index.php?q=aHR0cHM6Ly9hbnN3ZXJzLmVkZ2UubGF1bmNocGFkLm5ldC9ocGxpcC8rcXVlc3Rpb24vNDU0NDE%3D&hl=3ed](http://www.kero.valesti.net/index.php?q=aHR0cHM6Ly9hbnN3ZXJzLmVkZ2UubGF1bmNocGFkLm5ldC9ocGxpcC8rcXVlc3Rpb24vNDU0NDE%3D&hl=3ed)) me but my knowledge about Linux sill sucks. I'll try fix that too but I need more time.

I'll really appreciate any help

---

