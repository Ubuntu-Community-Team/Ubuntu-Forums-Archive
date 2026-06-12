---
title: "HP-Deskjet-3520-series' Printer is either Powered-OFF or Failed to communicate"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by atharvasehgal on 2014-06-30
I've been using Ubuntu for 2 Years now (and am still a noob)... Recently I have been having problems with my printer not being able to print (hplip 3.14.6) an documents.


The ```
sudo usermod -a -G lp <usr name> 
``` command provides temporary relief but requires me to restart my computer every time I need to print.

Here's a ```
hp-doctor
``` report and a ```
hp-check
``` report



```
$ hp-checkSaving output in log file: /home/atharva/hp-check.log


HP Linux Imaging and Printing System (ver. 3.14.6)
Dependency/Version Check Utility ver. 15.1


Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
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


 Kernel: 3.11.0-23-generic #40-Ubuntu SMP Wed Jun 4 21:05:24 UTC 2014 GNU/Linux
 Host: atharva-desktop
 Proc: 3.11.0-23-generic #40-Ubuntu SMP Wed Jun 4 21:05:24 UTC 2014 GNU/Linux
 Distribution: ubuntu 13.10
 Bitness: 32 bit




-----------------------
| HPLIP CONFIGURATION |
-----------------------


HPLIP-Version: HPLIP 3.14.6
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  13.10 version 


Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.


[hplip]
version=3.14.6


[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.14.6
html=/usr/share/doc/hplip-3.14.6
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp
bin=/usr/bin


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
internal-tag=3.14.6
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no




Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory


Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1403765050
pending_upgrade_time = 0
latest_available_version = 3.14.6


[settings]
systray_visible = 0
systray_messages = 0


[last_used]
device_uri = "hp:/usb/Deskjet_3520_series?serial=CN34G1C5G005T0"
printer_name = 
working_dir = .


[commands]
scan = /usr/bin/xsane -V %SANE_URI%


[refresh]
rate = 30
enable = false
type = 1


[polling]
enable = false
interval = 5
device_list = 


[fax]
voice_phone = 
email_address = 


[installation]
date_time = 07/01/2014 00:04:36
version = 3.14.6




 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>


--------------------------
|  External Dependencies |
--------------------------


 policykit            Admin-Policy-framework    OPTIONAL        -               0.105           OK         -
 gs                   Ghostscript               REQUIRED        7.05            9.10            OK         -
 network              Network-wget              OPTIONAL        -               1.14            OK         -
 scanimage            Shell-Scanning            OPTIONAL        1.0             1.0.23          OK         -
 avahi-utils          avahi-utils               OPTIONAL        -               0.6.31          OK         -
 dbus                 DBus                      REQUIRED        -               1.6.12          OK         -
 cups                 CUPS                      REQUIRED        1.1             1.7             OK         'CUPS Scheduler is running'
 xsane                SANE-GUI                  OPTIONAL        0.9             0.998           OK         -


-------------------------
|  General Dependencies |
-------------------------


 reportlab            Python-PDF-Lib            OPTIONAL        2.0             2.6             OK         -
 libcrypto            OpenSSL-Crypto-Lib        REQUIRED        -               1.0.1           OK         -
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.10.3          OK         -
 libjpeg              JPEG-Lib                  REQUIRED        -               -               OK         -
 libpthread           POSIX-Threads-Lib         REQUIRED        -               2.17            OK         -
 python-dbus          Python-DBUS               REQUIRED        0.80.0          1.2.0           OK         -
 python-devel         Python-SDK                REQUIRED        2.2             2.7.5           OK         -
 pyqt4                Python-Qt4                REQUIRED        4.0             4.10.3          OK         -
 cups-devel           CUPS-SDK                  REQUIRED        -               1.7             OK         -
 sane-devel           SANE-SDK                  REQUIRED        -               1.0.23          OK         -
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
 sane                 Scan-Lib                  REQUIRED        -               1.0.23          OK         -
 cups-image           CUPS-Image-Lib            REQUIRED        -               1.7             OK         -
 libnetsnmp-devel     SNMP-Networking-SDK       REQUIRED        5.0.9           5.7.2           OK         -
 python-xml           Python-XML-Lib            REQUIRED        -               2.1.0           OK         -
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -


------------------------------
|  Compile Time Dependencies |
------------------------------


 gcc                  gcc-Compiler              REQUIRED        -               4.8.1           OK         -
 libtool              Build-tools               REQUIRED        -               2.4.2           OK         -
 make                 GNU-Build-tools           REQUIRED        3.0             3.81            OK         -


----------------------
|  Python Extentions |
----------------------


 cupsext              CUPS-Extension            REQUIRED        -               3.14.6          OK         -
 pcardext             PhotoCard-Extension       REQUIRED        -               3.14.6          OK         -
 hpmudext             IO-Extension              REQUIRED        -               3.14.6          OK         -


-----------------------
|  Scan Configuration |
-----------------------


 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.14.6          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension       REQUIRED        -               3.14.6          OK         -


------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------


device `hpaio:/usb/Deskjet_3520_series?serial=CN34G1C5G005T0' is a Hewlett-Packard Deskjet_3520_series all-in-one




--------------------------
| DISCOVERED USB DEVICES |
--------------------------


  Device URI                        Model                 
  --------------------------------  ----------------------
  hp:/usb/Deskjet_3520_series?seri  HP Deskjet 3520 series
  al=CN34G1C5G005T0                                       


---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


 
HP-Deskjet-3520-series
----------------------
Type: Printer
Device URI: hp:/usb/Deskjet_3520_series?serial=CN34G1C5G005T0
PPD: /etc/cups/ppd/HP-Deskjet-3520-series.ppd
PPD Description: HP Deskjet 3520 Series, hpcups 3.14.6
Printer status: printer HP-Deskjet-3520-series is idle.  enabled since Mon 30 Jun 2014 1Processing page 1...
error: Device busy: hp:/usb/Deskjet_3520_series?serial=CN34G1C5G005T0
error: Device not found
error: Communication status: Failed




--------------
| PERMISSION |
--------------


USB             HP-Deskjet-3520-series         Required        -        -        OK       Node:'/dev/bus/usb/001/005' Perm:'  root  lp rw- rw- rw- rw- r--'
 
-----------
| SUMMARY |
-----------


Missing Required Dependencies
-----------------------------
None


Missing Optional Dependencies
-----------------------------
None




Total Errors: 1
Total Warnings: 0




Done.


[/QUOTE]

[QUOTE]hpijs-install=nofoomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.14.6
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no




Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory


Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1403765050
pending_upgrade_time = 0
latest_available_version = 3.14.6


[settings]
systray_visible = 0
systray_messages = 0


[last_used]
device_uri = "hp:/usb/Deskjet_3520_series?serial=CN34G1C5G005T0"
printer_name = 
working_dir = .


[commands]
scan = /usr/bin/xsane -V %SANE_URI%


[refresh]
rate = 30
enable = false
type = 1


[polling]
enable = false
interval = 5
device_list = 


[fax]
voice_phone = 
email_address = 


[installation]
date_time = 07/01/2014 00:04:36
version = 3.14.6




 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>


--------------------------
|  External Dependencies |
--------------------------


 policykit            Admin-Policy-framework    OPTIONAL        -               0.105           OK         -
 gs                   Ghostscript               REQUIRED        7.05            9.10            OK         -
 network              Network-wget              OPTIONAL        -               1.14            OK         -
 scanimage            Shell-Scanning            OPTIONAL        1.0             1.0.23          OK         -
 avahi-utils          avahi-utils               OPTIONAL        -               0.6.31          OK         -
 dbus                 DBus                      REQUIRED        -               1.6.12          OK         -
 cups                 CUPS                      REQUIRED        1.1             1.7             OK         'CUPS Scheduler is running'
 xsane                SANE-GUI                  OPTIONAL        0.9             0.998           OK         -


-------------------------
|  General Dependencies |
-------------------------


 reportlab            Python-PDF-Lib            OPTIONAL        2.0             2.6             OK         -
 libcrypto            OpenSSL-Crypto-Lib        REQUIRED        -               1.0.1           OK         -
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.10.3          OK         -
 libjpeg              JPEG-Lib                  REQUIRED        -               -               OK         -
 libpthread           POSIX-Threads-Lib         REQUIRED        -               2.17            OK         -
 python-dbus          Python-DBUS               REQUIRED        0.80.0          1.2.0           OK         -
 python-devel         Python-SDK                REQUIRED        2.2             2.7.5           OK         -
 pyqt4                Python-Qt4                REQUIRED        4.0             4.10.3          OK         -
 cups-devel           CUPS-SDK                  REQUIRED        -               1.7             OK         -
 sane-devel           SANE-SDK                  REQUIRED        -               1.0.23          OK         -
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
 sane                 Scan-Lib                  REQUIRED        -               1.0.23          OK         -
 cups-image           CUPS-Image-Lib            REQUIRED        -               1.7             OK         -
 libnetsnmp-devel     SNMP-Networking-SDK       REQUIRED        5.0.9           5.7.2           OK         -
 python-xml           Python-XML-Lib            REQUIRED        -               2.1.0           OK         -
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -


------------------------------
|  Compile Time Dependencies |
------------------------------


 gcc                  gcc-Compiler              REQUIRED        -               4.8.1           OK         -
 libtool              Build-tools               REQUIRED        -               2.4.2           OK         -
 make                 GNU-Build-tools           REQUIRED        3.0             3.81            OK         -


----------------------
|  Python Extentions |
----------------------


 cupsext              CUPS-Extension            REQUIRED        -               3.14.6          OK         -
 pcardext             PhotoCard-Extension       REQUIRED        -               3.14.6          OK         -
 hpmudext             IO-Extension              REQUIRED        -               3.14.6          OK         -


-----------------------
|  Scan Configuration |
-----------------------


 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.14.6          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension       REQUIRED        -               3.14.6          OK         -


------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------


device `hpaio:/usb/Deskjet_3520_series?serial=CN34G1C5G005T0' is a Hewlett-Packard Deskjet_3520_series all-in-one




--------------------------
| DISCOVERED USB DEVICES |
--------------------------


  Device URI                        Model                 
  --------------------------------  ----------------------
  hp:/usb/Deskjet_3520_series?seri  HP Deskjet 3520 series
  al=CN34G1C5G005T0                                       


---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


 
HP-Deskjet-3520-series
----------------------
Type: Printer
Device URI: hp:/usb/Deskjet_3520_series?serial=CN34G1C5G005T0
PPD: /etc/cups/ppd/HP-Deskjet-3520-series.ppd
PPD Description: HP Deskjet 3520 Series, hpcups 3.14.6
Printer status: printer HP-Deskjet-3520-series is idle.  enabled since Mon 30 Jun 2014 1Processing page 1...
error: Device busy: hp:/usb/Deskjet_3520_series?serial=CN34G1C5G005T0
error: Device not found
error: Communication status: Failed




--------------
| PERMISSION |
--------------


USB             HP-Deskjet-3520-series         Required        -        -        OK       Node:'/dev/bus/usb/001/005' Perm:'  root  lp rw- rw- rw- rw- r--'
 
-----------
| SUMMARY |
-----------


Missing Required Dependencies
-----------------------------
None


Missing Optional Dependencies
-----------------------------
None




Total Errors: 1
Total Warnings: 0




Done.
atharva@atharva-desktop:~$ clear


atharva@atharva-desktop:~$ hp-doctor


HP Linux Imaging and Printing System (ver. 3.14.6)
Self Diagnse Utility and Healing Utility ver. 1.0


Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


 


Checking for Deprecated items....
No Deprecated items are found




Checking for HPLIP updates....
Latest version of HPLIP is already installed.




Checking for Dependencies....


---------------
| SYSTEM INFO |
---------------


 Kernel: 3.11.0-23-generic #40-Ubuntu SMP Wed Jun 4 21:05:24 UTC 2014 GNU/Linux
 Host: atharva-desktop
 Proc: 3.11.0-23-generic #40-Ubuntu SMP Wed Jun 4 21:05:24 UTC 2014 GNU/Linux
 Distribution: ubuntu 13.10
 Bitness: 32 bit




-----------------------
| HPLIP CONFIGURATION |
-----------------------


HPLIP-Version: HPLIP 3.14.6
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  13.10 version 


Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.


[hplip]
version=3.14.6


[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.14.6
html=/usr/share/doc/hplip-3.14.6
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp
bin=/usr/bin


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
internal-tag=3.14.6
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no




Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory


Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1403765050
pending_upgrade_time = 0
latest_available_version = 3.14.6


[settings]
systray_visible = 0
systray_messages = 0


[last_used]
device_uri = "hp:/usb/Deskjet_3520_series?serial=CN34G1C5G005T0"
printer_name = 
working_dir = .


[commands]
scan = /usr/bin/xsane -V %SANE_URI%


[refresh]
rate = 30
enable = false
type = 1


[polling]
enable = false
interval = 5
device_list = 


[fax]
voice_phone = 
email_address = 


[installation]
date_time = 07/01/2014 00:05:25
version = 3.14.6




 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>


--------------------------
|  External Dependencies |
--------------------------


 policykit            Admin-Policy-framework    OPTIONAL        -               0.105           OK         -
 gs                   Ghostscript               REQUIRED        7.05            9.10            OK         -
 network              Network-wget              OPTIONAL        -               1.14            OK         -
 scanimage            Shell-Scanning            OPTIONAL        1.0             1.0.23          OK         -
 avahi-utils          avahi-utils               OPTIONAL        -               0.6.31          OK         -
 dbus                 DBus                      REQUIRED        -               1.6.12          OK         -
 cups                 CUPS                      REQUIRED        1.1             1.7             OK         'CUPS Scheduler is running'
 xsane                SANE-GUI                  OPTIONAL        0.9             0.998           OK         -


-------------------------
|  General Dependencies |
-------------------------


 reportlab            Python-PDF-Lib            OPTIONAL        2.0             2.6             OK         -
 libcrypto            OpenSSL-Crypto-Lib        REQUIRED        -               1.0.1           OK         -
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.10.3          OK         -
 libjpeg              JPEG-Lib                  REQUIRED        -               -               OK         -
 libpthread           POSIX-Threads-Lib         REQUIRED        -               2.17            OK         -
 python-dbus          Python-DBUS               REQUIRED        0.80.0          1.2.0           OK         -
 python-devel         Python-SDK                REQUIRED        2.2             2.7.5           OK         -
 pyqt4                Python-Qt4                REQUIRED        4.0             4.10.3          OK         -
 cups-devel           CUPS-SDK                  REQUIRED        -               1.7             OK         -
 sane-devel           SANE-SDK                  REQUIRED        -               1.0.23          OK         -
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
 sane                 Scan-Lib                  REQUIRED        -               1.0.23          OK         -
 cups-image           CUPS-Image-Lib            REQUIRED        -               1.7             OK         -
 libnetsnmp-devel     SNMP-Networking-SDK       REQUIRED        5.0.9           5.7.2           OK         -
 python-xml           Python-XML-Lib            REQUIRED        -               2.1.0           OK         -
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -


------------------------------
|  Compile Time Dependencies |
------------------------------


 gcc                  gcc-Compiler              REQUIRED        -               4.8.1           OK         -
 libtool              Build-tools               REQUIRED        -               2.4.2           OK         -
 make                 GNU-Build-tools           REQUIRED        3.0             3.81            OK         -


----------------------
|  Python Extentions |
----------------------


 cupsext              CUPS-Extension            REQUIRED        -               3.14.6          OK         -
 pcardext             PhotoCard-Extension       REQUIRED        -               3.14.6          OK         -
 hpmudext             IO-Extension              REQUIRED        -               3.14.6          OK         -


-----------------------
|  Scan Configuration |
-----------------------


 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.14.6          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension       REQUIRED        -               3.14.6          OK         -


------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------


device `hpaio:/usb/Deskjet_3520_series?serial=CN34G1C5G005T0' is a Hewlett-Packard Deskjet_3520_series all-in-one




--------------------------
| DISCOVERED USB DEVICES |
--------------------------


  Device URI                        Model                 
  --------------------------------  ----------------------
  hp:/usb/Deskjet_3520_series?seri  HP Deskjet 3520 series
  al=CN34G1C5G005T0                                       


---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


 
HP-Deskjet-3520-series
----------------------
Type: Printer
Device URI: hp:/usb/Deskjet_3520_series?serial=CN34G1C5G005T0
PPD: /etc/cups/ppd/HP-Deskjet-3520-series.ppd
PPD Description: HP Deskjet 3520 Series, hpcups 3.14.6
Printer status: printer HP-Deskjet-3520-series is idle.  enabled since Mon 30 Jun 2014 1Processing page 1...
error: Device busy: hp:/usb/Deskjet_3520_series?serial=CN34G1C5G005T0
error: Device not found
error: Communication status: Failed




--------------
| PERMISSION |
--------------


USB             HP-Deskjet-3520-series         Required        -        -        OK       Node:'/dev/bus/usb/001/005' Perm:'  root  lp rw- rw- rw- rw- r--'
 


Checking Permissions....
Permissions are correct.




Checking for Configured Queues....
 
Queue(s) configured correctly using HPLIP.




Checking for HP Properitery Plugin's....
No plug-in printers are configured.
 


Checking for Printer Status....
error: 'HP-Deskjet-3520-series' Printer is either Powered-OFF or Failed to communicate.
Turn On Printer and re-run hp-doctor


Diagnose completed...






More information on Troubleshooting,How-To's and Support is available on [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)



```

---

