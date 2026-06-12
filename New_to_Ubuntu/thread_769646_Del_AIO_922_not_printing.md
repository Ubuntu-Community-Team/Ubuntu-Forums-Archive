---
title: "Del AIO 922 not printing"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by ngutman on 2008-04-26
I have a dual boot, WinXP and Ubuntu computer.
I connected to it a Dell AIO 922 printer. It works fine with WinXP.
I added the printer in Ubuntu but don't seem to find a driver for it. Could this be the reason that it will not even print a test page?
Where can I find a driver for it?
Thanks,
Nathan

---

### Post by TransitMan on 2008-04-26
Try this link here - [http://ubuntuforums.org/showpost.php?p=3023609&postcount=7](http://ubuntuforums.org/showpost.php?p=3023609&postcount=7)

It should give the help you need.

---

### Post by ngutman on 2008-04-27
The link to [www.elinuxstop.com](www.elinuxstop.com) to get the deb files is dead.
Nathan

---

### Post by TransitMan on 2008-04-27
I uploaded the drivers to an off-site that I use to send large files. 
Download and follow the directions after you gunzip it.

[http://www.sendspace.com/file/tvjl27](http://www.sendspace.com/file/tvjl27)

Hope this helps.

---

### Post by ngutman on 2008-04-27
I am really new to Linux and Ubuntu.
I downloaded and extracted the files. Double clicked on the deb file and the Package Installer came up and "installed?" both packages.
Went to [http://localhost:631](http://localhost:631) and followed instructions to add a new printer and gave the usr location.
When tried to print I see that the printer is processing a file but nothing happens.
Where from/how/when should execute the dgtlmoon command?
When I enter it in Terminal I get:
bash: dgtlmoon@seven:/usr/share/cups/model$: No such file or directory

I hate to bother you but can you give step-by-step instructions to a real newbie. I will be eternally greatfull.
Nathan

---

### Post by TransitMan on 2008-04-27
Hang on, I got to get back into Ubuntu as I am using Xubuntu and the directions would be different.

---

### Post by TransitMan on 2008-04-27
In Ubuntu, go to System -> Administration -> Printing.
Once the Printer Configuration opens click on New Printer -> Click on the Dell/Lexmark printer listed -> click forward -> then scroll down to Lexmark then forward -> scroll to the bottom and click on Z600 -> click on forward -> then click on APPLY.
This will bring you back to the Printer Configuration panel.
Highlight the installed printer, make sure your Dell is turned on and the click on Print Test Page.
Once the test page has printed, close out of the Prionter Configuration and life will be good.

Note, there will be a listing for PDF in the Local Printers, leave it there. Any other printer listed besides what you just installed remove.

Let me know how it goes.

---

### Post by Mogurijin on 2008-04-28
Any chance that there are 64 bit versions of these drivers?

---

### Post by ngutman on 2008-04-28
No joy...
Followed instructions.
New printer was correctly listed as:
Dell Photo AIO 922 USB #1.
Found the Z600
Back in the Printer Configuration shows:
Make and Model Lexmark Z600 V1.0-1
Printer state - idle
This is the default printer.
Clicked "Print Test Page", got "Submitted as Job" clicked OK.
"Printer Test Page" changes to "Cancell Tests".
Waited 15 minutes and nothing is happening so I wonder if there is something else that I might be missing.

BTW - I succeeded to install a networked printer which is working fine but I didn't make it the default printer. Why do you suggest to remove any other printers? Can't Ubuntu deal with more than one printer installed?

As always thank you for holding my hand this and helping.
Nathan


> **TransitMan said:**
> In Ubuntu, go to System -> Administration -> Printing.
Once the Printer Configuration opens click on New Printer -> Click on the Dell/Lexmark printer listed -> click forward -> then scroll down to Lexmark then forward -> scroll to the bottom and click on Z600 -> click on forward -> then click on APPLY.
This will bring you back to the Printer Configuration panel.
Highlight the installed printer, make sure your Dell is turned on and the click on Print Test Page.
Once the test page has printed, close out of the Prionter Configuration and life will be good.

Note, there will be a listing for PDF in the Local Printers, leave it there. Any other printer listed besides what you just installed remove.

Let me know how it goes.

---

### Post by TransitMan on 2008-04-28
My suggestion to remove other printers associated with the Dell is so there would be no confusion over what was indeed installed. Further, any printer listed that you no longer have, use or not connected helps keep things clear in the Printer Configuration settings.

As for it not working, don't know. I scoured the site here for the answers you have posed.

---

### Post by TransitMan on 2008-04-28
> **Mogurijin said:**
> Any chance that there are 64 bit versions of these drivers?

Since I do not use 64-bit software, I would not know.

I would suggest you go to OpenPrinting - The Linux Foundation located here - [http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting) for answers to your question.

---

### Post by ngutman on 2008-04-29
I have no other printers associated with Dell. The other printer is an Epson Stylus Color 600 accessed via a network connection.

What baffles me is that the Dell works on your computer but not on mine so I wonder what is the difference between the two.

Thank you again for your continuing assistance.
Nathan

---

### Post by Sef on 2008-04-29
> I would suggest you go to OpenPrinting - The Linux Foundation located here - [http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting) for answers to your question. 

Here is OpenPrinting's take on [your printer]("http://openprinting.org/show_printer.cgi?recnum=Dell-AIO_Printer_A920").

---

### Post by TransitMan on 2008-04-29
> **Sef said:**
> Here is OpenPrinting's take on [your printer]("http://openprinting.org/show_printer.cgi?recnum=Dell-AIO_Printer_A920").

Thanks Sef for that link in OpenPrinting.

I am thinking the OP is having issues related to the CUPS install. I wonder if re-installing and the trying a re-association would work?

---

### Post by Mogurijin on 2008-04-30
What got me interested in this post was that the 922 is listed as a "paperweight" on OpenPrinting. Sorry about intruding on your thread ngutman. I don't know much about printers in Linux, but OpenPrinting does list the 920 as "Perfect" and I think it has instructions. I'd check it out ;)

---

### Post by trksh22 on 2008-09-30
Has anyone been able to get the 922 to work with Hardy? I do a lot of printing and would hate to not be able to use my printer. I only print, the other functions don't really matter.

---

### Post by brentavius on 2010-04-02
I am new to Ubuntu and trying to figure out how to install my Dell AIO 922.  Can't find the drivers.  Ran across this thread and tried to follow the directions, but I can't find the Lexmark Z600 in the printer database.  Can't find drivers on the internet.  My printer installation CD only has Windows installation files.  Striking out here from pretty much every angle!

I noticed the age of this thread, and I wonder if my (presumably) newer version of Ubuntu has discontinued this driver.  Obviously, I can't convert if I can't install my printer. . . .what can I do?  Any suggestions?

> **TransitMan said:**
> In Ubuntu, go to System -> Administration -> Printing.
Once the Printer Configuration opens click on New Printer -> Click on the Dell/Lexmark printer listed -> click forward -> then scroll down to Lexmark then forward -> scroll to the bottom and click on Z600 -> click on forward -> then click on APPLY.
This will bring you back to the Printer Configuration panel.
Highlight the installed printer, make sure your Dell is turned on and the click on Print Test Page.
Once the test page has printed, close out of the Prionter Configuration and life will be good.

Note, there will be a listing for PDF in the Local Printers, leave it there. Any other printer listed besides what you just installed remove.

Let me know how it goes.

---

