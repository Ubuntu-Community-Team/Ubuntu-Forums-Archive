---
title: "Canon laser printer LBP 3010 - driver"
date: 2013-11-16
forum: New to Ubuntu
---

### Post by vedranboric on 2013-11-16
Hi,
can someone help me with detailed instructions on how to install driver for laser printer LBP 3010 on Lubuntu 13.10.
I'm total Linux noob. I would appreciate your help and understanding.
Best regards.

---

### Post by heir4c on 2013-11-16
Here the link to download the driver. Scroll to the bottom and click on "Accept & Download":
[http://www.canon-europe.com/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP3010.aspx?DLtcmuri=tcm:13-1060371&page=1&type=download](http://www.canon-europe.com/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP3010.aspx?DLtcmuri=tcm:13-1060371&page=1&type=download)
Than go to the Download folder and rightclick on the tar.gz file and choose to unpack (or something like that, I have no English version here).
Than you see a map with the name: Linux_CAPT_PrinterDriver_V260_uk_EN
Doubleclick on that and than you see 4 folders choose the 32bit or 64bit folder (depends on your hardware) and choose than inside that the "Debian' folder.
Now you see 2 .deb files. Doubleclick on the SECOND file to install the .deb.
Than you doubleclick on the FIRST one to install.
Go after installing the drivers to "SystemSettings" and there to printersettings/printermanager (something like that). Check if he is recognized and check the settings for the printer.
(I don't know where the Printersettings are in Lubuntu, I have at the moment not a Lubuntu install on my PC)

---

### Post by vedranboric on 2013-11-18
Without success. I need more detailed instructions about procedure steps after installing two .deb files.
I was also try to follow instruction [here]("http://ubuntuforums.org/showthread.php?t=1982917&p=11955525#post11955525") (by changing some inputs because of different printer), but without success.
Can someone help me, I would really like to have working printer on my Lubuntu installation.
Best regards.

---

### Post by heir4c on 2013-11-18
Now I have a Lubuntu on my Laptop. Look for "SystemTools>Printers"

---

### Post by vedranboric on 2013-11-19
I already found that option and tried several things to do (adding CAPT printer, entered several URI addresses, restart system...).
But printer never has "ready for print" status and it doesn't work.

---

### Post by vedranboric on 2013-11-21
Any help from  someone, or I should give up from having my printer working on Lubuntu?

---

