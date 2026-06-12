---
title: "HPLIP Devise Manager screen fails to appear"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Isaiah Lee on 2008-05-30
I'm using Ubuntu 8.04, after installing HPLIP 2.8.5 for my HP Laserjet P1006 printer, and after configuring the printer using HP-setup,  the HP system tray icon appears on my desktop, but when i click on the icon, nothing appears.  The printer is running ok.  
What is wrong, anyone can help to fix ?


here is the log file after running hp-check -t

hp-check[6129]: info: :
Initializing. Please wait...
Ubuntu

8.04

scheduler is running

1.3.7

Linux HumbleServant 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

hp-check[6129]: info: :
hp-check[6129]: info: :---------------
hp-check[6129]: info: :| SYSTEM INFO |
hp-check[6129]: info: :---------------
hp-check[6129]: info: :
hp-check[6129]: info: :Basic system information:
hp-check[6129]: info: :Linux HumbleServant 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

hp-check[6129]: info: :
hp-check[6129]: info: :Distribution:
hp-check[6129]: info: :ubuntu 8.04
hp-check[6129]: info: :
HPOJ running?
hp-check[6129]: info: :No, HPOJ is not running (OK).
hp-check[6129]: info: :
hp-check[6129]: info: :Checking Python version...
hp-check[6129]: info: :OK, version 2.5.2 installed
hp-check[6129]: info: :
hp-check[6129]: info: :Checking PyQt version...
hp-check[6129]: info: :OK, version 3.17 installed.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking SIP version...
error: SIP not installed or version not found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for CUPS...
hp-check[6129]: info: :Status: scheduler is running
hp-check[6129]: info: :Version: 1.3.7
hp-check[6129]: info: :error_log is set to level: warn
note: For troubleshooting printing issues, it is best to have the CUPS 'LogLevel'
note: set to 'debug'. To set the LogLevel to debug, edit the file /etc/cups/cupsd.conf (as root),
note: and change the line near the top of the file that begins with 'LogLevel' to read:
note: LogLevel debug
note: Save the file and then restart CUPS (see your OS/distro docs on how to restart CUPS).
note: Now, when you print, helpful debug information will be saved to the file:
note: /var/log/cups/error_log
note: You can monitor this file by running this command in a console/shell:
note: tail -f /var/log/cups/error_log
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dbus/python-dbus...
hp-check[6129]: info: :dbus daemon is running.
hp-check[6129]: info: :python-dbus version: 0.82.4
hp-check[6129]: info: :
hp-check[6129]: info: :
hp-check[6129]: info: :------------------------------------
hp-check[6129]: info: :| COMPILE AND RUNTIME DEPENDENCIES |
hp-check[6129]: info: :------------------------------------
hp-check[6129]: info: :
note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: cups - Common Unix Printing System...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: cups-ddk - CUPS driver development kit...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: cups-devel- Common Unix Printing System development files...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: dbus - Message bus system...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: gcc - GNU Project C and C++ Compiler...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: libcrypto - OpenSSL cryptographic library...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: libjpeg - JPEG library...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: libpthread - POSIX threads library...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: libtool - Library building support services...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: libusb - USB library...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: make - GNU make utility to maintain groups of programs...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: ppdev - Parallel port support kernel module....
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: PyQt - Qt interface for Python...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: python-ctypes - A foreign function library for Python...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: python-dbus - Python bindings for dbus...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: python-devel - Python development files...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: Python 2.3 or greater - Required for fax functionality...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: Python 2.2 or greater - Python programming language...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: Reportlab - PDF library for Python...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: SANE - Scanning library...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: SANE - Scanning library development files...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: scanimage - Shell scanning program...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for dependency: xsane - Graphical scanner frontend for SANE...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :
hp-check[6129]: info: :----------------------
hp-check[6129]: info: :| HPLIP INSTALLATION |
hp-check[6129]: info: :----------------------
hp-check[6129]: info: :
hp-check[6129]: info: :
hp-check[6129]: info: :Currently installed HPLIP version...
hp-check[6129]: info: :HPLIP 2.8.5 currently installed in '/usr/share/hplip'.
hp-check[6129]: info: :
hp-check[6129]: info: :Current contents of '/etc/hp/hplip.conf' file:
hp-check[6129]: info: :# hplip.conf. Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.8.5

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-2.8.5
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp/

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
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=yes
internal-tag=2.8.5.23

hp-check[6129]: info: :
hp-check[6129]: info: :--------------------------
hp-check[6129]: info: :| DISCOVERED USB DEVICES |
hp-check[6129]: info: :--------------------------
hp-check[6129]: info: :
hp-check[6129]: info: :
hp-check[6129]: info: :---------------------------------
hp-check[6129]: info: :| INSTALLED CUPS PRINTER QUEUES |
hp-check[6129]: info: :---------------------------------
hp-check[6129]: info: :
hp-check[6129]: info: :
hp-check[6129]: info: :640_Series
hp-check[6129]: info: :----------
hp-check[6129]: info: :Type: Unknown
hp-check[6129]: info: :Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
hp-check[6129]: info: :Device URI: usb://Lexmark%20/640%20Series
hp-check[6129]: info: :PPD: /etc/cups/ppd/640_Series.ppd
hp-check[6129]: info: :PPD Description: Generic text-only printer
hp-check[6129]: info: :Printer status: printer 640_Series is idle. enabled since Thu 29 May 2008 08:02:13 PM MYT

warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
hp-check[6129]: info: :Deskjet_D1300_series
hp-check[6129]: info: :--------------------
hp-check[6129]: info: :Type: Printer
hp-check[6129]: info: :Installed in HPLIP?: Yes, using the hp: CUPS backend.
hp-check[6129]: info: :Device URI: hp:/usb/Deskjet_D1300_series?serial=CN73T1J04304ND
hp-check[6129]: info: :PPD: /etc/cups/ppd/Deskjet_D1300_series.ppd
hp-check[6129]: info: :PPD Description: HP DeskJet D1300 Foomatic/hpijs, hpijs 2.8.2
hp-check[6129]: info: :Printer status: printer Deskjet_D1300_series is idle. enabled since Thu 29 May 2008 08:02:14 PM MYT

warning: Unable to connect to dbus. Is hp-systray running?
hp-check[6129]: info: :Communication status: Good
hp-check[6129]: info: :
hp-check[6129]: info: :HP_LaserJet_P1006
hp-check[6129]: info: :-----------------
hp-check[6129]: info: :Type: Printer
hp-check[6129]: info: :Installed in HPLIP?: Yes, using the hp: CUPS backend.
hp-check[6129]: info: :Device URI: hp:/usb/HP_LaserJet_P1006?serial=AB08LZP
hp-check[6129]: info: :PPD: /etc/cups/ppd/HP_LaserJet_P1006.ppd
hp-check[6129]: info: :PPD Description: HP LaserJet P1006 Foomatic/foo2xqx (recommended)
hp-check[6129]: info: :Printer status: printer HP_LaserJet_P1006 is idle. enabled since Fri 30 May 2008 06:33:29 PM MYT

warning: Unable to connect to dbus. Is hp-systray running?
hp-check[6129]: info: :Required plug-in status: Installed
hp-check[6129]: info: :Communication status: Good
hp-check[6129]: info: :
hp-check[6129]: info: :HP_LaserJet_P1006_1
hp-check[6129]: info: :-------------------
hp-check[6129]: info: :Type: Printer
hp-check[6129]: info: :Installed in HPLIP?: Yes, using the hp: CUPS backend.
hp-check[6129]: info: :Device URI: hp:/usb/HP_LaserJet_P1006?serial=AB08LZP
hp-check[6129]: info: :PPD: /etc/cups/ppd/HP_LaserJet_P1006_1.ppd
hp-check[6129]: info: :PPD Description: HP LaserJet P1006 Foomatic/hpijs-ZJS (recommended)
hp-check[6129]: info: :Printer status: printer HP_LaserJet_P1006_1 is idle. enabled since Fri 30 May 2008 06:34:48 PM MYT

warning: Unable to connect to dbus. Is hp-systray running?
hp-check[6129]: info: :Required plug-in status: Installed
hp-check[6129]: info: :Communication status: Good
hp-check[6129]: info: :
hp-check[6129]: info: :HP_LaserJet_P1006_2
hp-check[6129]: info: :-------------------
hp-check[6129]: info: :Type: Printer
hp-check[6129]: info: :Installed in HPLIP?: Yes, using the hp: CUPS backend.
hp-check[6129]: info: :Device URI: hp:/usb/HP_LaserJet_P1006?serial=AB08LZP
hp-check[6129]: info: :PPD: /etc/cups/ppd/HP_LaserJet_P1006_2.ppd
hp-check[6129]: info: :PPD Description: HP LaserJet P1006 Foomatic/hpijs-ZJS (recommended)
hp-check[6129]: info: :Printer status: printer HP_LaserJet_P1006_2 is idle. enabled since Fri 30 May 2008 06:58:21 PM MYT

warning: Unable to connect to dbus. Is hp-systray running?
hp-check[6129]: info: :Required plug-in status: Installed
hp-check[6129]: info: :Communication status: Good
hp-check[6129]: info: :
hp-check[6129]: info: :PDF
hp-check[6129]: info: :---
hp-check[6129]: info: :Type: Unknown
hp-check[6129]: info: :Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
hp-check[6129]: info: :Device URI: cups-pdf:/
hp-check[6129]: info: :PPD: /etc/cups/ppd/PDF.ppd
hp-check[6129]: info: :PPD Description: Generic PDF file generator
hp-check[6129]: info: :Printer status: printer PDF is idle. enabled since Wed 23 Apr 2008 01:54:42 AM MYT

warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
hp-check[6129]: info: :
hp-check[6129]: info: :----------------------
hp-check[6129]: info: :| SANE CONFIGURATION |
hp-check[6129]: info: :----------------------
hp-check[6129]: info: :
hp-check[6129]: info: :'hpaio' in '/etc/sane.d/dll.conf'...
hp-check[6129]: info: :OK, found. SANE backend 'hpaio' is properly set up.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking output of 'scanimage -L'...
hp-check[6129]: info: :

No scanners were identified. If you were expecting something different,

check that the scanner is plugged in, turned on and detected by the

sane-find-scanner tool (if appropriate). Please read the documentation

which came with this software (README, FAQ, manpages).

hp-check[6129]: info: :
hp-check[6129]: info: :---------------------
hp-check[6129]: info: :| PYTHON EXTENSIONS |
hp-check[6129]: info: :---------------------
hp-check[6129]: info: :
hp-check[6129]: info: :Checking 'cupsext' CUPS extension...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking 'pcardext' Photocard extension...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking 'hpmudext' I/O extension...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :Checking 'scanext' SANE scanning extension...
hp-check[6129]: info: :OK, found.
hp-check[6129]: info: :
hp-check[6129]: info: :
hp-check[6129]: info: :-----------------
hp-check[6129]: info: :| USB I/O SETUP |
hp-check[6129]: info: :-----------------
hp-check[6129]: info: :
hp-check[6129]: info: :
hp-check[6129]: info: :Checking for permissions of USB attached printers...
hp-check[6129]: info: :
HP Device 0x7804 at 006:002:
hp-check[6129]: info: : Device URI: hp:/usb/Deskjet_D1300_series?serial=CN73T1J04304ND
hp-check[6129]: info: : Device node: /dev/bus/usb/006/002
hp-check[6129]: info: : Mode: 0666
hp-check[6129]: info: :getfacl: Removing leading '/' from absolute path names

# file: dev/bus/usb/006/002

# owner: root

# group: lp

user::rw-

user:isaiah:rw-

group::rw-

mask::rw-

other::rw-

hp-check[6129]: info: :
HP Device 0x3e17 at 003:003:
hp-check[6129]: info: : Device URI: hp:/usb/HP_LaserJet_P1006?serial=AB08LZP
hp-check[6129]: info: : Device node: /dev/bus/usb/003/003
hp-check[6129]: info: : Mode: 0666
hp-check[6129]: info: :getfacl: Removing leading '/' from absolute path names

# file: dev/bus/usb/003/003

# owner: root

# group: lp

user::rw-

user:isaiah:rw-

group::rw-

mask::rw-

other::rw-

hp-check[6129]: info: :
hp-check[6129]: info: :-----------
hp-check[6129]: info: :| SUMMARY |
hp-check[6129]: info: :-----------
hp-check[6129]: info: :
error: 3 errors and/or warnings.
hp-check[6129]: info: :
hp-check[6129]: info: :Please refer to the installation instructions at:
hp-check[6129]: info: :[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

hp-check[6129]: info: :
hp-check[6129]: info: :Done.

---

### Post by alienexplorers on 2008-06-03
Do you have the following programs loaded:
> HPLIP
HPIJS
HPLIP-DATA
HPLIP-GUI

---

### Post by tantares on 2008-09-30
I have a similar problem. After downloading and installing HPLIP 2.8.9 the HP Toolbox Panel Icon does not appear on my panel and the HP Device Manager does not run.

Now the interresting part is, that for all other users on the same machine with less rights everything works!

Any help?

---

### Post by tantares on 2008-10-01
Found the solution in another thread: [https://answers.launchpad.net/hplip/+question/38346](https://answers.launchpad.net/hplip/+question/38346)

Thanks:)

---

