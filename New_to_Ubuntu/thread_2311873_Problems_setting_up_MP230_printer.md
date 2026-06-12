---
title: "Problems setting up MP230 printer"
date: 2016-01-30
forum: New to Ubuntu
---

### Post by jmamos1984 on 2016-01-30
I'm having difficulty setting up my MP230 printer on Ubuntu 14.04, 64-bit.

I downloaded and installed the drivers from manufacturer's site.  

cnijfilter-common_3.80-1_amd64.deb
scangearmp-mp230series-2.00-1-deb

Installing these was difficult (it required first downloading libtiff4), but I think that this part is done.  Here's my reason to think so:

$ dpkg -l | grep scangear
ii scangearmp-common    2.00-1    amd64    ScanGear MP for Linux.
ii scangearmp-mp230series    2.00-1    amd64    ScanGear MP for Linux.

$ dpkg -l | grep cni
ii cnijfilter-common        3.80-1    amd64    IJ Printer Driver for Linux.
ii cnijfilter-mp230series    3.80-1    amd64    IJ Printer Driver for Linux.

After this, the printer showed up (for example, System Settings -> Printers), and when I hit print, it goes to the queue.  However, it still doesn't print.  To sanity check physical issues like paper loading, I pressed the button on the printer that makes a copy of the item in the scanner &#8211; it has no difficulty with this.

Because it wasn't working, I went back a step and ran the ./install.sh scripts that came with the drivers.  (These didn't work the first time due to libtiff4.  Once I had libtiff4, I installed using dpkg.)  The install script for the scanner has no issues.  When I run it for cnijfilter, I get:

#=========================================================#
#  Register Printer
#=========================================================#
Next, register the printer to the computer.
Connect the printer,and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
> 
Searching for printers...
#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------
 0) Update
-----------------------------------------------------------
Could not detect the target printer.
-----------------------------------------------------------

At which point, I'm now in a loop until I just give up.

I wondered if my experiments had misconfigured something, so I deleted the printer (System Settings -> Printers -> right click).  Now, I can't even get the printer to show back up in the menu.

Any suggestions for what to try next?

----------- Update -------------

I solved the problem without really understanding how.  I moved on to working on getting other things to work - when I came back to working on the printer, it was plug-and-play.  Enough cords were moved and packages were installed that it wasn't necessarily just fixed due to power cycling.  I'm okay with not knowing exactly what fixed it.

---

