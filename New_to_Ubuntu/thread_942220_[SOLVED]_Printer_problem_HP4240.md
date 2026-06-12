---
title: "[SOLVED] Printer problem HP4240"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by NancyM on 2008-10-09
Help, Please!  Brand new Ubuntu user (yesterday).  A friend built a computer for me and installed Ubuntu instead of Windows saying I would really like it, and I do.  Except, I bought a new HP printer HP F4240, All-in-One and it will not print.  Copies okay but no print function works.  The computer recognized it and says that it's printing but nothing happens.

What am I doing wrong here?  As you can tell I'm fairly illiterate about these things and could use any help you can give. 

Thanks, NancyM in Memphis and yes I am a:lolflag:

---

### Post by Ubuntiac on 2008-10-09
Hi Nancy and welcome!

Your printer is supported by HP and Ubuntu as you can see at:
[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f4200_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f4200_series.html)

You could try running the HP Linux Imaging and Printing tool and see if that helps, or at least if it gives you an error message.

You can install this by entering into a console:
```
sudo apt-get install hplip && sudo apt-get install hplip-gui

```
If it asks, put in your password, and after it's finished installing (ie everything stops), you can run it by typing (into the console):
```
hplip-gui
```

You can also see if the system itself is spitting out any errors by turning your printer on (when in Ubuntu) and typing:
dmesg | tail

It will give you the last few messages the kernel (the main part that runs hardware) has reported. You probablby won't know what they mean yet, but scan for any phrases that sound nasty like "error" "not found" "unable to..." etc and paste them back here if you see something.

Cheers

Ubuntiac

---

### Post by bumanie on 2008-10-09
Go to add/remove type hplip in the search box and it will come up with hplip toolbox which is basically the same gui as they provide on windows.Just check the box, click apply and it will download and can be found under System --> Preferences --> hplip toolbox.

---

### Post by NancyM on 2008-10-09
Thanks so much. here's what I got: friendly@Aopen:~$ sudo apt-get install hplip && sudo apt-get install hplip-gui
Reading package lists... Done
Building dependency tree        
Reading state information... Done
hplip is already the newest version.
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd libdns32 linux-headers-2.6.24-16-generic
  linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree        
Reading state information... Done
hplip-gui is already the newest version.
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd libdns32 linux-headers-2.6.24-16-generic
  linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
friendly@Aopen:~$ hplip-gui
bash: hplip-gui: command not found
friendly@Aopen:~$ 
Will send info got from other entry next msg. Thanks

---

### Post by NancyM on 2008-10-09
here'w what happened with 'dmesg | tail'
~$ dmesg | tail
[   68.444615] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   68.444914] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   70.190107] NET: Registered protocol family 17
[   82.481660] eth0: no IPv6 routers present
[  779.900410] usb 1-2: new full speed USB device using uhci_hcd and address 2
[  780.069495] usb 1-2: configuration #1 chosen from 1 choice
[  780.541363] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2504
[  780.542677] usbcore: registered new interface driver usblp
[  784.828788] audit(1223562838.644:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=5628 profile="/usr/sbin/cupsd" namespace="default"
[  891.984725] audit(1223562945.860:4): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=5648 profile="/usr/sbin/cupsd" namespace="default"
What 'cha think? Thanks, Nancy

---

### Post by Ubuntiac on 2008-10-09
I don't see anything obviously wrong in the dmesg. You might need to install HP's printer toolbox. You can try running it with:

1.
```
hp-toolbox
```
in the console.

2. And if that's not found install it with:
```
sudo apt-get install hp-toolbox
```
and then try step 1 again.

---

### Post by bumanie on 2008-10-09
Don't use command line, go to add/remove and put hplip in search and then install the hplip toolbox.

---

### Post by Ubuntiac on 2008-10-09
Is there something less desirable with using the command line, or is it just considered less user friendly to point new users to command line rather than gui?

---

### Post by NancyM on 2008-10-09
friendly@Aopen:~$ hp-toolbox

HP Linux Imaging and Printing System (ver. 2.8.2)
HP Device Manager ver. 11.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


HP Linux Imaging and Printing System (ver. 2.8.2)
Services and Status Daemon ver. 9.3

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
error: Unsupported model: Deskjet_F4200_series
friendly@Aopen:~$ 
friendly@Aopen:~$ sudo apt-get install hp-toolbox
[sudo] password for friendly: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hp-toolbox
friendly@Aopen:~$ 

Here's what I got on first try.  By going to add/remove I got
friendly@Aopen:~$ sh hplip-2.8.8.44.run
sh: Can't open hplip-2.8.8.44.run
friendly@Aopen:~$ sh hplip-2.8.9.run
sh: Can't open hplip-2.8.9.run
friendly@Aopen:~$ 

I'm afraid you must be very basic with me.  Thank you for your patience. NancyM..getting to be an older :lolflag:

---

### Post by NancyM on 2008-10-10
I went to the Ubuntu documentation pages for HpALLnOne and followed those instructions, Just as I deleted the printer from System Admin..etc..a pop-up showed that the Deskjet F4200 added.. BUT still no print. Here's more stuff.  Any ideas?
friendly@Aopen:~$ sudo hp-check -r
[sudo] password for friendly: 
Sorry, try again.
[sudo] password for friendly: 

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
warning: Invalid drv_dir value: /usr/share/cups/drv/hp/

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux Aopen 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

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
error: Version: (Not available. CUPS may not be installed or not running.)


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
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes sane-utils

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

 
Deskjet_F4200_series
--------------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/Deskjet_F4200_series?serial=CN8732N25905BR
PPD: /etc/cups/ppd/Deskjet_F4200_series.ppd
PPD Description: HP 910 Foomatic/hpijs, hpijs 2.8.2
Printer status: printer Deskjet_F4200_series is idle.  enabled since Thu 09 Oct 2008 11:00:08 PM CDT
error: Unsupported model: Deskjet_F4200_series


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
error: Not found. SANE backend 'hpaio' NOT properly setup (needs to be added to /etc/sane.d/dll.conf).

Checking output of 'scanimage -L'...
error: scanimage not found.

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
 
HP Device 0x2504 at 001:007: 
    Device URI: hp:/usb/Deskjet_F4200_series?serial=CN8732N25905BR
    Device node: /dev/bus/usb/001/007
    Mode: 0660
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/007
# owner: lp
# group: scanner
user::rw-
user:friendly:rw-
group::rw-
mask::rw-
other::---

-----------
| SUMMARY |
-----------

error: 5 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo apt-get install --yes --force-yes sane-utils

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

---

### Post by Ubuntiac on 2008-10-10
Hmmm... so when you ran hp-toolbox it didn't open a window with printer options?

It's also odd that it's saying "Unsupported Model" when HP's page clearly says it *is* supported. It may just be that because your printer is so new that the driver isn't included in your version of Ubuntu yet. If that's the case then it will likely be in the next version (Intrepid, due out this month). Until then you can try installing the latest version by:

1. Clicking on the big shiny green "Download HPLIP" button on [this page]("http://hplipopensource.com/hplip-web/downloads.html").

2. Save the file (hplip-2.8.9.run or something similar) to your home directory (/home/friendly from the look of it)

3. Open a console and type:
> cd ~
sh hplip-2.8.9.run

4. Follow [this guide at HP]("http://hplipopensource.com/hplip-web/install/install/index.html") from step 3 onwards. You can type "a" for automatic when asked whether you want automatic or custom mode.

---

### Post by Ubuntiac on 2008-10-10
Oh, you can also ask HP directly by visiting [this page]("https://launchpad.net/hplip") and clicking "Ask a Question" - the purple button (You may need to create an account). If you do this I'd supply them with a link to this thread so they can see what you've tried.

---

### Post by kansasnoob on 2008-10-10
Did your friend install 8.10 Beta?

If so hplip and hpijs have issues still in the 8.10 beta.

Major issues!

---

### Post by beadrifle on 2010-04-16
hplip-gui fixed the problem for me.

An hp-check will tell you all that you need to know down below at the summary of errors.

---

### Post by ajaustin on 2010-07-31
> **Ubuntiac said:**
> 

you can try installing the latest version by:

1. Clicking on the big shiny green "Download HPLIP" button on [this page]("http://hplipopensource.com/hplip-web/downloads.html"). [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

2. Save the file (hplip-x.x.x.run or something similar) to your home directory (/home/friendly from the look of it)

3. Open a console and type:


4. Follow [this guide at HP]("http://hplipopensource.com/hplip-web/install/install/index.html") from step 3 onwards. You can type "a" for automatic when asked whether you want automatic or custom mode.

Thanks Ubuntiac.  The download from HP resolves all the dependency conflicts automagically and updates everything.

Worked a treat for me.

Tony

---

