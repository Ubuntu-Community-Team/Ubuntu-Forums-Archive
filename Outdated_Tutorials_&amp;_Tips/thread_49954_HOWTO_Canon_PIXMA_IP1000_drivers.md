---
title: "HOWTO: Canon PIXMA IP1000 drivers"
date: 2005-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Boyzcha on 2005-07-18
This is driver for ip1000. 

[COLOR=DarkOrange]The HOWTO:[/COLOR]
[COLOR=DarkRed]1. Install required packages
Install alien with synaptic
Install libxml1 with synaptic (required later on to run canon's bjcups application)[/COLOR]

**2. Download Driver**
open terminal
cd to your preferred download directory
For ip1000:

$ wget [http://www.mafia.or.id/bjfilter/bjfilter-common-2.50-2.i386.rpm](http://www.mafia.or.id/bjfilter/bjfilter-common-2.50-2.i386.rpm)
$ wget [http://www.mafia.or.id/bjfilter/bjfilter-pixmaip1000-2.50-2.i386.rpm](http://www.mafia.or.id/bjfilter/bjfilter-pixmaip1000-2.50-2.i386.rpm)
$ wget [http://www.mafia.or.id/bjfilter/bjfilter-pixmaip1000-lprng-2.50-2.i386.rpm](http://www.mafia.or.id/bjfilter/bjfilter-pixmaip1000-lprng-2.50-2.i386.rpm)

**3. Convert .rpm to .deb**
$ sudo alien bjfilter-common-2.50-2.i386.rpm
$ sudo alien bjfilter-pixmaip1000-2.50-2.i386.rpm
$ sudo alien bjfilter-pixmaip1000-lprng-2.50-2.i386.rpm

**4. Install**
$ sudo dpkg -i <names of the 3 generated deb files>

**5.Edit .ppd file**
To allow printing quality options to be accessed through cups' printer properties you must edit as root the printer's ppd file.(This applies only to the ip1000.
$ sudo gedit /usr/share/cups/model/canonpixmaip1000.ppd
Add these lines:
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

You can also replace these lines:
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution
with:
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*CloseUI: *Resolution

Save the file

**6. Fix libs**

$sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
$sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
$sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1

(i don't know why i do this but otherwise the printer does not work)

**7. Restart Cups**
$ sudo killall cupsd
$ sudo cupsd

**8. Setup Printer**
-System>Administration>Printing>New Printer
-Choose Local or network printer and specify port or url, respectively
-Forward
Manufacturer>canon
Model> PIXMA IP1000 (depends on your printer)
Driver>Standard
-Apply
(if you can't find your printer choose:install driver>choose the ppd file you edited, reboot and try again to setup printer)

**9. Test**
Right Click on printer> properties>print test page

10. Setup on GIMP
-open an image to print
-file>print>Choose your printer name>setup printer:
Printer Model>PostScript level 2
command>lpr -P <your printer name> (PIXMA IP1000)
PPD File>browse at /usr/share/cups/model/ (mine is /usr/share/cups/model/canonpixmaip1000.ppd)
-OK
-Save Settings
-Print

Linux For All :-P I just try to help

---

### Post by deng on 2005-07-18
thx for the tips... its make me happy with it and now i can print all my document smoothly without changing my hdd (hdd with winxp) again and again.

p/s best jugak kamu punya tips ni ya... camtulah geng... hidup Open Source!

---

### Post by Cycha on 2005-07-18
nice guide man... thx a lot now i can use my printer ... u ar the best... \\:D/

---

### Post by bihe on 2005-08-13
at last ... it works.
thanx a lot

---

### Post by kebayan_it on 2005-09-19
Hi,

I've followed your tips, and success to install it.

However i came to this problem.

The TEST PRINT is Ok, but I can't print from any other application (Open Office, GIMP, Firefox etc).

The printer LED is blinking, but there is no output.

Checking at the PRINT JOBS, also nothing.

Pls help... thanx

---

### Post by nbcthreat on 2005-10-08
Same problem on a PIXMA iP4000. Test page prints, but not firefox.

---

### Post by Dareos on 2005-11-23
I've done this howto step-by-step, but printer doesn't work :confused:

---

### Post by madirajuananth on 2007-04-04
i found that the link provided takes me to a page where i can see an error message saying that the material for which i am searching for, is not in that page.please help me in some other easier & shorter way. thank you.

---

### Post by thefoolisme on 2007-04-04
Would you mind working on a driver for the Canon MF4150 laser printer?  :-)  Then I would be able to print from Linux.

---

### Post by madirajuananth on 2007-04-04
why canon mf4150 laser printer ,i have a canon pixma ip1000 printer only please help me in instaslling that.thank you for ur reply.

---

### Post by madirajuananth on 2007-04-05
can canon pixma ip1000 be installed in ubuntu  6.10 or not.:confused: please clarify my doubt.if so how.

---

### Post by minal on 2007-12-15
hello all,

can anybody plz provide sum othr link for .rpm pkgs for IP1000??
these ones r nt working..

Thanx in advance..

---

