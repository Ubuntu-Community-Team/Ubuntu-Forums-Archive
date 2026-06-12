---
title: "Canon Printers"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by johnwill on 2012-11-14
I have tried without success to connect my printer in Linux Ubuntu 12.04. (Canon MP610) and have at last given up and therefore still use Windows 7 for printing.
I have contacted Canon who were not helpful at all.
Is there anyway that one can connect a Canon Printer.
Thank you.

---

### Post by deadflowr on 2012-11-14
Did you try Canon-Asia or Canon-Australia?

Here's Canon-Australia:

[http://www.canon.com.au/Support-Services/Drivers-and-Downloads]("http://www.canon.com.au/Support-Services/Drivers-and-Downloads")


Pick debian package if available. When on the download page scroll down to the bottom(the download page is usually rather long) the download button will be near the bottom of the page.

---

### Post by pdc on 2012-11-14
Canon is an asian company initially ......

.....so if you google on 

" Canon Asia downloads" ......you get to their Singapore site that I find excellent............

[http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal)

you then select your device.....in your case a multi-functional inkjet..

....and you get to ....... series....and you select pixma.......

........and you select model number.....MP610........and you get to here

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MP610&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP610&menu=download&filter=0&tagname=g_os&g_os=Linux)

.......when you click on the linux button at the left .....

......Canon supply both rpm and deb packages.......

...........Ubuntu uses deb.........

so you need to install the [COLOR="SeaGreen"]COMMON PACKAGE[/COLOR] first .......

......by going here......

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100083403.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100083403.html)

and you will be downloading the [COLOR="Blue"]IJ Printer Driver Ver. 2.80 for Linux(debian Common package)
[/COLOR]
...it comes down as .......[COLOR="Green"]cnijfilter-common_2.80-1_i386.deb[/COLOR]

.....gdebi installer should offer to install as you click to download so I would let it do that for you .......

then go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100084001.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100084001.html)

and download [COLOR="Blue"]IJ Printer Driver Ver. 2.80 for Linux(debian Package for the MP610 series)[/COLOR]

.......it comes down as [COLOR="Green"]cnijfilter-mp610series_2.80-1_i386.deb[/COLOR]

......and install with gdebi installer

If you copy and paste the command below

> [COLOR="Red"]sudo dpkg -l | grep cnijfilter[/COLOR]

into a terminal, (and hit the enter key....)it should tell you the driver is installed

you don't tell us if you are using 32bit or 64bit..64bit may need a symbolic link to tell the driver to look in lib64..whereas it may be programmed to look only in lib

---

### Post by offgridguy on 2012-11-14
There have been threads here in the recent past regarding canon printers.
  You could try a thread search under canon printer, if you haven't already. :)

---

### Post by alphacrucis2 on 2012-11-14
It seems to vary a lot depending on the particular printer model. I have had no trouble getting the Canon image runner laser printers and PIXMA printers I have access to working on Linux. On the other hand I can't get an older Canon printer (MPC400) to work at all on Linux or even W7 though it works on XP.

---

### Post by johnwill on 2012-11-16
> **pdc said:**
> Canon is an asian company initially ......

.....so if you google on 

" Canon Asia downloads" ......you get to their Singapore site that I find excellent............

[http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal)

you then select your device.....in your case a multi-functional inkjet..

....and you get to ....... series....and you select pixma.......

........and you select model number.....MP610........and you get to here

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MP610&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP610&menu=download&filter=0&tagname=g_os&g_os=Linux)

.......when you click on the linux button at the left .....

......Canon supply both rpm and deb packages.......

...........Ubuntu uses deb.........

so you need to install the [COLOR="SeaGreen"]COMMON PACKAGE[/COLOR] first .......

......by going here......

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100083403.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100083403.html)

and you will be downloading the [COLOR="Blue"]IJ Printer Driver Ver. 2.80 for Linux(debian Common package)
[/COLOR]
...it comes down as .......[COLOR="Green"]cnijfilter-common_2.80-1_i386.deb[/COLOR]

.....gdebi installer should offer to install as you click to download so I would let it do that for you .......

then go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100084001.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100084001.html)

and download [COLOR="Blue"]IJ Printer Driver Ver. 2.80 for Linux(debian Package for the MP610 series)[/COLOR]

.......it comes down as [COLOR="Green"]cnijfilter-mp610series_2.80-1_i386.deb[/COLOR]

......and install with gdebi installer

If you copy and paste the command below



into a terminal, (and hit the enter key....)it should tell you the driver is installed

you don't tell us if you are using 32bit or 64bit..64bit may need a symbolic link to tell the driver to look in lib64..whereas it may be programmed to look only in lib
Hello Thank you for your detailed answer: I am useing a 64bit programme

---

### Post by pdc on 2012-11-16
1) if you install the drivers as advised;

2) then create symbolic links, so the system looks in your lib64; instead of looking in lib (which will not exist in your system);

(*the newer drivers from Canon have an* [COLOR="Magenta"]install.sh[/COLOR] *script; that looks to see if you need a debian or rpm package; and whether you have a 32bit or 64bit system, and manages accordingly........your driver is an earlier one, written for 32bit*..............)

.....so to create symbolic links, if you copy and paste the commands below into a terminal and hit the enter key; in a terminal, use the Menu/Edit/Paste from the top line, as it is easier than the terminal's keyboard shortcuts of shift+control+V

> [COLOR="Red"]sudo ln -s /usr/lib /usr/lib64[/COLOR]

> [COLOR="Red"]sudo ln -s /usr/local/lib /usr/local/lib64[/COLOR]

as advised in post #62 here

[http://ubuntuforums.org/showthread.php?t=1723101&page=7&highlight=canon](http://ubuntuforums.org/showthread.php?t=1723101&page=7&highlight=canon)

........all should now be good........let us know how it goes.....

---

### Post by BicyclerBoy on 2012-11-16
The Canon support is very good..there is source code & packages all over the place.
Unfortunately some are rpms or debs or 32bit & the install script has problems with *buntu changes or the source code had problems with libpopt multi-arch support etc.

As this is a beginners section..the PPA install is package managed. It is safe, it works with the rest of your distro & it is maintained.

Why not just add a PPA that just works:
[https://launchpad.net/~michael-gruz/+archive/canon-trunk](https://launchpad.net/~michael-gruz/+archive/canon-trunk)

driver versions 3.60 & 3.70 for 32 & 64bit..
Then install:
cnijfilter-mp610series
scangearmp-mp610series

These should pull in 2 other common packages..

---

