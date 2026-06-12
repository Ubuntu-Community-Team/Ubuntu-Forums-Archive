---
title: "Setting up networked Brother MFC5840CN on Dapper Drake"
date: 2006-09-13
forum: Outdated Tutorials &amp; Tips
---

### Post by tonywhelan on 2006-09-13
I'm a newcomer to Linux. But thought I'd share my success in getting a Brother MFC5840CN working on Ubuntu 6 (Dapper Drake).

We have a Brother MFC5840CN printer/fax/scanner with a fixed IP address (10.0.0.1 in my case) connected via ethernet cable to a router. We print to it from a couple of Windows machines already. I wanted to be able to print from my new Ubuntu box. This post deals ONLY with setting up the print function. I have yet to tackle the fax function, and I doubt that scanning will be an option at all, but that's for another day.

The things that made the difference between success and failure were tips from people in various places including these forums (fora?). But I haven't seen them all put together in one place, so here's a quick run through of what worked for me:

1. For the MFC5840CN there are two downloads required from Brother:
- the LPR driver [here]("http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc5840cnlpr-1.0.2-1.i386.deb")
and
the CUPS wrapper [here]("http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc5840cn_1.0.0-1_i386.deb")

Save them somewhere sensible on your machine (by default your machine may save things to the /tmp folder.
BUT DO NOT RUN THESE PACKAGES YET!

2. The Brother installers require the C Shell package "csh" so if it is not installed then you need to use Synaptic Package Manager (or apt-get) to install it.

3. The Brother scripts expect a file called /etc/init.d/cups but on Debian/Ubuntu this file is not present - it is called /etc/init.d/cupsys instead. So you should make a symbolic link to "point" from one to the other. The way I did it (may not be the simplest way but I'm new!) was to open Nautilus file manager as root, right-click on the file /etc/init.d/cupsys, select "Make Link". Then rename the resultant link to "cups".

4. The Brother script for the LPR driver also expects to find a folder /var/spool/lpd and it will bomb out if it doesn't find it. So create the lpd folder now, if it isn't already there.

5. Now you can install the LPR driver package. Open a terminal in the folder containing the package and execute 
dpkg -i --force-all mfc5840cnlpr-1.0.2-1.i386.deb 
Watch the terminal window for any error messages though.

6. If the LPR driver seemed to run ok, you can install the CUPS wrapper package. 
Open a terminal in the folder containing the package and execute 
dpkg -i --force-all cupswrappermfc5840cn_1.0.0-1_i386.deb
Again watch the terminal window for errors.

7. You will probably find now that your printer is installed, but as a USB device. So if your MFC is network-attached, you will need to change this. You can do it via the Gnome System/Administration/Printing menu. The connection tab should be set to "Network Printer", "Unix Printer (LPD)", and the "Host Name" box needs the IP address of the printer - eg 10.0.0.1 in my case. The "Queue name" I left blank.

7. If you prefer to use the browser-based print manager at [http://localhost:631](http://localhost:631)  it will eventually stop you in your tracks with a demand for a CUPS username and password. To get it to accept your username and password you must first have executed the following commands as root from a terminal window:

adduser cupsys shadow
/etc/init.d/cupsys restart

8. If in the process you need to know the location of the PPD file for the MFC5840, it will probably be in /etc/cups/ppd

9. Just to be on the safe side, you might want to restart CUPS: /etc/init.d/cupsys restart 

10. Try printing a document and hopefully be pleasantly surpised by seeing it work!

As I said at the start, I'm very new to Linux. So I can't offer advice. Just thought I'd share my experience.

---

### Post by nicolas.dh on 2006-10-04
What if, at step 6), lpr is not found. :) and it is normal....
$ lpr
bash: lpr : commande introuvable
$ lpq
bash: lpq : commande introuvable

Following the remaining steps, ubuntu seems
to be able to print on our MFC5840CN "networked"
but... acroread (7.0.8) attempts to print using lpr...
:idea: just make acroread to use 
  /usr/bin/lp -d YOURPRINTERNAME
(gimp also)

---

### Post by tonyr1988 on 2006-10-05
On my networked MFC5840CN, I can't get it to respond to any of my changes in print quality. I want it to have a lower quality, but it never changes. Any ideas?

---

