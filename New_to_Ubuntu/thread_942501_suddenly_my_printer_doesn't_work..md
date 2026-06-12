---
title: "suddenly my printer doesn't work."
date: 2008-10-09
forum: New to Ubuntu
---

### Post by adamogardner on 2008-10-09
a little monolog box pops up that reads,  "NOT CONNECTED?  Printer 'Photosmart_c2700_series'  may not be connected"  
Does anyone know what's going on?  I checked the connection as far as the wires that connect to it and my computer and it and the wall.  Everything is fine.  The last thing I remember doing is hitting cancel in the middle of my last print job so as not to print what I didn't need.  Then it started to finish the job and I hit cancel again, but I don't think that is relevant.  I don't know.  How can I troubleshoot this or what is going on with it?  thanks

---

### Post by bcom on 2008-10-09
I assume you powered-off both the computer and the printer, then powered them back on?

---

### Post by adamogardner on 2008-10-09
yes I powered off both, though not concomitantly.  It didn't change behavior at all.  it's getting no signal from the computer.

---

### Post by bcom on 2008-10-09
Not sure where to go from here.

What if you check to see if cupsd is running: type "etc/init.d/cupsys status" from the prompt in Terminal.

If cuspd is not running, you can start it by typing "sudo /etc/init.d/cups start"

---

### Post by adamogardner on 2008-10-09
> **bcom said:**
> Not sure where to go from here.

What if you check to see if cupsd is running: type "etc/init.d/cupsys status" from the prompt in Terminal.

If cuspd is not running, you can start it by typing "sudo /etc/init.d/cups start"

what is init.d and cups? what does this do?
here's what I've done:
.restarted both machines
.changed usb ports 
.attempted hp-setup
.attempted hp-toolbox
Is is not reaching the printer .  There is no damage to the chord. I was trying to print from GIMP when this occurred.  It was my first time in GIMP but again I think this too is irrelevent.

---

### Post by superprash2003 on 2008-10-09
how about just deleting the printer.. and adding it again..

---

### Post by bcom on 2008-10-09
cups stands for Common Unix Printing Systems.  Cups is used to handle printers.

init.d is a directory that holds scripts to start and start services

The commands I suggested would a) tell you if the cups service is running and b) start the service if it had stopped for some reason.

A couple of other thoughts: unistall and reinstall printer, change the USB cable itself.  I've had devices malfunction due to small breaks in cables.

---

### Post by adamogardner on 2008-10-09
can you rewrite that command?  here's what I got from it:
adamogardner@CRONUS:~$ etc/init.d/cupsys status
bash: etc/init.d/cupsys: No such file or directory
adamogardner@CRONUS:~$ cd /etc/init.d
adamogardner@CRONUS:/etc/init.d$ ls

...cupsys ....

adamogardner@CRONUS:/etc/init.d$ cd cupsys
bash: cd: cupsys: Not a directory
adamogardner@CRONUS:/etc/init.d$ stsatus cupsys
bash: stsatus: command not found
adamogardner@CRONUS:/etc/init.d$ status cupsys
status: Need to be root
adamogardner@CRONUS:/etc/init.d$ sudo status cupsys
sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 
status: Unknown job: cupsys
adamogardner@CRONUS:/etc/init.d$ sudo cupsys status
sudo: unable to resolve host CRONUS
sudo: cupsys: command not found
adamogardner@CRONUS:/etc/init.d$

---

### Post by LowSky on 2008-10-09
from Firefox go to the following address
[http://localhost:631](http://localhost:631)

then check if your printer shows up, cancel any jobs that are stuck and so on.

if that doesn't work try downloading the newest version of HPLIP, you can easily find it on google and the instructions are really clear.

---

### Post by adamogardner on 2008-10-09
> **LowSky said:**
> from Firefox go to the following address
[http://localhost:631](http://localhost:631)

then check if your printer shows up, cancel any jobs that are stuck and so on.

if that doesn't work try downloading the newest version of HPLIP, you can easily find it on google and the instructions are really clear.

well that
 was interesting.  there were a handful of 'jobs' on hold that I canceled.  It made no difference in the connection though.  I'll look into hp-lip, thanks.

---

### Post by bcom on 2008-10-09
sorry, the first command should be: /etc/init.d/cupsys status

the second command is: sudo /etc/init.d/cupsys start

---

### Post by adamogardner on 2008-10-09
> **bcom said:**
> sorry, the first command should be: /etc/init.d/cupsys status

the second command is: sudo /etc/init.d/cupsys start

no if you look that is what I typed.  It doesn't work.

---

