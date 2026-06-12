---
title: "Trying to install new Brother DCP-560CN printer"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by gandalf2000 on 2008-07-14
I bought the above printer today and have wasted most of the day trying to get it running but it steadfastly refuses all my advances.  I downloaded the Brother linux driver for Debian distros and installed it, I think.  I also have this file, ink3_GPL_src_101-1 from somewhere and my printer is there but I still can't get it to work.  I want to run it as a network printer but not a problem if it has to be run as a local USB printer ( I have tried both ).  Any help would be much appreciated.

---

### Post by kevincai96 on 2008-07-14
I found this really cool site that lets you make money! It's real, since I use it. [http://www.AWSurveys.com/HomeMain.cfm?RefID=kevincai96](http://www.AWSurveys.com/HomeMain.cfm?RefID=kevincai96)

---

### Post by plucky on 2008-07-14
> **gandalf2000 said:**
> I bought the above printer today and have wasted most of the day trying to get it running but it steadfastly refuses all my advances.  I downloaded the Brother linux driver for Debian distros and installed it, I think.  I also have this file, ink3_GPL_src_101-1 from somewhere and my printer is there but I still can't get it to work.  I want to run it as a network printer but not a problem if it has to be run as a local USB printer ( I have tried both ).  Any help would be much appreciated.

If you are running Ubuntu Hardy 8.04,the Brother drivers are in **Synaptic Package Manager**.Just open and search for Brother DCP-560CN and it will show you the two packages you need to install.Tick the boxes and **Apply** and it will install the drivers.

For more information see the [Wiki Brother Packaging](https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(brother)) page.

Good Luck

---

### Post by gandalf2000 on 2008-07-14
Thank you, plucky.  That did it.  Kinda frustrating spending all that time when the solution was so simple.  Love this forum, without it Ubuntu would be much weakened.

---

### Post by gandalf2000 on 2008-07-15
Ok, plucky, got another problem for you.  I have the printer set up as a network printer and working just fine.  I cannot however get the scanner working.  I have sane, xsane, xsane-common and sane-utils installed and also, for good measure, kooka.  Xsane won't recognize the scanner and kooka just goes away and hides when I ask it to scan for devices.  Help, what do I do now?

---

### Post by plucky on 2008-07-15
> **gandalf2000 said:**
> Ok, plucky, got another problem for you.  I have the printer set up as a network printer and working just fine.  I cannot however get the scanner working.  I have sane, xsane, xsane-common and sane-utils installed and also, for good measure, kooka.  Xsane won't recognize the scanner and kooka just goes away and hides when I ask it to scan for devices.  Help, what do I do now?

I am not sure about network scanning as my printer is connected by USB,but you have to install the [Brother Sane drivers](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html) from the website.

See this [thread for Howto](http://ubuntuforums.org/showthread.php?t=590793) install the Brother Sane driver.


Good Luck

---

### Post by gandalf2000 on 2008-07-16
Well, I've tried everything I can find to get the scanner working.  I have installed sane, xsane, xsane-common, brscan2, scankey and probably one or two others.  I've messed around with it til I'm blue in the face.  The scanner is registered but when I run scankey it is "not responded" but it is turned on.  The router says it is connected and it does print with no problems.  When I try to run Xsane Image Scanner I get this message "Failed to open device 'brother2:net1;dev0':Invalid argument."
This is an improvement over what I was getting.  I was getting the "no scanners found" message.  Please help, it's driving me mad, errrr, well.......................

---

### Post by plucky on 2008-07-16
I don't know if this will help but see post #4 on this [thread](http://ubuntuforums.org/showthread.php?t=702105&highlight=brother+scanner)

Good Luck

---

### Post by gandalf2000 on 2008-07-16
Got it.  I had been doing it by the Brother solutions website [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html) but I already had bits and pieces installed and was going round in circles.  Last night I decided to remove all the scanning software that I had installed to get this thing to work with the intention of starting again from the beginning.  So, this morning I started again and after one false start it is up and running.  The main problem I was having is that the packages have to be installed in the right order and while the site mentions sane-utils and Gimp it doesn't give instructions to install them.  Gimp was already installed but sane-utils wasn't.  Guess a careful read of the instructions would have been quicker.  Anyway, thanks to Brother for providing a site for Linux, a much better company than Lexmark.

---

### Post by gandalf2000 on 2008-07-20
Nope, I don't got it.  I have three Ubuntu boxes on the network and I can get the scanner working on all three boxes.  But when I go back to use it the damn thing won't work and then I have to mess with it for awhile to get it scanning again.  Talk about frustrating.  The printer side was bad enough but this is unbelievable.  Can anyone provide any insight to this problem?

---

### Post by rbmorse on 2008-07-21
Sounds like the dread permissions problem. 

Open a terminal window and issue whatever command you use to start the scan utility, but procede it with sudo, i.e., 

sudo *scanprogram*

Enter your user password when prompted.  Look for interesting error messages.  If it "just works" as root but not as your regular user, we have some detecting work to do, but the problem is fixable.

---

### Post by sbms81 on 2009-03-09
Hello I have tried to install the Brother 560CN (printer) and scanner on ubuntu 8.10. When I tried to scan with XSane, It only worked when I was logged in as root. The solution for this problem is to edit the file:
** /etc/udev/rules.d/40-basic-permissions.rules **

Before:
[B] # USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664" [/B]

after:
[B] # USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"[/B]

finally:

**sudo /etc/init.d/udev restart **


this worked for me...

See this link
[http://wiki.ubuntuusers.de/Brother/Scanner#udev-Regeln-anpassen](http://wiki.ubuntuusers.de/Brother/Scanner#udev-Regeln-anpassen) (German)

---

