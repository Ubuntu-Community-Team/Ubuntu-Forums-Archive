---
title: "Download, extract and install???"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by ctdahle on 2012-08-16
I'm sure this must be covered somewhere and must be a very basic, but I have no idea how to do this.

I am running 10.04 "Lucid"

I  am attempting to set up a new printer. It is a "Canon Color imageCLASS  MF8380Cdw" multifunction color laser printer/scanner/fax/copier.

I  first attempted to install the printer by using the "add printer"  dialog under the System-->Administration-->Printing tab.

I  told the dialog that I wanted to install a network printer and it did  identify the printer which is hard wired to my wireless router and is  already operational from my wife's windows computer.

Continuing  through the dialog, my particular printer was not listed under Canon  printers and using the driver search dialog returned no joy.

I ran a google search for  "canon mf8380cdw linux", I found that canon does have a driver for this printer : Linux_UFRII_PrinterDriver_V250_us_EN.tar.gz

I downloaded this file from
[http://usa.canon.com/cusa/consumer/products/printers_multifunction/color_laser_multifunction/color_imageclass_mf8380cdw?selectedName=DriversAndSoftware](http://usa.canon.com/cusa/consumer/products/printers_multifunction/color_laser_multifunction/color_imageclass_mf8380cdw?selectedName=DriversAndSoftware)
and saved it on the desktop.

I  extracted the file, and buried within a readme file I found a  specification for a postscript printer description file (PPD). So I  chose "provide ppd" and then navigated through the extracted files to  the specified file "CNCPSMF8300CZS.PPD". 

Selecting this file allowed me to move through the rest of the dialog until I received the following message:

"Missing driver"
"Printer  'Canon-MF8300C' requires the 'pstoufr2cpca' program but it is not  currently installed.  Please install it before using this printer."

So, going back to the extracted files, I do see this program, but I have no idea how to install it.

I  am pretty certain that I am going about this all wrong, that what I  need to do is probably run something from a shell prompt that will  install the printer driver and the needed PPD file.

Obviously I  would be grateful if someone would just tell me, step by step, what to  do, but I would be even more grateful if someone would point me at an  indepth article that actually explains what is required.

I've been using Ubuntu for 3 years now, but because Canonical has made it so darn easy, I still really don't grok Linux.

---

### Post by unevenflow on 2012-08-16
OK 
A. remove printer from printer settings 
B. in the extracted folder you should find cndrvcups-ufr2-uk_2.50-1_i386.deb right click it and open with software center if this doesn't work right click it again and move it to home folder the in terminal type
**sudo dpkg -i cndrvcups-ufr2-uk_2.50-1_i386.deb**
C.if you succeed open printer settings as you did before and when it'll ask for PPD file navigate to usr/share/ppd/ and choose the ppd file named similar to your model
Hope that helps.

---

### Post by ctdahle on 2012-08-17
Thank you sir, that was a great help. The actual steps I needed to take ended up slightly different, but without your help I did not know what to try.

Here's what I ended up doing:

There were two "CUPS" files in the extracted .deb directory, one ..."cups-common_"....etc, and the other ..."cups-ufr2_us_"...etc (us instead of uk).

Right clicking did not give me a choice of "software center" but did give me  "open with GDebi package installer".

I took a gamble...and it didn't work! I got an unsatisfied dependency message, but it was clear from the message that I needed to install the ..."common"...file before I installed the ..."ufr2"...file. So I backed out and tried it that way.

GDebi informed me that the installation was successful for both files, so I ran the add printer routine again. My printer was quickly identified and the program automatically began a search for drivers, then prompted me to print a test page, which was sitting in the output tray by the time I made it from my cave in the garage to the printer in the house.

Happiness reigns.

Thanks again!

---

