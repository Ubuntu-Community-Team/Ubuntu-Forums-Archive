---
title: "Wireless Networks Scanner"
date: 2006-08-16
forum: Outdated Tutorials &amp; Tips
---

### Post by robert_pectol on 2006-08-16
Here's a simple script that allows you to scan the area for wireless networks using your wireless network interface.  Simply copy the following block of code and paste it into your text editor, save it as, 'wiscan.sh', and set it to be executable (chmod 755 wiscan.sh).  At this point, you can already run the script from the command line!  First, it will automatically detect the presense of a wireless network interface in your Ubuntu box.  Next, it will use that interface to conduct a quick scan of the area for any wireless networks.  Then, it will generate a nice little gui dialog with the results of the scan!  Pretty cool!  :p 

Now, instead of having to launch it from the command line, why not create a little taskbar launcher for it?  It's easy to do!  Simply right-click on an empty space on your taskbar and select, 'Add to panel...'  Then select, 'Custom Application Launcher.'  For the, 'Name' and, 'Generic Name', you can put, 'WiScan.'  For the, 'command:' put, '/path/to/wiscan.sh' and then select an icon for your new WiScan Launcher!  Click, 'ok' and you're ready to scan for wireless networks with a simple click of your new WiScan Launcher.  You can download the script here:
[http://rob.pectol.com/myscripts/wiscan.sh.txt](http://rob.pectol.com/myscripts/wiscan.sh.txt)
As pointed out by PvSinNL, the script needs to execute the scan with root privs.  I've added that ability to this version of the scanner.  It will now prompt you for you system password when needed!

It's not Netstumbler but hey, it gives you a quick and easy view of the wireless networks around!  Enjoy!  ;)

---

### Post by PvSinNL on 2006-08-17
Nice idea, though I believe you need to be a priviledged user (root) or use sudo to actually see all available networks. At least, that's how it works on my system.
 
The *iwlist* man page reads: 
> Triggering  scanning  is  a privileged operation (root only) and normal users can only read left-over scan results.

---

### Post by DavidW2 on 2006-08-18
Nice little program. Just have to add sudo to make it work.  Gives me the results I want. Thanks

---

### Post by robert_pectol on 2006-08-19
> **PvSinNL said:**
> Nice idea, though I believe you need to be a priviledged user (root) or use sudo to actually see all available networks. At least, that's how it works on my system...

Interesting!  Thanks for pointing that out.  Now to figure out why it doesn't require root on mine...

---

### Post by troy1of2 on 2006-08-19
Very nice little script. Thank you so much for posting this!

---

### Post by kleeman on 2006-08-19
Thanks for the script. BTW it doesn't work if you happen to have two wireless interfaces.

---

### Post by robert_pectol on 2006-08-21
Ok, just a quick note to let you know that the script has been updated.  It now prompts the user for his/her password when required, and runs the scan with the appropriate privs.

> **kleeman said:**
> Thanks for the script. BTW it doesn't work if you happen to have two wireless interfaces.

It should now!  I've given it the ability to automatically select the first wireless network interface it finds on your system.  Give the new version a try!

---

### Post by kleeman on 2006-08-21
> **robert_pectol said:**
> Ok, just a quick note to let you know that the script has been updated.  It now prompts the user for his/her password when required, and runs the scan with the appropriate privs.



It should now!  I've given it the ability to automatically select the first wireless network interface it finds on your system.  Give the new version a try!

Much better. Might be nicer to output both interfaces (I use my second interface normally).

---

### Post by robert_pectol on 2006-08-21
> **kleeman said:**
> Much better. Might be nicer to output both interfaces (I use my second interface normally).

The version from my Website (v0.4) now allows you to choose from all of the detected wireless interfaces on your machine!  You can get it here:
[http://rob.pectol.com/myscripts/wiscan.sh.txt](http://rob.pectol.com/myscripts/wiscan.sh.txt)
Enjoy!

---

