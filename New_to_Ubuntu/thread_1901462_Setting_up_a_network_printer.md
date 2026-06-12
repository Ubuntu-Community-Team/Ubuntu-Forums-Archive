---
title: "Setting up a network printer"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by JeremySchubert on 2011-12-28
I am trying to setup my Brother 4100 Fax/Printer which is connected to a single port Star Tech USB print server.  The printer wizard finds the printer by it's IP adddress.  But I can't seem to print anything.

1.  What determines the name of the Queue?  Is it something I pick arbitrarily or is it something configured in the print server such as the device's name?
2.  On the Brother website, I can choose from four drivers (LPR and CUPS, one of each DEB and one of each RPM).  How do I know which to choose?

Thanks,
Jeremy

---

### Post by drdos2006 on 2011-12-28
The driver will be DEB ( short for Debian operating system ).

Normally a printer is connected to computer with the driver loaded onto the computer. The printer is then accessed by the browser.

http://<the-computer-ip-address>:631/printers/<my-printer-name>

CUPS uses port 631 to communicate with the printer.

Does the single port Star Tech USB print server have an IP address that you can ping ?
Is the single port Star Tech USB print server connected to a computer that has an IP address that you can ping ?

regards

---

### Post by jtarin on 2011-12-28
[Instructions for using CUPS to setup Network Printer.]("http://www.cups.org/documentation.php/network.html")

---

### Post by JeremySchubert on 2011-12-28
Thank you both for your response.  Based on what you've posted, here is some more info.

I can ping the print server device and I can connect to its web based configuration page.
I can get to CUPS on my computer with localhost:631 but not with the ip-address:631.
Using CUPS, I added the printer.  The process completed but during the install a window popped up noting "There was an error during the CUPS operation 'server-error-internal-error'"
On a Macbook pro I have the same printer setup and working with cups using lpd://192.168.0.197/lpt1. 

I'll keep messing around with it, but if you guys have any further suggestions, I'd appreciate it.  
Thanks,
Jeremy

---

### Post by drdos2006 on 2011-12-28
If you can ping to 192.168.0.197 and you can access its web interface you may have to allow port 631 to access the printer.

Or you may have to connect via : ipp://192.168.0.197:631/lpt1

ipp = Internet Printing Protocol

regards

---

### Post by JeremySchubert on 2011-12-28
We have a winner!  Thank you very much DrDOS, adding port 631 did the trick.

---

### Post by JeremySchubert on 2011-12-29
Hmmm, in order to fix an update notification problem, I had to remove and then reinstall my printer driver.  After that, my printer stopped working, giving me a message about an 'empty print file'.  After digging around a while, I found documentation on the Brother website about how to access the config file for my printer.  When I tried to run the command 
> brprintconf -P [Printer Name] [Option] I got a message saying the program had not been installed, please do the following
> sudo apt-get install brother-lpr-drivers-laser1
I did that and now everything is hunky dory again.  So I'm not complaining.  Just wondering if someone would please explain 
1. does 'apt-get install' simply stand for get this application and install it
2.  Where is the database this install came from
Thanks,
Jeremy

---

### Post by chipbuster on 2011-12-30
APT is the advanced packaging tool, and apt-get install is a command that just tell the computer to pull the program off of an online repository and install it.

As for where it came from, I'm not entirely sure, but I believe Canonical is responsible for maintaining the Ubuntu repositories....dunno if that particular file came from there though.

---

