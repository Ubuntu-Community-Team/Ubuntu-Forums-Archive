---
title: "Install Brother DCP-117C on Ubuntu 9.04 Jaunty"
date: 2009-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by ramm400 on 2009-04-23
Printer:

Step 1:
Open Terminal by selecting Applications -- Terminal from the task bar. 

Step 2:
Type or Copy & Paste the following into Terminal and press enter: 
"sudo apt-get install tcsh"

Step 3:
From the task bar go to: System -- Administration -- Printing, select the printer from here if you have already tried to install it and delete it.

Step 4:
Download [THIS]("http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb") and [THIS]("http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC210C-1.0.2-3.i386.deb") and make sure you save them to your desktop.

Step 5:
Type or Copy & Paste the following into Terminal:
"cd Desktop"

Step 6:
Create the lpd directory. In terminal Type or Copy & Paste the following command:
"sudo mkdir /var/spool/lpd"

Step 7:
Install the LPR Driver. In terminal Type or Copy & Paste the following command:
"sudo dpkg -i --force-all mfc210clpr-1.0.2-1.i386.deb"

Step 8:
Create the model directory. In terminal Type or Copy & Paste the following command:
"sudo mkdir /usr/share/cups/model"

Step 9:
Now to install the CUPS wrapper driver. In terminal Type or Copy & Paste the following command:
sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb

Step 10:
From the task bar go to: System -- Administration -- Printing, select your printer and click Print Test Page. Hopefully it should work. 
PM me if it doesn't work and I will try to help.

---

