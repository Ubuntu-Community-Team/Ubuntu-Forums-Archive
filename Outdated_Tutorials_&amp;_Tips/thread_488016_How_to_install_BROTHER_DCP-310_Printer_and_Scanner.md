---
title: "How to install BROTHER DCP-310 Printer and Scanner"
date: 2007-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by inoxllor on 2007-06-29
** Tested on Ubuntu 7.04 Feisty Fawn x32**

To install the Printer (USB)
==================
I've managed to install my DCP310 printer using the guide provided here:
**[Brother Printer Driver Site]("http://solutions.brother.com/linux/en_us/index.html")**
*Download the LPR and the CUPS drivers for Debian*.

Also don't forget to install **CSH **via synaptics manager.

If cups asks for the Brother DCP-310CN ppd file you can download it here: [Brother PPD file]("http://ubuntuforums.org/attachment.php?attachmentid=32519&d=1179086574")

To Install the Scanner (USB)
===================
**sudo apt-get install xsane**

then
**lsusb**

in my case it retuns:
> Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 04f9:016b Brother Industries, Ltd
Bus 003 Device 002: ID 041e:401c Creative Technology, Ltd WebCam NX [PD1110]
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

so I enter this command
**sudo chmod 666 /proc/bus/usb/003/003**
*to give access to "Bus 003 Device 003" = Brother Printer, in my case. Don't forget to replace 003 and 003 with other numbers provided by the lsusb command in your system.*

then run **xsane** and you should get your scanner working. 
more info here:[http://welcome.solutions.brother.com/BSC/public/eu/pt/pt/model_top/colormfc/dcp310cn_eu.html?reg=eu&c=pt&lang=pt&prod=dcp310cn_eu]("http://welcome.solutions.brother.com/BSC/public/eu/pt/pt/model_top/colormfc/dcp310cn_eu.html?reg=eu&c=pt&lang=pt&prod=dcp310cn_eu")

---

### Post by scoultas on 2007-07-12
Thanks,  very useful!

Worth pointing out the following tips to anyone else following these instructions :

i) Must cd to the directory with the .deb file
II) Needed to create the lpd and DCP310CN directories in spool

which I found in the following posting:

[http://ubuntuforums.org/showthread.php?t=486675](http://ubuntuforums.org/showthread.php?t=486675)

---

### Post by snakra on 2007-09-01
Hello,

I've tried what you suggested.

I get a message saying that I already have the latest version of xsane installed.

When I send a test message to the printer, the printer display lights up to show that data is being received but then nothing happens.

Any suggestions gratefully received - I'm very much a beginner, so easy steps please!

It's a pity about the printer as I've got everything else working fine, even the screen digitiser works - but without the printer I have to keep going back to XP

Suresh

---

### Post by inoxllor on 2007-09-09
The problem is not in Xsane (scanner). 
I think its related to the printer drivers.

1) Run **Synaptics Manager** and search for "**CSH**", then install it;

2) Download and** install the LPR driver** from Brother:
_[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/dcp310cnlpr-1.0.2-1.i386.deb&lang=English_lpr]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/dcp310cnlpr-1.0.2-1.i386.deb&lang=English_lpr")_

3) Download and **install the CUPS driver**:
[U][http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperDCP310CN-1.0.2-3.i386.deb&lang=English_gpl]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperDCP310CN-1.0.2-3.i386.deb&lang=English_gpl")
[/U]
4) Open your browser and enter: "**[http://localhost:631](http://localhost:631)**"

5) Click on “**Manage Printers**” and confirm that the device name is listed there.
(If the device name is NOT listed there, click on "**Add Printer**" and install the driver following the on-screen instructions.)

6) The default port is USB. If you want to use a different port, click on “Modify Printer” and select the required printer port.

7) If you need the** PPD file** for the Brother DCP-310CN printer, grab it here: _[http://ubuntuforums.org/attachment.php?attachmentid=32519&d=1179086574]("http://ubuntuforums.org/attachment.php?attachmentid=32519&d=1179086574")_

---

### Post by snakra on 2007-09-10
Dear Inoxllor,

Thank you for your reply.  I did as follows:

1) Run Synaptics Manager and search for "CSH", then install it;
got message that csh 20060813-1 already installed

2) Download and install the LPR driver from Brother:
[http://www.brother.com/cgi-bin/agree...ng=English_lpr](http://www.brother.com/cgi-bin/agree...ng=English_lpr)
got message that driver already installed

3) Download and install the CUPS driver:
[http://www.brother.com/cgi-bin/agree...ng=English_gpl](http://www.brother.com/cgi-bin/agree...ng=English_gpl)
did this and installed cups driver

4) Open your browser and enter: "http://localhost:631"

5) Click on “Manage Printers” and confirm that the device name is listed there.
did this and device was listed and operational.  Did a test page and this printed fine.

Then went Applications>Graphics>XSANE and got messages:
No device available
on help
1) no device connected - it is!
2) device busy - it is not!
3) Permissions for device file do not allow you to use it - try as root
   HELP - how does one do this
4) Backend not loaded by SANE(man sane-dll)
5) Backend not configured correctly ( man sane - backend name)

Any ideas on how to get scanner to work?

Thanks

SN

---

### Post by inoxllor on 2007-09-10
So, now the printer is working fine but the scanner does not?

1) Don't forget the **lsusb** step

2) and the **sudo chmod 666 /proc/bus/usb/00x/00x**  step (please change the "00x" accordingly to your lsusb results, as in the example given on top of this thread)

3) If it still fails to scan, here is the link to get your scanner working: [http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html")
Notice that you should download the** brscan2 driver ver.0.2.3-0 (for Debian users)**

Good Luck. :D

---

### Post by snakra on 2007-09-11
Dear Inoxllor,

Many, many thanks for persisting with my problems.

The good news is that the scanner now works perfectly.  

I need to take a break, take breath and come back to get used to using the unfamiliar screens.  It now seems silly to think there were moments when I nearly gave up.

I had made a stupid, stupid assumption that when I downloaded the printer driver the scanner driver was included as for the process with Windows.  Your comment  as follows:

3) If it still fails to scan, here is the link to get your scanner working: [http://solutions.brother.com/linux/s...e_drivers.html](http://solutions.brother.com/linux/s...e_drivers.html)
Notice that you should download the brscan2 driver ver.0.2.3-0 (for Debian users)

was the first indication to me that there was a separate driver for the scanner.

How I missed this on the Brother solutions site I don't know - probably as the printer and scanner drivers are on separate locations.

If it helps other people I've identified the following steps which helped - I will not mention the many false starts

1) Download and install the LPR and Scanner drivers from the Brother solutions centre site - [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

2) Make suggested change: 
<For Ubuntu6.06 or later Users>
1.Open the file "/etc/udev/rules.d/45-libsane.rules" with an editor.
2.Add the following description to the file as below:
=================
#brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"
LABEL="libsane_rules_end"
=================
3.Restart the OS.

This is contained in the Brother site:
[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

do remember one needs sudo gedit rights for these changes

I hope this will help others to avoid my mistakes and save an awful lot of time and frustration

I do hope that I will now gain confidence in Ubuntu and slowly wean myself off XP Pro

Many thanks again

Sincerely

SN

:)

---

### Post by inoxllor on 2007-09-16
I am glad that the information posted here helped your path to the ubuntu side. :D

---

### Post by montedalua on 2007-10-23
Hi Everybody

I did all the sugestions my printer is recognized but it does not work.
test page is not printed, the printer shows the message " receiving data" print job number 19 but it does not print.
In Windows it does
Please can anybody help me?
I am a bigginner in Ubuntu but it has been hard to not have  printer to work with.
Montedalua

---

### Post by snakra on 2008-01-25
Hello,

I hope that by now you have already got your Brother printer working - but just in case you have not the following might help.

I'm no expert - rather a beginner - but as you will see above in this thread other people have helped me so I hope this little note will help you and anybody else.

My Brother DCP-310CN printer/scanner had been working fine until I upgraded yesterday from 7.04 to 7.10 to find exactly the symptoms you describe.

I found the following worked:

1 I re-installed the printer driver (the links are in earlier posts above); I got the message saying it is already installed but I re-installed anyway.

2 I re-installed the CUPS driver (links above); got no message to say it was already there so this seems to have been lost in the upgrade.

And, what do you think - the test page printed and all is well again!

Hope this helps


SN

---

