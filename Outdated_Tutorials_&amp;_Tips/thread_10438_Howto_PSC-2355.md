---
title: "Howto: PSC-2355"
date: 2005-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Allen S on 2005-01-07
This has been a problem in every distro that I have tried. I finally found a way to make it work without to much hassle.

The 1st thing that needs to be done is configure the scanner. To do this you'll need hpoj.

Open a terminal window and using a editor such as pico
sudo pico /etc/apt/sources.list
Uncomment the 2 lines for universe
Save file CTL O
Close pico CTL X

sudo apt-get update
sudo apt-get install hpoj
After downloading and installing it will start ptal-init install
When ask if you want to scan the parallel ports answer NO
When ask if you want to scan the usb ports answer YES
Just choose the defaults for the rest of the questions.

If you know open xsane or what ever scanner frontend you prefer you should be able to scan.

Close the scanner program of your choice

Reboot the machine - in theroy this should be needed but in my experience if you don't the printer won't work.

Log back in as the same user as before

Computer/System Configuration/Printing
New Printer
Use a detected printer ( the PSC-2350 should be listed) highlight it. It might also show 2300

Forward
Manufacturer HP
Model PSC 2300
Default driver is OK
Apply
You should now have the newly installed PSC-2300 show up under printers and you are ready to print.

Using thie procedure I have been able to get the printer and the scanner to work together as they are suppose to.

This same procedure worked for my old PSC-750 also, so I would think that the same procedure could be used for any of the HP PSC printers.

As long as the printer is listed at [http://www.linuxprinting.org/](http://www.linuxprinting.org/) it should work. There is also some hints and tips about the various printers there.

---

### Post by AndyAWS on 2005-04-17
I just want to thank you for this execellent How-To.

I have a PSC-2355 and this worked perfectly for me.

---

### Post by verbalshadow on 2005-04-19
[QUOTE=AndyAWS]I just want to thank you for this execellent How-To.

I have a PSC-2355 and this worked perfectly for me.[/QUOTE]
 This Also works for the HP PSC 1315v. the printer is decected as psc 1310

---

### Post by UbuntuPerre on 2005-08-09
Yes I join the thank-you gang. 
I have one question: I'm using HP PSC 2355 on my Ubuntu PC. I want to share it on my windows network. I have managed the sharing, but when installing the printer on the WinXP machines, I can't find a suitable driver. The HP CD has a minimum install on 300MB!! I can't understand why I have to install that much when all I want from HP is to print...

Regards,
UbuntuPerre (new to Ubuntu ;)

---

### Post by leftydf1970 on 2005-10-17
[QUOTE=UbuntuPerre]Yes I join the thank-you gang. 
I have one question: I'm using HP PSC 2355 on my Ubuntu PC. I want to share it on my windows network. I have managed the sharing, but when installing the printer on the WinXP machines, I can't find a suitable driver. The HP CD has a minimum install on 300MB!! I can't understand why I have to install that much when all I want from HP is to print...

Regards,
UbuntuPerre (new to Ubuntu ;)[/QUOTE]

UbuntuPerre, 

I had the same problem until I happened across another forum on this exact problem.  It turns out that the Deskjet 990C driver which comes with WinXP works perfectly with the printer portion of the PSC-2355.  I installed it on 2 different networked machines in my house, and it works perfectly.

Regards,
Don

---

### Post by 11hjpphty76lkjj on 2005-10-17
hpoj will not give you full functionality of your printer.  For a full driver package go to [http://hpinkjet.sf.net](http://hpinkjet.sf.net) and use that software.  It's not hard to install, and there is a good forum section for any issues.  I would recommend HPLIP over HPOJ.  HPLIP is update with many newer models as well as printing over USB/ETH/Parallel Port, etc.  It also has a GUI as well as many features.

Aaron

---

### Post by leftydf1970 on 2005-10-18
[QUOTE=kalosaurusrex]hpoj will not give you full functionality of your printer.  For a full driver package go to [http://hpinkjet.sf.net](http://hpinkjet.sf.net) and use that software.  It's not hard to install, and there is a good forum section for any issues.  I would recommend HPLIP over HPOJ.  HPLIP is update with many newer models as well as printing over USB/ETH/Parallel Port, etc.  It also has a GUI as well as many features.

Aaron[/QUOTE]

Aaron,

I agree that HPLIP is a much better option.  The realease version of 5.10 actually comes loaded with this.  I don't know if you mean there is a newer version of it now available.  

Don

---

