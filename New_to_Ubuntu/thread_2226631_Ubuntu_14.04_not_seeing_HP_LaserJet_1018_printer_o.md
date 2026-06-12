---
title: "Ubuntu 14.04 not seeing HP LaserJet 1018 printer on USB"
date: 2014-05-28
forum: New to Ubuntu
---

### Post by swarup on 2014-05-28
I am using Ubuntu 14.04, and the HP LaserJet 1018 printer is connected via USB. But for some reason it is not being detected. I've installed the latest version of the HP printer driver software [hplip (3.14.4)]. It has a diagnostics tool, which I have run. Here below is what seems to be the critical part of the output:

```
--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

HP_LaserJet_1018_2
------------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_1018?serial=KP0SYPQ
PPD: /etc/cups/ppd/HP_LaserJet_1018_2.ppd
PPD Description: HP LaserJet 1018, hpcups 3.14.3, requires proprietary plugin
Printer status: printer HP_LaserJet_1018_2 is idle. enabled since Wed 28 May 2014 07:48Rendering completed
Required plug-in status: Installed
error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_1018?serial=KP0SYPQ
error: Device not found
error: Communication status: Failed
```

I have used this printer with many earlier distributions of Ubuntu and never had a problem. But now for some reason the printer is not being found as connected to the USB port.

Here below is the full output of the diagnostics tool, in case it may be helpful. Note that  I also have an HP OfficeJet 5610, which is not connected. You can ignore the information showing below about that printer. I am just interested in getting the HP Laser Jet 1018 to print dependably.

```
HP Linux Imaging and Printing System (ver. 3.14.4)
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

 Kernel: 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 GNU/Linux
 Host: swarup
 Proc: 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 GNU/Linux
 Distribution: ubuntu 14.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.14.4
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  14.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.14.4

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.14.4
html=/usr/share/doc/hplip-3.14.4
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
internal-tag=3.14.4
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
[plugin]
installed = 1
eula = 1
version = 3.14.4



Current contents of '~/.hplip/hplip.conf' file:
[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = "hp:/usb/HP_LaserJet_1018?serial=KP0SYPQ"
printer_name = 
working_dir = .

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[refresh]
rate = 30
enable = true
type = 1

[polling]
enable = false
interval = 5
device_list = 

[fax]
voice_phone = 
email_address = 

[upgrade]
notify_upgrade = true
last_upgraded_time = 1398824791
pending_upgrade_time = 0
latest_available_version = 3.14.4

[installation]
date_time = 05/28/2014 07:49:24
version = 3.14.4


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------------------
|  External Dependencies |
--------------------------

 policykit            Admin-Policy-framework    OPTIONAL        -               0.105           OK         -
 gs                   Ghostscript               REQUIRED        7.05            9.10            OK         -
 network              Network-wget              OPTIONAL        -               1.15            OK         -
 scanimage            Shell-Scanning            OPTIONAL        1.0             1.0.23          OK         -
 avahi-utils          avahi-utils               OPTIONAL        -               0.6.31          OK         -
 dbus                 DBus                      REQUIRED        -               1.6.18          OK         -
 cups                 CUPS                      REQUIRED        1.1             1.7.2           OK         'CUPS Scheduler is running'
 xsane                SANE-GUI                  OPTIONAL        0.9             0.998           OK         -

-------------------------
|  General Dependencies |
-------------------------

 reportlab            Python-PDF-Lib            OPTIONAL        2.0             3.0             OK         -
 libcrypto            OpenSSL-Crypto-Lib        REQUIRED        -               1.0.1           OK         -
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.10.4          OK         -
 libjpeg              JPEG-Lib                  REQUIRED        -               -               OK         -
 libpthread           POSIX-Threads-Lib         REQUIRED        -               2.19            OK         -
 python-dbus          Python-DBUS               REQUIRED        0.80.0          1.2.0           OK         -
 python-devel         Python-SDK                REQUIRED        2.2             2.7.6           OK         -
 pyqt4                Python-Qt4                REQUIRED        4.0             4.10.4          OK         -
 cups-devel           CUPS-SDK                  REQUIRED        -               1.7.2           OK         -
 sane-devel           SANE-SDK                  REQUIRED        -               1.0.23          OK         -
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
 sane                 Scan-Lib                  REQUIRED        -               1.0.23          OK         -
 cups-image           CUPS-Image-Lib            REQUIRED        -               1.7.2           OK         -
 libnetsnmp-devel     SNMP-Networking-SDK       REQUIRED        5.0.9           5.7.2           OK         -
 python-xml           Python-XML-Lib            REQUIRED        -               2.1.0           OK         -
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -

------------------------------
|  Compile Time Dependencies |
------------------------------

 gcc                  gcc-Compiler              REQUIRED        -               4.8.2           OK         -
 libtool              Build-tools               REQUIRED        -               2.4.2           OK         -
 make                 GNU-Build-tools           REQUIRED        3.0             3.81            OK         -

----------------------
|  Python Extentions |
----------------------

 cupsext              CUPS-Extension            REQUIRED        -               3.14.4          OK         -
 pcardext             PhotoCard-Extension       REQUIRED        -               3.14.4          OK         -
 hpmudext             IO-Extension              REQUIRED        -               3.14.4          OK         -

-----------------------
|  Scan Configuration |
-----------------------

 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.14.4          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension       REQUIRED        -               3.14.4          OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

No Scanner found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_LaserJet_1018_2
------------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_1018?serial=KP0SYPQ
PPD: /etc/cups/ppd/HP_LaserJet_1018_2.ppd
PPD Description: HP LaserJet 1018, hpcups 3.14.3, requires proprietary plugin
Printer status: printer HP_LaserJet_1018_2 is idle.  enabled since Wed 28 May 2014 07:48Rendering completed
Required plug-in status: Installed
error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_1018?serial=KP0SYPQ
error: Device not found
error: Communication status: Failed

Officejet-5600-series
---------------------
Type: Printer
Device URI: hp:/usb/Officejet_5600_series?serial=CN63IDE0B604CY
PPD: /etc/cups/ppd/Officejet-5600-series.ppd
PPD Description: HP Officejet 5600 Series, hpcups 3.14.3
Printer status: printer Officejet-5600-series is idle.  enabled since Mon 28 Apr 2014 01:16:02 PM EDT
error: Unable to communicate with device (code=12): hp:/usb/Officejet_5600_series?serial=CN63IDE0B604CY
error: Device not found
error: Communication status: Failed

Officejet-5600-series-Fax
-------------------------
Type: Fax
Device URI: hpfax:/usb/Officejet_5600_series?serial=CN63IDE0B604CY
PPD: /etc/cups/ppd/Officejet-5600-series-Fax.ppd
PPD Description: HP Fax hpcups
Printer status: printer Officejet-5600-series-Fax is idle.  enabled since Mon 28 Apr 2014 01:16:04 PM EDT
error: Unable to communicate with device (code=12): hpfax:/usb/Officejet_5600_series?serial=CN63IDE0B604CY
error: Device not found
error: Communication status: Failed


--------------
| PERMISSION |
--------------

 

Checking Permissions....
Permissions are correct.


Checking for Configured Queues....
 
Queue(s) configured correctly using HPLIP.


Checking for HP Properitery Plugin's....
Plugin's already installed
 

Checking for Printer Status....
error: 'Officejet-5600-series-Fax' Printer is either Powered-OFF or Failed to communicate.
Turn On Printer and re-run hp-doctor
error: 'HP_LaserJet_1018_2' Printer is either Powered-OFF or Failed to communicate.
Turn On Printer and re-run hp-doctor
error: 'Officejet-5600-series' Printer is either Powered-OFF or Failed to communicate.
Turn On Printer and re-run hp-doctor

Diagnose completed...



More information on Troubleshooting,How-To's and Support is available on http://hplipopensource.com/hplip-web/index.html


Please close this terminal manually. 


```

I would really appreciate any tip on how to get the computer to recognize the device on the USB port. I've been trying for several weeks, and have searched the web without finding any solution.

---

### Post by doctorbighands on 2014-05-28
Hi! I'm sorry you've been having so much trouble! Let's see if we can't get you up and running.

First, the obvious: Make sure your printer is powered on! I know it seems dumb, but first thing's first.

Now, the next thing to check is whether the computer sees the printer at all. With the printer powered on and plugged into the computer, make sure it shows up in the list of devices when you run

```
lsusb
```

in the terminal.

If it shows up in the list, then we make sure you're added to the "lp" and "sys" groups (a "Code 12" error in CUPS often means that this is the issue). Input the following two commands separately:

```
sudo usermod -a -G lp <your user name>
```
```
sudo usermod -a -G sys <your user name>
```

Just backspace over "<your user name>" and type yourself in there.

Once those are done, try installing the printer once more. I might reboot the computer once, just to be sure, if I were you.

Try these steps first. If you're still having trouble, we'll go further!

---

### Post by swarup on 2014-05-28
Thank you so much for coming to help!

I ran lsusb, and the printer isn't in the list of connected devices. So it doesn't look like the computer sees the printer. Which I guess is what the hp diagnostics check in my first post showed as well.

The next two commands you indicated to do only if the printer showed up in the lsusb list, which it did not. So what should be my next step?

---

### Post by swarup on 2014-05-29
Sorry to bump this thread-- I've been struggling for several weeks on my own to get this printer working, and for some reason it is not seen as connected to the USB port in 14.04. I've used this very printer with the hplip printer driver in several previous Ubuntu distributions with no problems whatsoever. Any suggestion for how to get the printer to be seen as connected to the USB?

---

### Post by tripp98 on 2014-05-29
When your reboot the computer does the printer come alive?  Does it move or lights change?   Have you tried it in a different usb port or tried different usb cable?  After you try a different usb port use terminal and do lsusb

another good method would be watch the syslog as you plug / unplug the printer.

tail -f /var/log/syslog



Just a few suggestions.

---

### Post by swarup on 2014-05-29
After reading your post, I just tried plugging the printer in again. When I plugged in the printer to the usb port, it did bring the printer alive, making the motor start moving and the lights change. And this time it showed up with lsusb:
```

~$ lsusb
Bus 002 Device 010: ID 03f0:4117 Hewlett-Packard LaserJet 1018
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

But when I open the HP device manager, it still shows device communication error 5012. I tried to print a page, and it would not print. In the job queue, the print order I gave is listed as "on hold". But the "status" window of the device manager shows that the print job was started, and that it was completed. Yet nothing printed.

Here is the output of the syslog. I ran it now, with the printer already plugged in. But it does give info below about the printer, that it could not open the device.

```
~$ tail -f /var/log/syslog
May 29 22:33:43 swarup avahi-daemon[821]: Received response from host 192.168.1.133 with invalid source port 51130 on interface 'eth0.0'
May 29 22:33:43 swarup avahi-daemon[821]: Received response from host 192.168.1.133 with invalid source port 51130 on interface 'wlan0.0'
May 29 22:33:44 swarup avahi-daemon[821]: Received response from host 192.168.1.133 with invalid source port 51130 on interface 'eth0.0'
May 29 22:33:44 swarup avahi-daemon[821]: Received response from host 192.168.1.133 with invalid source port 51130 on interface 'wlan0.0'
May 29 22:33:45 swarup avahi-daemon[821]: Received response from host 192.168.1.133 with invalid source port 51130 on interface 'eth0.0'
May 29 22:33:45 swarup avahi-daemon[821]: Received response from host 192.168.1.133 with invalid source port 51130 on interface 'wlan0.0'
May 29 22:36:35 swarup hp[28019]: io/hpmud/musb.c 150: unable get_string_descriptor -7: Resource temporarily unavailable
May 29 22:36:35 swarup hp[28019]: io/hpmud/musb.c 599: invalid product id string ret=-7
May 29 22:36:35 swarup hp[28019]: io/hpmud/musb.c 1142: unable to open hp:/usb/HP_LaserJet_1018?serial=KP0SYPQ
May 29 22:36:35 swarup hp[28019]: prnt/backend/hp.c 745: ERROR: open device failed stat=12: hp:/usb/HP_LaserJet_1018?serial=KP0SYPQ
```

A few minutes later I unplugged the printer, and logged out of Ubuntu and then back in. Then I plugged the printer into a different USB port. This time there was no external sign of activation-- the printer motor did not go on, and the lights did not flash or change. Here is the output of syslog just after plugging in the printer:

```
May 29 22:45:37 swarup kernel: [88896.552218] usb 1-1: new high-speed USB device number 10 using ehci-pci
May 29 22:45:52 swarup kernel: [88911.664211] usb 1-1: device descriptor read/64, error -110
May 29 22:46:07 swarup kernel: [88926.880209] usb 1-1: device descriptor read/64, error -110
May 29 22:46:08 swarup kernel: [88927.096195] usb 1-1: new high-speed USB device number 11 using ehci-pci
May 29 22:46:23 swarup kernel: [88942.208209] usb 1-1: device descriptor read/64, error -110
May 29 22:46:38 swarup kernel: [88957.424203] usb 1-1: device descriptor read/64, error -110
May 29 22:46:38 swarup kernel: [88957.640191] usb 1-1: new high-speed USB device number 12 using ehci-pci
May 29 22:46:43 swarup kernel: [88962.660462] usb 1-1: device descriptor read/8, error -110
May 29 22:46:48 swarup kernel: [88967.780464] usb 1-1: device descriptor read/8, error -110
May 29 22:46:49 swarup kernel: [88967.996181] usb 1-1: new high-speed USB device number 13 using ehci-pci
May 29 22:46:54 swarup kernel: [88973.016416] usb 1-1: device descriptor read/8, error -110
May 29 22:46:59 swarup kernel: [88978.136465] usb 1-1: device descriptor read/8, error -110
May 29 22:46:59 swarup kernel: [88978.240211] hub 1-0:1.0: unable to enumerate USB device on port 1
May 29 22:46:59 swarup kernel: [88978.696201] usb 3-1: new full-speed USB device number 6 using ohci-pci
May 29 22:47:14 swarup kernel: [88993.872229] usb 3-1: device descriptor read/64, error -110
May 29 22:47:30 swarup kernel: [89009.152211] usb 3-1: device descriptor read/64, error -110
May 29 22:47:30 swarup kernel: [89009.432209] usb 3-1: new full-speed USB device number 7 using ohci-pci
May 29 22:47:45 swarup kernel: [89024.608187] usb 3-1: device descriptor read/64, error -110
May 29 22:48:00 swarup kernel: [89039.888213] usb 3-1: device descriptor read/64, error -110
May 29 22:48:01 swarup kernel: [89040.168189] usb 3-1: new full-speed USB device number 8 using ohci-pci
May 29 22:48:06 swarup kernel: [89045.188365] usb 3-1: device descriptor read/8, error -110
May 29 22:48:11 swarup kernel: [89050.308408] usb 3-1: device descriptor read/8, error -110
May 29 22:48:11 swarup kernel: [89050.588210] usb 3-1: new full-speed USB device number 9 using ohci-pci
May 29 22:48:16 swarup kernel: [89055.608353] usb 3-1: device descriptor read/8, error -110
May 29 22:48:21 swarup kernel: [89060.728438] usb 3-1: device descriptor read/8, error -110
May 29 22:48:21 swarup hp[29642]: io/hpmud/musb.c 1142: unable to open hp:/usb/HP_LaserJet_1018?serial=KP0SYPQ
May 29 22:48:21 swarup hp[29642]: prnt/backend/hp.c 745: ERROR: open device failed stat=12: hp:/usb/HP_LaserJet_1018?serial=KP0SYPQ
May 29 22:48:21 swarup kernel: [89060.836202] hub 3-0:1.0: unable to enumerate USB device on port 1
```

Note: When I run lsusb now, the printer does not show up.

---

### Post by tripp98 on 2014-05-30
ok just found this.

[http://askubuntu.com/questions/37126/hp-laserjet-1018-printer-keeps-asking-me-to-install-it-everytime-i-plug-it-in](http://askubuntu.com/questions/37126/hp-laserjet-1018-printer-keeps-asking-me-to-install-it-everytime-i-plug-it-in)

it may help.  looks like lots of people have the problem

---

### Post by swarup on 2014-05-30
The four posts on that link you've given are all addressing problems people were having getting the printer to work with Ubuntu 11.04 Beta 2, three years ago. I am working with Ubuntu 14.04 and a much later version of hplip, the hp driver software and its device manager. I don't want to start clicking on the things they recommended to download there three years ago. I need recommendations which are relevant to the current situation. This is a great printer and I've been using it for years with several different Ubuntu distributions without issue. If someone can help to get it properly recognized, I will be so appreciative.

---

### Post by swarup on 2014-06-12
Yesterday I connected my HP LaserJet 1018 Printer to my colleague's computer which is running Ubuntu 12.04. As soon as I connected the printer, the computer identified it as the HP LJ 1018, and asked if I would like to have the plug-in installed for it. I clicked "yes". Immediately a terminal window opened, the plug-in was installed, the printer motor was activated, and it is printing perfectly. I could not believe how easy it was-- it took merely 2 minutes to do. Given that, why would 14.04 not be able to do the same? 

I started a [thread at the HP Linux Imaging and Printing site]("https://answers.launchpad.net/hplip/+question/249391"), but have not received any help there. There are further details about the output of the printer driver's diagnostics tool there.

---

### Post by oldfred on 2014-06-12
I would think it should be the same or better, but there are regressions.

Was the plug in that installed automatically in 12.04 the same as suggested in the old threads?
And can you copy plugin from 12.04 and install in 14.04 if it is different?

---

### Post by natasa2 on 2014-06-21
I have a feeling that this issue is related to a kernel. Same issue appears with OpenSuse 13.1. Initially it worked, and after a batch of upgrades with new kernel version, printer stopped being reported as connected on USB (no matter reboot or re-plug USB cord or change cable or change computer). Error reported is the same as with Ubuntu, about USB and error number "-110", so I assume correct answer is to look at the issues with the kernel. I am also interested in resolution with this printer which always had clunky support in linux (sometimes it required re-plugging USB cable, sometimes full system reboot, sometimes different kernel version, sometimes different driver versions, sometimes other configuration hacks). ](*,)

---

### Post by swarup on 2014-06-26
There is a bug in Ubuntu 14.04 which has now been recognized, due to which the HP 1018 is not getting recognized. See this link:

[https://bugs.launchpad.net/hplip/+bug/1315408](https://bugs.launchpad.net/hplip/+bug/1315408)

And yes, they seem to be saying there that it is related to the kernel. It is been been reported there that: 

> on ubuntu 13.10 my USB printer hp-1018 worked seamlessly. Upgrade to 14.04 (hplip 3.14.3-0ubuntu3) caused hp-setup not to recognize the printer anymore (error: No devices found on bus: usb)....The printer works properly on ubuntu 14.04 under kernel 3.8.0 (taken from ubuntu 12.04).

---

### Post by swarup on 2014-07-07
A workaround has been provided in the bug report. Here are the instructions for all interested. They worked great! Problem solved!

> WORKAROUND: use hplip from ubuntu 13.10 (use "sudo su -")

1) Remove hplip of 14.04 (for some reason apt-get won't do that automatically)
apt-get remove hplip

2) Add repo strings for 13.10
cat > /etc/apt/sources.list.d/saucy.list <<EOF
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) saucy main restricted
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) saucy universe
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) saucy multiverse
EOF

3) apt-get update

4) install hplip of 13.10
apt-get install hplip=3.13.9-1 libhpmud0=3.13.9-1 libsane-hpaio=3.13.9-1 hplip-data=3.13.9-1 printer-driver-hpcups=3.13.9-1

5) pin hplip to protect from upgrades
echo hplip hold | dpkg --set-selections

---

### Post by swarup on 2014-07-11
In my earlier report above, I thought that the workaround was going to work for me just fine, as when it installed, the printer worked. And one subsequent time I used it, it worked again. But there are two problems now:

1) Every time I plug the printer in and turn it on, the computer asks for my password and reinstalls the driver plug in. I give permisison to install it, and usually then get a reply that the plug-in has successfully installed. But sometimes it gives two messages-- first one saying the installation failed, and then when I close that another message behind it saying the installation was successful. But I have to go through this every time I turn on the printer.

2) It is no longer printing. It installs the driver plug in every time I turn it on, but does not print. I have several print orders pending now, and in the status window it shows the print orders, and next to each is the status "pending - not connected ?". So it does not seem to be seeing the printer any more.

We definitely need a more dependable solution to this issue.

---

### Post by oldfred on 2014-07-11
Some more possibilities:

HPLIP issue on 14.04 - manual download of plugin to solve
[http://ubuntuforums.org/showthread.php?t=2230875](http://ubuntuforums.org/showthread.php?t=2230875)
HP printers broken in Linux? Here's a fix. 
[http://www.dedoimedo.com/computers/linux-hp-printing.html](http://www.dedoimedo.com/computers/linux-hp-printing.html)

---

### Post by ppguara on 2015-06-29
First thanks all for all the info, had this problem as well...

The solution given by waran777 here at the bottom worked for me:

[https://bugs.launchpad.net/hplip/+bug/1315408?comments=all](https://bugs.launchpad.net/hplip/+bug/1315408?comments=all)

---

