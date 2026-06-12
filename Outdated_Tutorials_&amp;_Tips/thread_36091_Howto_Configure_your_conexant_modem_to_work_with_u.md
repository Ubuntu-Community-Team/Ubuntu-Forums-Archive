---
title: "Howto: Configure your conexant modem to work with ubuntu"
date: 2005-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by de4th on 2005-05-21
All you have to do is to download linux headers for your kernel. Open synaptic, search for linux-headers-(kernel version), check and aply it!

Now go to [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) and download hsfmodem_(version)full_i386.deb. Open a console go to the directory where you downloaded the file, type:
"sudo dpkg -i hsfmodem_(version)i386.deb" (withoun the "") and press enter on questions.

After all you will have your modem configured on your system and you can find it in /dev/modem!

Have fun ;)

PS. This note from driver's site:
# a free version (limited to 14.4Kbps data), available at no cost. Please use it to test if your hardware is compatible.
# a full version (with 56K and FAX), available for a modest price.

---

### Post by FreeEagle on 2005-05-21
good job...


Regards,
FreeEagle

---

### Post by Jad on 2005-05-22
Please note a free version (limited to 14.4Kbps data)

---

### Post by eagleseye on 2005-10-14
It seems, for example the Unofficall Ubuntu guide, assumes you can access the internet using Ubuntu, for me that wasn't the case.  I had to download the driver from Linuxant on a Windows based machine and save it to a floppy.

The instructions for installing the driver Linuxant provided didn't work for a Debain file.  To shorten the story here is what I did.

Go to terminal, type in "cd /media/floppy0/"  hit enter.  Then add to the next line seen "sudo dpkg -i hcfpci~1.deb" both commmands without quotation marks.  With a sudo command you will have to enter your password.  Bam, the A driver started clicking and the driver loaded asking for some additional information.  Of course now I have to figure out how to see if it is communicationg with the OS.

Hope this  helps.

---

### Post by caps on 2006-06-07
works on Dapper 2.6.15.23

-James DeLong

---

### Post by DeKreonD on 2006-08-20
It's even easier: d/l the files to usbdrive, unzip the .deb file. Attach usb drive to ubuntu system.
The system will recognize it & put an icon on the desktop. Double click to open (with nautilus). 
Double click the .deb package and it will open & install automatically. You'll have to provide your admin password, but you'll be prompted for it.
There's a couple of questions that have to be answered (country, for one) by hitting enter & accepting the defaults.
Here's the trick: there's a TERMINAL option inside the .deb installer that ran when you double clicked on the package. Click that, and a terminal window opens that lets you respond to the prompts.
This is all *much* easier and quicker to do than describe - just try it. No need to use cryptic shell commands at any time.
=D> 

> **eagleseye said:**
> It seems, for example the Unofficall Ubuntu guide, assumes you can access the internet using Ubuntu, for me that wasn't the case.  I had to download the driver from Linuxant on a Windows based machine and save it to a floppy.

The instructions for installing the driver Linuxant provided didn't work for a Debain file.  To shorten the story here is what I did.

Go to terminal, type in "cd /media/floppy0/"  hit enter.  Then add to the next line seen "sudo dpkg -i hcfpci~1.deb" both commmands without quotation marks.  With a sudo command you will have to enter your password.  Bam, the A driver started clicking and the driver loaded asking for some additional information.  Of course now I have to figure out how to see if it is communicationg with the OS.

Hope this  helps.

---

### Post by indie56 on 2006-08-20
I have downloaded my modem file intel-v92ham-453.tgz.
Can some body give me how to install this file. It is Ambient Technologies contollerless modem.

---

### Post by bimodh on 2009-06-01
> **de4th said:**
> All you have to do is to download linux headers for your kernel. Open synaptic, search for linux-headers-(kernel version), check and aply it!

Now go to [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) and download hsfmodem_(version)full_i386.deb. Open a console go to the directory where you downloaded the file, type:
"sudo dpkg -i hsfmodem_(version)i386.deb" (withoun the "") and press enter on questions.

After all you will have your modem configured on your system and you can find it in /dev/modem!

Have fun ;)

PS. This note from driver's site:
# a free version (limited to 14.4Kbps data), available at no cost. Please use it to test if your hardware is compatible.
# a full version (with 56K and FAX), available for a modest price.
I am new to ubuntu. and when i try to connect to my dial up connection, it shows a message cannot open modem. What should i do?

---

### Post by east375 on 2010-05-19
This driver didn't work with my Conexant modem (Acer Aspire 7720G laptop). I tried different versions but all I did get is the conflict with standard ALSA sound driver.
But I used linmodem drivers on Redhat in past (on different PC) and it didn't annoy about money for extra kilobits. You may use your modem on Windows for free but you should pay to use it on linux. This is a kind of stupid idea.

---

