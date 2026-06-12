---
title: "Installed but can't find - KTrafficAnalyzer"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Yumpin_Yimminie on 2008-09-29
My ISP has now put on a total limit per month.  I found software called "KtrafficAnalyzer" that offers band monitoring.  I am running Ubuntu 8.04 and am very shaky as far as knowledge of how to do anything other then surf the web and play Mahjong.

So I followed some google links and found this webpage:

[http://wiki.suselinuxsupport.de/wikka.php?wakka=KTrafficAnalyzer](http://wiki.suselinuxsupport.de/wikka.php?wakka=KTrafficAnalyzer)

and they have a download package available for Ubuntu 6.10 dated 14 April 2007.  So I clicked the download link.  A window came up and then another and it said I needed something like 10 other packages so I clicked OK or whatever is appropriate.  Then I think it did it's magic.  Showed a window with a bar graph showing loading 10 packages.  Gave me a message that KTrafficAnalyzer was loaded.  

I'm not having a success finding it on my computer or system though.  It's not on the taskbar.  I've tried looking for it in Applications the various submenus of Applications, System>preferences or System>administration.  

So I went to back to the webpage where I downloaded the package from.  Clicked the download link and it came up with a window that said, "already installed."

I'm looking for help on how to get this graphic bandwith usage meter running.  Or if it's running how to find out how much bandwidth I've used.

I am clueless.  Please help.

Thank you.

Have a Great Day,
Jim

---

### Post by Yumpin_Yimminie on 2008-09-30
Some more information.  I found a file that has the installation instructions for KTrafficAnalyzer by tracking the path of the installation stuff (great term...sorry).

I hoping someone can help me make heads and tales out of this.  I've taken the liberty of copying the instructions.  Here they are:

[COLOR="Blue"][SIZE="3"]#***************************************************************************
#                        CHANGELOG  -  description
#                             -------------------
#    title                : KTrafficAnalyzer
#    version              : 0.3.6
#    release-date         : 11.04.2007
#    copyright            : (C) 2003-2007 by Wolfgang 'Vir@s' Koller
#    email                : [email]viras@suselinuxsupport.de[/email]
#***************************************************************************

#***************************************************************************
#*                                                                         *
#*   This program is free software; you can redistribute it and/or modify  *
#*   it under the terms of the GNU General Public License as published by  *
#*   the Free Software Foundation; either version 2 of the License, or     *
#*   (at your option) any later version.                                   *
#*                                                                         *
#***************************************************************************

Requirements:
=============
- Tested under KDE 3.4.2 - it might work under other KDE versions as well (it
  most propably will), but I wont guarantee it.

Installation:
=============
A simple make should do the job:

shell> make

If no error occurs you will find the KTrafficAnalyzer binary in the current
directory. Now you can install it into your kde/bin folder by running:

shell> make install

NOTE: You have to be root in order to do that

Installation on systems with seperated libraries and include files:
===================================================================
Some systems (as e.g. Debian) store the libraries and the header files in
different directories. In order to compile on those systems you can use the
ADD_CFLAGS and ADD_LFLAGS environment variables. When you set them they are
simply prepended to the CFLAGS and LFLAGS variables.

So e.g. to add the directory /usr/lib/qt3/ to the library search path, just
run the following command:

shell> export ADD_LFLAGS=-L/usr/lib/qt3/

Similar you can do it with the header search path (adding /usr/include/qt3
in this example):

shell> export ADD_CFLAGS=-I/usr/include/qt3/

So with that it should be possible to compile on any system :).

Uninstall:
==========
Just run "make uninstall" in order to uninstall KTrafficAnalyzer:

shell> make uninstall

NOTE: You have to be root in order to do that

Troubleshooting:
================
If you get any command not found errors, make sure you have both KDE and QT
installed (including the devel packages). Also make sure both KDEDIR and
QTDIR are set (the script will tell y[/SIZE]ou anyway if it isn't set). They both
should point to the KDE / QT base dirs. So e.g.:

shell> export KDEDIR=/opt/kde3
shell> export QTDIR=/usr/lib/qt3

Usage:
======
Just start it, the rest is pretty self explanatory. In the settings dialog
you can set the colors for up and download and select the interface you want
to display the traffic for.
The stats dialog shows you a list of daily stats (the up-/downloads and totals for each
day). In addition you can get also view a list of monthly stats.
[/COLOR]

---

### Post by Yumpin_Yimminie on 2008-09-30
I think I've read that Ubuntu is a Debian derivative or offshoot or child something along those lines.  

I'm kind of at a huge loss here.  Very concerned about going over my bandwidth limit. 

I would appreciate it if someone could walk me through this.  

Thank you.

Have a Great Day,
Jim

---

### Post by Yumpin_Yimminie on 2008-09-30
Ah yes, one last thing that I think might help.

The folloiwng paths or actually the proper term might be files that were listed in details of the package installer are:

./
usr/
usr/share/
usr/share/doc/
usr/share/doc/ktrafficanalyzer/
usr/share/doc/ktrafficanalyzer/CHANGELOG
usr/share/doc/ktrafficanalyzer/INSTALL
usr/share/doc/ktrafficanalyzer/TODO
usr/share/doc/ktrafficanalyzer/GPL
usr/bin/
usr/bin/KTrafficAnalyzer
usr/bin/ktrafficanalyzer

Once again any help is appreciated.

Thank you.

Have a Great Day,
Jim

---

### Post by jerome1232 on 2008-09-30
From my understanding you downloaded a debian package correct (.deb)?

If that's the case try just running it from the command line

```
ktrafficanalyzer
```

---

### Post by UncleAlan on 2010-04-30
I have downloaded ktrafficanalyzer but dont know where. ! it is only showing up in the Download folder but says it is installed. It is not on the Installed software list and it isnt working. I cant even find a way of uninstalling it. I do need a programme to measure my broadband usage and this sound like one of the few that might work but how to do that is a total mystery. Its the only let down I have found for Ubuntu.
alan

---

