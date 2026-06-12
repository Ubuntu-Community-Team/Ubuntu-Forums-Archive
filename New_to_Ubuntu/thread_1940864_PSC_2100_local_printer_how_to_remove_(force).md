---
title: "PSC_2100 local printer how to remove (force)"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by riverupdude on 2012-03-14
I am running onieric (11.10), has been a learning process(Major Newbie to Linux), in attempt to get all the features I needed working, I found I needed to install HPLIP multifuntion package for my HP PSC printer, that worked !

Then installed XSANE, that worked !  The other day, I went to scan, found that HPAIO problem, removed (apt-get remove xsane) and reinstalled and that worked again. 

But now, I am getting a BACKEND PROBLEM for my printer.

I have at present , removed all these package and wish to get back to a CLEAN printer definitions across the system , include /var, /usr/,etc.   I was tempted to clear out /etc/printcap, but have not, wish to consult first here.

Since this is a "local" USB printer, I tried to "delete/remove printer" via the SYSTEM TOOLS--> SYSTEM SETTINGS--> PRINTERS, however  the "+ / -" buttons do NOT allow me to add or deltete the local printer.


How can I get a clean slate and redefine the printer ???  eg: like out of the box.


Then I plan to reinstall the forementioned packages.


If  I am wrong in my assumptions (which I might be) your advice is appreciated ...very much !

Again, the printer admin screen is not providing me ANY add /remove, only able to see jobs are "HELD", that is a step up from the "stopping job because the scheduler could not execute the backend" message I was getting.

thanks,

Mark):P

---

### Post by tbhatia4 on 2012-03-14
> **riverupdude said:**
> I am running onieric (11.10), has been a learning process(Major Newbie to Linux), in attempt to get all the features I needed working, I found I needed to install HPLIP multifuntion package for my HP PSC printer, that worked !

Then installed XSANE, that worked !  The other day, I went to scan, found that HPAIO problem, removed (apt-get remove xsane) and reinstalled and that worked again. 

But now, I am getting a BACKEND PROBLEM for my printer.

I have at present , removed all these package and wish to get back to a CLEAN printer definitions across the system , include /var, /usr/,etc.   I was tempted to clear out /etc/printcap, but have not, wish to consult first here.

Since this is a "local" USB printer, I tried to "delete/remove printer" via the SYSTEM TOOLS--> SYSTEM SETTINGS--> PRINTERS, however  the "+ / -" buttons do NOT allow me to add or deltete the local printer.


How can I get a clean slate and redefine the printer ???  eg: like out of the box.


Then I plan to reinstall the forementioned packages.


If  I am wrong in my assumptions (which I might be) your advice is appreciated ...very much !

Again, the printer admin screen is not providing me ANY add /remove, only able to see jobs are "HELD", that is a step up from the "stopping job because the scheduler could not execute the backend" message I was getting.

thanks,

Mark):P

remove packages using synaptic package manager
just locate the names of the printer in the package and mark for complete removal

---

### Post by riverupdude on 2012-03-15
I was able to "delete/remove" the printer via the "[COLOR=Blue]lpadmin[/COLOR]" command. Right or wrong, that was my goal here, BUT I am wondering why the "+/-"  Is not allowing me to ADD or REMOVE a printer, is this the normal GUI ?

[COLOR=Blue]root@riverupdude-laptop:~# lpadmin -p PSC_2100   -x PSC_2100
root@riverupdude-laptop:~# lpstat -a
lpstat: No destinations added.
[/COLOR]
There are no printer classes defined...
[COLOR=Blue]root@riverupdude-laptop:~# lpstat -c
lpstat: No destinations added.[/COLOR]

Here is a list of "synaptic packages" as you suggested;
[COLOR=Blue]root@riverupdude-laptop:~# dpkg --list|grep -i synaptic
ii  synaptic                                      0.75.2ubuntu8                              Graphical package manager
ii  xserver-xorg-input-synaptics                  1.4.1-1ubuntu2                             Synaptics TouchPad driver for X.Org server

[/COLOR]Here is a list of packages that include "hp";
[COLOR=Blue]root@riverupdude-laptop:~# dpkg --list|grep -i hp
ii  adobe-flashplugin                         11.1.102.63-0oneiric1              Adobe Flash Player plugin version 11
ii  gir1.2-launchpad-integration-3.0              0.1.54                            library for launchpad integration (gir files)
ii  hpijs                                         3.11.7-1ubuntu3.1                          HP Linux Printing and Imaging - gs IJS driver (hpijs)
rc  hplip                                         3.11.7-1ubuntu3.1                          HP Linux Printing and Imaging System (HPLIP)
ii  hplip-cups                                    3.11.7-1ubuntu3.1                          HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  hplip-data                                    3.11.7-1ubuntu3.1                          HP Linux Printing and Imaging - data files
ii  launchpad-integration                         0.1.54                                     launchpad integration
ii  libapache2-mod-php5                           5.3.6-13ubuntu3.6                          server-side, HTML-embedded scripting language (Apache 2 module)
ii  libhpmud0                                     3.11.7-1ubuntu3.1                          HP Multi-Point Transport Driver (hpmud) run-time libraries
ii  liblaunchpad-integration-3.0-1                0.1.54                                     library for launchpad integration
ii  liblaunchpad-integration-common               0.1.54                                     library for launchpad integration common data
ii  liblaunchpad-integration1                     0.1.54                                     library for launchpad integration
ii  liblaunchpad-integration1.0-cil               0.1.54                                     CLI bindings for liblaunchpad-integration
rc  liblpint-bonobo0                              0.1.51                                     library for launchpad integration
ii  libpathplan4                                  2.26.3-5ubuntu4                            rich set of graph drawing tools - pathplan library
rc  libsane-hpaio                                 3.11.7-1ubuntu3.1                          HP SANE backend for multi-function peripherals
ii  php5-cli                                      5.3.6-13ubuntu3.6                          command-line interpreter for the php5 scripting language
ii  php5-common                                   5.3.6-13ubuntu3.6                          Common files for packages built from the php5 source
ii  pxljr                                         1.3-0ubuntu2                               Driver for HP's Color LaserJet 35xx/36xx color laser printers
ii  python-launchpad-integration                  0.1.54                                     library for launchpad integration
ii  python-launchpadlib                           1.9.8-2ubuntu0.1                           Launchpad web services client library
ii  xserver-xorg-input-synaptics                  1.4.1-1ubuntu2                             Synaptics TouchPad driver for X.Org server

[/COLOR]I was trying to see what services are running;  BUT I Don't know how to interpret this;

services --status-all
root@riverupdude-laptop:~# service --status-all|more
[COLOR=Blue] [ ? ]  acpi-support
 [ ? ]  acpid
 [ ? ]  alsa-restore
 [ ? ]  alsa-store
 [ ? ]  anacron
 [ + ]  apache2
 [ + ]  apparmor
 [ ? ]  apport
 [ ? ]  atd
 [ ? ]  atop
 [ ? ]  avahi-daemon
 [ ? ]  binfmt-support
 [ + ]  bluetooth
 [ - ]  bootlogd
 [ - ]  brltty
 [ ? ]  console-setup
 [ ? ]  cron
 [ ? ]  cups
 [ ? ]  dbus
 [ ? ]  dmesg
 [ + ]  dmucs
 [ ? ]  dns-clean
 [ ? ]  ecryptfs-utils-restore
 [ ? ]  ecryptfs-utils-save
 [ - ]  fancontrol
 [ ? ]  friendly-recovery
 [ ? ]  gdm[/COLOR]

[COLOR=Blue][COLOR=Black]GOOD NEWS !
Just now, I plugged my printer in and it AUTO configured.....let me see if it works !

Yep ...Botta BING !

It works now....in spite of HPLIP not being installed.  I think that is for the multi-funtion (eg: scanner) HAL part.  [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]https://help.ubuntu.com/community/HpAllInOne

[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]
Still not sure why the GDE doesn't allow me to ADD/Remove printers, etc..... Apparently 11.10 (Oneiric) is much different than previous versions.

[/COLOR][/COLOR]
[COLOR=Blue][COLOR=Black]



Thank you for your attention to my requestI, 
God Bless
[/COLOR]
[/COLOR]

---

