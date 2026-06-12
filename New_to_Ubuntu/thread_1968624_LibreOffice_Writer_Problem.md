---
title: "LibreOffice Writer Problem"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by edwardLS on 2012-04-29
Just update, Clean install, from 10.04 LTS to 12.04 LTS.  Disappointed that OpenOffice was not included.  In any case, attempting to use LibreOffice Writer was extremely frustrating and I still have not accomplished what I need to accomplish.

When I open LibreOffice Writer, click on File -> New -> Labels the program responds by closing.  When I attempt to restart I have to Recover the document.  Have restarted Ubuntu and Writer several times.  It seems on my system that the problem is 100% consistent.

Are other experiencing this same problem?  It seems that all other items under the File -> New menu work properly.

---

### Post by clive littlewood on 2012-04-29
Hi

This is a bug within Libre Office Writer.

If you report the bug you will see it is already reported.

So hopefully a resolve soon.

Clive

---

### Post by r-senior on 2012-04-29
As a workaround, you might try gLabels. Nice little program for label printing. Can take a feed of addresses from a simple text file.

---

### Post by keithpeter on 2012-04-29
> **edwardLS said:**
> Just update, Clean install, from 10.04 LTS to 12.04 LTS.  Disappointed that OpenOffice was not included.  In any case, attempting to use LibreOffice Writer was extremely frustrating and I still have not accomplished what I need to accomplish.

+1 for glabels

I have taken the *drastic* step on *one* of my machines of uninstalling LO and [installing OpenOffice 3.3.0]("http://www.unixmen.com/oracles-openofficeorg-330-is-released-with-installation-instructions-for-ubuntu-fedora-centos-debian-linuxmint/") from the Apache Foundation openoffice.org web site. It works ok, but you don't get the desktop integration (the file open and save as dialog boxes are missing some features, the application looks a bit fugly &c).

*This step is only recommended if you are confident with the command line and understand how to use apt-get and dpkg to install debs and remove debs and packages.*

On the other machine, I am using LO as much as possible to help with bug fixing. I suspect it is 'one step back before a great leap forward' for LibreOffice as they confront the legacy code. My resolution is to post as many bugs on LO as I can because I want it to get better.

**Exercise for the skeptical reader**: Open LibreOffice Impress, and create a new presentation. Select Insert | Comment from the LO menu. Watch what happens.

---

### Post by edwardLS on 2012-05-18
I now have the Labels working as desired in LibreOffice.  My solution, it it is in fact a solution is - I installed LibreOffice-Base.  Labels now works fine.

---

