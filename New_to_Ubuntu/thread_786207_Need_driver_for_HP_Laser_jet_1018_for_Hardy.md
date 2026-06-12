---
title: "Need driver for HP Laser jet 1018 for Hardy"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by swarup on 2008-05-07
I have been using this HP Laser jet 1018 for a year with Feisty, and it worked well with a few glitches here and there. Now I have installed Hardy on another computer, and it recognizes that the printer is "HP Laser Jet 1018", but it does not print. Should I bring over the driver that I got last year for Feisty? If so, then please inform where in Feisty the printer driver is kept so I can go get it. And if over the course of the last year there may have been a better driver developed i.e. for Hardy, then where can I get it from? I went to this [http://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp]("http://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp") link, but the instructions there for my printer are from 2006-Dec-26, and were given for Edgy (6.10). I'm thinking there must be something newer than that available.

---

### Post by ramjet_1953 on 2008-05-08
This link should help you to get it going.

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018)

Regards,
Roger :cool:

---

### Post by swarup on 2008-05-08
Thanks for the help :)

I've also just found a few very good links. For anyone who has Ubuntu 7.04 (Feisty) or later, the install is extremely simple. See the below instruction. You need look no further than this: [NOTE-- SEE MY NEXT POST. I HAVE FOUND A MUCH BETTER INSTALL METHOD THAN THE ONE IN THIS POST. I RECOMMEND YOU TO IGNORE THE INSTRUCTION IN THIS POST, AND FOLLOW THOSE IN THE NEXT POST.]

- - - - - - - - - - - -

17 May 2007 - On Ubuntu Feisty, you do not need to download foo2zjs from it's homepage (and recompile it) anymore. Only the firmware is missing in the distribution; to get it just enter this in a root shell (sudo bash): 
getweb 1018 ; arm2hpdl sihp1018.img > /usr/share/foo2zjs/firmware/sihp1018.dl

In cleaner language, here below is the direction:

```
sudo bash
```

```
getweb 1018 ; arm2hpdl sihp1018.img > /usr/share/foo2zjs/firmware/sihp1018.dl
```

&#65279;Then power off and on the printer and do the printer setup as usual i.e. select HP 1018 as your printer. (This can be done simply at the time of your first time printing something, by pointing to "HP 1018" in the print window options.)

---

### Post by swarup on 2008-05-08
In the last 12 hours I've done quite a bit of research on installing HP Laser Jet 1018. I first did what I outlined above. But I found that the install was not giving a dependable result. Sometimes when I tried to print it would print, and sometimes not. 

Since then I searched the various help links thoroughly and went through them all, comparing the instructions on each one. 

I found one link to be the most definitive and solid, and having done the install using it, the printer is now working really well for me. 

Here is the link: [http://foo2zjs.rkkda.com/INSTALL](http://foo2zjs.rkkda.com/INSTALL)

On that link, they give install instructions for several different Linux distributions. Here below I am pasting the instructions from that site which are specific for Ubuntu. If you follow this line by line, as per my experience you will get a very good result indeed.

My recommendation is to first open Synaptic Package Manager, select the package "foo2zjs", and remove it. That is the driver you are going to be installing below. I had seen someone else do that on the forums for this printer, and it makes sense. You want a clean install. That is what I did, and it is working great. 

Once you remove "foo2zjs", then follow the below instructions.

Note: For Gutsy and later users, **this** line found in the below instructions will be your last instruction. 

     ```
For 7.10 and later users:
        $ sudo system-config-printer
```

(Once you do this in the below instructions, you are done. At this point the GUI for the HP 1018 printer settings will open automatically, and you can look through them to make sure they are as you want them. Click on the button in the GUI for setting this printer as the default. All the rest of the settings should be fine.)

```

INSTALLING LASER JET 1018 IN UBUNTU
------------
    Install build-essential FIRST:
	$ sudo apt-get install build-essential
	$ wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
	$ tar zxf foo2zjs.tar.gz
	$ cd foo2zjs
	$ sudo make uninstall
	$ make
	$ ./getweb 1018
	$ sudo make install install-hotplug cups

	For 7.10 and later users:
	    $ sudo system-config-printer

(Ignore the rest if you are using Gutsy or Hardy)

	For 5.10/6.06/6.10/7.04 users:
	    $ sudo gnome-cups-manager
	    [configure ColorMode = Color if a color printer]
	    $ sudo make cups

	    Ubuntu has a bug in gnome-cups-manager with Color, so you must
	    restart cups.  No other distro has this bug.

    If that doesn't work, then fire up:
	$ firefox http://localhost:631

    And click on:
	Printers -> Set Printer Options -> Color Mode -> Color
    Then click on:
	Set Printer Options
```

---

### Post by davide.del.vento on 2008-06-11
Ok, I confirm this behavior, but WHY is this happening? It seems pretty weird, to have to unistall something from the package manager and re-install it from the old-fashioned tarball!
I created this bug report, hopefully we can fix it. [https://bugs.launchpad.net/ubuntu/+source/foo2zjs/+bug/239079](https://bugs.launchpad.net/ubuntu/+source/foo2zjs/+bug/239079)
Ciao,
;Dav

---

### Post by vague jayhawk on 2008-08-18
Thanks for the help.  This worked well.  It was exactly what I needed.

---

### Post by shirilover on 2008-08-19
Just curious, but did hplip not work?

[This page]("http://hplip.sourceforge.net/models/laserjet/hp_laserjet_1018.html") does say a driver plugin is required. That may have been what was missing.

---

### Post by gjoellee on 2008-08-19
[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

---

### Post by alienexplorers on 2008-08-19
The laser jet 1018 is part of the hplip package:
```
HP LaserJet 1018

Supported by HPLIP (requires HPLIP version 2.7.10 or later).

This information applies to these HP printer models:
Model Name
HP LaserJet 1018
HP LaserJet 1018s
Driver Plugin Information:

This printer REQUIRES a downloadable driver plug-in. Use hp-setup to install the printer, and to download and install the plug-in. In general, required driver plugins are required for printing support. Driver plug-ins are released under a proprietary (non-open) license and are not part of the HPLIP tarball release.
Summary of features available in various Linux distributions:
Distro	Version	Installer	GUI	Scan	Fax	Status	Photo Card	USB	Parallel	Network
Debian	2.2	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	3.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	3.1	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	4.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	4.0r0	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	4.0r1	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	5.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	lenny	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	lenny/sid	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	stable	Yes	Yes	No	No	Yes	No	Yes	No	No
Debian	testing	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	1.0	No	Yes	No	No	Yes	No	Yes	No	No
Fedora	2.0	No	Yes	No	No	Yes	No	Yes	No	No
Fedora	3.0	No	Yes	No	No	Yes	No	Yes	No	No
Fedora	4.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	5.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	5	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	5.92	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	6.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	6	Yes	Yes	No	No	Yes	No	Yes	No	No
Distro	Version	Installer	GUI	Scan	Fax	Status	Photo Card	USB	Parallel	Network
Fedora	7	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	7.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	8.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	8	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	9	Yes	Yes	No	No	Yes	No	Yes	No	No
Fedora	9.0	Yes	Yes	No	No	Yes	No	Yes	No	No
IGOS	1.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Linspire	5.0	No	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	9.1	No	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	9.2	No	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	10.0	No	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	10.1	Yes	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	10.2	Yes	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	2006.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	2007.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	2007.1	Yes	Yes	No	No	Yes	No	Yes	No	No
Mandriva Linux	2008.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Mepis	6.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Mepis	6.5	Yes	Yes	No	No	Yes	No	Yes	No	No
Mepis	7.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Distro	Version	Installer	GUI	Scan	Fax	Status	Photo Card	USB	Parallel	Network
PCLinuxOS	2006.0	Yes	Yes	No	No	Yes	No	Yes	No	No
PCLinuxOS	2006	Yes	Yes	No	No	Yes	No	Yes	No	No
PCLinuxOS	2007.0	No	Yes	No	No	Yes	No	Yes	No	No
PCLinuxOS	2007	No	Yes	No	No	Yes	No	Yes	No	No
PCLinuxOS	2008.0	No	Yes	No	No	Yes	No	Yes	No	No
PCLinuxOS	2008	No	Yes	No	No	Yes	No	Yes	No	No
Red Hat	8.0	No	No	No	No	Yes	No	Yes	No	No
Red Hat	9.0	No	No	No	No	Yes	No	Yes	No	No
Red Hat Enterprise Linux	3.0	No	Yes	No	No	Yes	No	Yes	No	No
Red Hat Enterprise Linux	4.0	No	Yes	No	No	Yes	No	Yes	No	No
Red Hat Enterprise Linux	5.0	No	Yes	No	No	Yes	No	Yes	No	No
Slackware Linux	9.0	No	No	No	No	Yes	No	No	No	No
Slackware Linux	9.1	No	No	No	No	Yes	No	No	No	No
Slackware Linux	10.0	No	No	No	No	Yes	No	No	No	No
Slackware Linux	10.1	No	No	No	No	Yes	No	No	No	No
Slackware Linux	10.2	No	No	No	No	Yes	No	No	No	No
SUSE Linux	9.0	No	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	9.1	No	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	9.2	No	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	9.3	No	Yes	No	No	Yes	No	Yes	No	No
Distro	Version	Installer	GUI	Scan	Fax	Status	Photo Card	USB	Parallel	Network
SUSE Linux	10	Yes	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	10.0	Yes	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	10.1	Yes	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	10.2	Yes	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	10.3	Yes	Yes	No	No	Yes	No	Yes	No	No
SUSE Linux	11.0	Yes	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	5.04	No	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	5.1	No	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	6.06	Yes	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	6.10	Yes	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	7.04	Yes	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	7.10	Yes	Yes	No	No	Yes	No	Yes	No	No
Ubuntu	8.04	Yes	Yes	No	No	Yes	No	Yes	No	No 
```

---

### Post by la cónica on 2008-10-19
> **swarup said:**
> In the last 12 hours I've done quite a bit of research on installing HP Laser Jet 1018. I first did what I outlined above. But I found that the install was not giving a dependable result. Sometimes when I tried to print it would print, and sometimes not. 

Since then I searched the various help links thoroughly and went through them all, comparing the instructions on each one. 

I found one link to be the most definitive and solid, and having done the install using it, the printer is now working really well for me. 

Here is the link: [http://foo2zjs.rkkda.com/INSTALL](http://foo2zjs.rkkda.com/INSTALL)

On that link, they give install instructions for several different Linux distributions. Here below I am pasting the instructions from that site which are specific for Ubuntu. If you follow this line by line, as per my experience you will get a very good result indeed.

My recommendation is to first open Synaptic Package Manager, select the package "foo2zjs", and remove it. That is the driver you are going to be installing below. I had seen someone else do that on the forums for this printer, and it makes sense. You want a clean install. That is what I did, and it is working great. 

Once you remove "foo2zjs", then follow the below instructions.

Note: For Gutsy and later users, **this** line found in the below instructions will be your last instruction. 

     ```
For 7.10 and later users:
        $ sudo system-config-printer
```

(Once you do this in the below instructions, you are done. At this point the GUI for the HP 1018 printer settings will open automatically, and you can look through them to make sure they are as you want them. Click on the button in the GUI for setting this printer as the default. All the rest of the settings should be fine.)

```

INSTALLING LASER JET 1018 IN UBUNTU
------------
    Install build-essential FIRST:
	$ sudo apt-get install build-essential
	$ wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
	$ tar zxf foo2zjs.tar.gz
	$ cd foo2zjs
	$ sudo make uninstall
	$ make
	$ ./getweb 1018
	$ sudo make install install-hotplug cups

	For 7.10 and later users:
	    $ sudo system-config-printer

(Ignore the rest if you are using Gutsy or Hardy)

	For 5.10/6.06/6.10/7.04 users:
	    $ sudo gnome-cups-manager
	    [configure ColorMode = Color if a color printer]
	    $ sudo make cups

	    Ubuntu has a bug in gnome-cups-manager with Color, so you must
	    restart cups.  No other distro has this bug.

    If that doesn't work, then fire up:
	$ firefox http://localhost:631

    And click on:
	Printers -> Set Printer Options -> Color Mode -> Color
    Then click on:
	Set Printer Options
```

Thanks a lot. I was having problems with HP LaserJet 1018 and this post of yours solved the issue.

---

### Post by IanB2 on 2008-11-01
Unfortunately the method described above did not work for me. Any help would be much appreciated.

A test page appears in the the 'Document print status' dialogue but nothing comes out of the printer.

This is the output from running the troubleshooting dialogue:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8d4e280>,
 'cups_instance': None,
 'cups_queue': 'HP_LaserJet_1018',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/HP_LaserJet_1018?serial=KP3HVY9',
                       'printer-info': u'Hewlett-Packard HP LaserJet 1018',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP LaserJet 1018 Foomatic/foo2zjs (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167940,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HP_LaserJet_1018'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(22, u'Job completed.')],
 'test_page_job_id': [22],
 'test_page_job_status': [(22, 'HP_LaserJet_1018', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

---

### Post by IanB2 on 2008-11-02
> **IanB2 said:**
> Unfortunately the method described above did not work for me. Any help would be much appreciated.

A test page appears in the the 'Document print status' dialogue but nothing comes out of the printer.

This is the output from running the troubleshooting dialogue:

Page 1 (Choose printer):


Very odd ...... this morning I booted into Ubuntu, and thought I'd try the printer and it works!

---

### Post by IanB2 on 2008-11-02
> **swarup said:**
> In the last 12 hours I've done quite a bit of research on installing HP Laser Jet 1018. I first did what I outlined above. But I found that the install was not giving a dependable result. Sometimes when I tried to print it would print, and sometimes not. 

Since then I searched the various help links thoroughly and went through them all, comparing the instructions on each one. 

I found one link to be the most definitive and solid, and having done the install using it, the printer is now working really well for me. 

Here is the link: [http://foo2zjs.rkkda.com/INSTALL](http://foo2zjs.rkkda.com/INSTALL)

On that link, they give install instructions for several different Linux distributions. Here below I am pasting the instructions from that site which are specific for Ubuntu. If you follow this line by line, as per my experience you will get a very good result indeed.

My recommendation is to first open Synaptic Package Manager, select the package "foo2zjs", and remove it. That is the driver you are going to be installing below. I had seen someone else do that on the forums for this printer, and it makes sense. You want a clean install. That is what I did, and it is working great. 

Once you remove "foo2zjs", then follow the below instructions.

Note: For Gutsy and later users, **this** line found in the below instructions will be your last instruction. 

     ```
For 7.10 and later users:
        $ sudo system-config-printer
```

(Once you do this in the below instructions, you are done. At this point the GUI for the HP 1018 printer settings will open automatically, and you can look through them to make sure they are as you want them. Click on the button in the GUI for setting this printer as the default. All the rest of the settings should be fine.)

```

INSTALLING LASER JET 1018 IN UBUNTU
------------
    Install build-essential FIRST:
	$ sudo apt-get install build-essential
	$ wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
	$ tar zxf foo2zjs.tar.gz
	$ cd foo2zjs
	$ sudo make uninstall
	$ make
	$ ./getweb 1018
	$ sudo make install install-hotplug cups

	For 7.10 and later users:
	    $ sudo system-config-printer

(Ignore the rest if you are using Gutsy or Hardy)

	For 5.10/6.06/6.10/7.04 users:
	    $ sudo gnome-cups-manager
	    [configure ColorMode = Color if a color printer]
	    $ sudo make cups

	    Ubuntu has a bug in gnome-cups-manager with Color, so you must
	    restart cups.  No other distro has this bug.

    If that doesn't work, then fire up:
	$ firefox http://localhost:631

    And click on:
	Printers -> Set Printer Options -> Color Mode -> Color
    Then click on:
	Set Printer Options
```

Thanks for this!

 ..... I'd like to click the 'thanks' button but it seems to have disappeared ..... (problems with the forum web site?)

---

