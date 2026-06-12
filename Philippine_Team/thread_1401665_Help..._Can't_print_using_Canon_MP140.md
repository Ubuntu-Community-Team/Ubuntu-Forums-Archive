---
title: "Help... Can't print using Canon MP140"
date: 2010-02-08
forum: Philippine Team
---

### Post by ramjitmyrtle on 2010-02-08
I followed all the threads concerning installing the drivers for the said printer but I still can't print. The only thing that I can do on it is to scan. Please help. Thanks. I also get CUPS error when using Print Self-Test Page and Clean Print Heads. Thanks again. Please Help.

---

### Post by ramjitmyrtle on 2010-02-08
MP145 is in Karmics database... just added a new printer then changed the printer to Pixma 150-CUPS... that's it... i can now print

---

### Post by wersdaluv on 2010-02-09
My MP150 works smoothly too :)

---

### Post by glezglez1 on 2010-02-21
[FONT=Verdana]Download files:
cnijfilter-common_2.80-1_i386.deb[/FONT][FONT=Verdana]
cnijfilter-mp140series_2.80-1_i386.deb[/FONT][FONT=Verdana]
scangearmp-common_1.10-1_i386.deb[/FONT][FONT=Verdana]
scangearmp-mp140series_1.10-1_i386.deb

from:[/FONT] [FONT=Verdana]
[http://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu-packages/gutsy/Canon-printing+scan/](http://ftp.akl.lt/Linux/Baltix/Baltix-Ubuntu-packages/gutsy/Canon-printing+scan/)[/FONT] [FONT=Verdana]

We'll first repackage the common .deb[/FONT] [FONT=Verdana]
$ dpkg-deb -x *cnijfilter-common_**2.80-1_i386.deb*
$ dpkg-deb --control [I]cnijfilter-common_3.00-1_i386.deb

[/I]$ cd DEBIAN
$ gedit control 

change [/FONT] [FONT=Verdana]*libcupsys2* to [I]libcups2

[/I]copy the entire[/FONT][FONT=Verdana] DEBIAN folder [/FONT][FONT=Verdana]into common folder

$ dpkg -b [/FONT][FONT=Verdana] common *cnijfilter-common_*[I]2.80-1_i386.deb

remove DEBIAN and common folfers

Do the same for [/I]*cnijfilter-mp140series_2.80*[I]-1_i386.deb

Install files.
[/I]*cnijfilter-common_*[I]2.80-1_i386.deb
[/I]*cnijfilter-mp140series_2.80**-1_i386.deb*
scangearmp-common_1.10-1_i386.deb[/FONT] [FONT=Verdana]
scangearmp-mp140series_1.10-1_i386.deb


Change owner and group:
#chown root /usr/lib/cups/filter/pstocanonij
#chgrp root /usr/lib/cups/filter/pstocanonij
#chown root /usr/lib/cups/backend/cnij_usb
#chgrp root /usr/lib/cups/backend/cnij_usb

Doing this solved my problem.[/FONT]

---

### Post by Script Warlock on 2010-02-21
pwede mo naman siguro gamitin ang driver na mp150 sa ubuntu.....

---

### Post by Vinnie V on 2010-04-13
Sweet! I love search. I had tried going to the manufacturers website to locate a solution, and killed a couple of hours trying different things. I searched the forum, and resolved in less than 5 minutes. Thanks again!

---

### Post by ben2talk on 2010-07-01
We'll first repackage the common .deb
$ dpkg-deb -x cnijfilter-common_2.80-1_i386.deb

**First error here!**
dpkg-deb -x cnijfilter-common_2.80-1_i386.deb
dpkg-deb: --extract needs a target directory

so I made a directory 'debian' and tried again:

dpkg-deb -x cnijfilter-common_2.80-1_i386.deb /home/ben/Desktop/debs/debian

Unfortunately, this only extracted a /usr directory (containing bin lib share folders) - what's the story here?

---

### Post by Miles Pennington on 2010-09-12
I tried a less elegant solution because I don't know anything about code. I went to  [http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download) and used the link there to install libcupsys2. After that I was able to install all four packages as normal and my MP140 is working.

Hope this helps.

---

### Post by lawra on 2011-08-02
I know this is an old thread but whatever

I can't get my 11.04 to work with this printer, I used the MP150 driver but it's not working and it's a bit complicated for me to use terminals 

Some help, guys :s ??

---

