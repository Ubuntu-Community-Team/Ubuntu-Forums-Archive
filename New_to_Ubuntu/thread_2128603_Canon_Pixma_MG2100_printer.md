---
title: "Canon Pixma MG2100 printer"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by Autodave on 2013-03-23
Was running Ubuntu 10.4 on a friend's machine.  They got a Canon Pixma MG2100 printer.  Worked OK in B&W, but no color.  After looking around on here, found a reply to get a driver from Canon's website and install.  I did that and it worked great.  Little while later, upgraded the machine (since it was an older machine) to Xubuntu 12.04.  Clean install.  Installed printer, but only printed in B&W again.  Went back to old thread on here and followed same steps as before, but no luck: only B&W printing.  Any ideas?

---

### Post by Autodave on 2013-03-29
Anyone?

---

### Post by MythicManiac on 2013-03-29
Only thing I could think of is either an incorrectly installed driver or the driver is broken for whatever reason

---

### Post by kuifje09 on 2013-03-29
I doubt if the driver was correcly build for ubuntu 12.04. There are some changes each time again....
Also I think you cannot build it yourself ?  Then you could see the errors while building.
You might see some error in one of the logs?  kernel log maybe.

---

### Post by pdc on 2013-03-30
Dave: we have an MG2100 series printer and it works well in colour:

I would advise anyone to go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100392602.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100392602.html)

and download the MG2100 series [COLOR="#0000FF"]IJ Printer Driver Ver. 3.60 for Linux (debian Packagearchive)[/COLOR] that comes down as [COLOR="#008000"]cnijfilter-mg2100series-3.60-1-deb.tar.gz[/COLOR]

the commands to install would be:

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mg2100series-3.60-1-deb.tar.gz
cd cnijfilter-mg2100series-3.60-1-deb
./install.sh[/COLOR]

...........that should have you up and running............

and go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100392902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100392902.html)

for ScanGearMP to run the scanner side of things........

can you be sure you have the colour cartridge correctly loaded; and that it has adequate ink etc

we installed ink to monitor levels and the command I think was [COLOR="#FF0000"]sudo ink -p usb[/COLOR]

---

