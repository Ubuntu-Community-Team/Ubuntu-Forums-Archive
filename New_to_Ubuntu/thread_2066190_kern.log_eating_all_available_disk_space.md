---
title: "kern.log eating all available disk space"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by Paper Pusher on 2012-10-04
I'm the administrator of several ubnuntu 12.04 DTE systems. Two systems are giving me major headaches. 

One is a 32-bit and the other is 64-bit. They each are running out of disk space.

The problem seems to be in the folder /var/log. The kern.log file and the kern.log.1 file is over 100 GB large.

What is going on? My personal assistants equivalent files are only about 700 kB large.

---

### Post by Doug S on 2012-10-04
Could you give us a snippet of some of the entries in the kern.log file. Maybe the output from:```
tail -30 /var/log/kern.log
```
Something might be wrong, making many entries in the log file, or perhaps something is logging too much information causing the file to become excessively large.
 
If you are getting into difficulties with disk space, it would probably be O.K. to delete the older kern.log.1 file.

---

### Post by 2F4U on 2012-10-04
As an immediate action, you should reconfigure the logrotation on those systems, so that logs don't grow that large:

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
[http://www.thegeekstuff.com/2010/07/logrotate-examples/#more-4826](http://www.thegeekstuff.com/2010/07/logrotate-examples/#more-4826)

However, I would also suggest that you find the reason for such large log files, because it indicates that something is wrong.

---

### Post by Paper Pusher on 2012-10-04
Thank you very much for all the advice. In a moment of panic since the system has run out of diskspace I deleted the kern.log file. The listing below is from the kern.log.1 file. 

Sep 30 07:44:57 axel-O-E-M kernel: [69438.019364] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.019422] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.019479] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.019536] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.019598] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.019655] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.019706] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.019754] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.019803] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.019855] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.019903] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.019952] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.020039] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.020093] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.020144] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.020206] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.020265] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.020322] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.020379] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use 
Sep 30 07:44:57 axel-O-E-M kernel: [69438.020437] usb 1-2: usbfs: process 1695 (demond_nscan) did not claim interface 3 before use

What do you think is going on?

---

### Post by Doug S on 2012-10-04
It seems a driver is misbehaving, and doing so at an extremely high repetition rate.
Do you have a Lexmark printer/scanner attached to the computer?
Have you tried to re-start everything?
I can only suggest to search around using search terms "demond-nscan" and "did not claim interface before use", although helpful information seems limited.
 
As a possible temporary patch to help limit file size, see answer 3 [here]("http://unix.stackexchange.com/questions/48894/is-it-possible-to-filter-duplicate-lines-from-syslog").

---

### Post by Paper Pusher on 2012-10-04
yes both the computers have lexmark s315 printers attatched.
Is there something i should do in this situation?

---

### Post by Doug S on 2012-10-04
Well yes, you should try to fix the problem.
There seems to have been new firmware and/or drivers released in August, is that what you are using? If yes try to go back to the previous version.
Did you try to re-start everything yet? Power off the printer at first, and power it up later. Is there any correlation with the entries starting in kern.log?

---

### Post by Paper Pusher on 2012-10-04
Thank you for telling me about the problems with the Lexmark printer drivers.  As I look at the Lexmark website, I see brand new drivers dating back to yesterday.  They are for Ubunutu 11.04 only.  Are these newer drivers then the ones I have currently installed are for Ubuntu 12.04?

Should I use these newly released drivers for 11.04?

How do I uninstall my current drivers?

---

### Post by Paper Pusher on 2012-10-05
I have found new drivers released 10-03-12 for my Lexmark s315 printer. 

Question: How do I install the new drivers on my system? Do I uninstall the old drivers first? How do I uninstall the old drivers?

---

### Post by Jim_Gallagher on 2013-09-07
Has anyone found a solution to the problem of this printer driver causing the Log kern and log sys files to fill the drives in a matter of hours?..i'd hate to have to go back to windoze

---

### Post by Paper Pusher on 2013-09-21
I had the same problem with the Log kern and log sys files filling up disk space. After deleting those files, I did the following:

Used the Lexmark printer installation CD to make a wi-fi installation from a Windows PC.

The mistake I made was accepting firmware updates. That in turn did not allow me to refill the ink cartridges. 

Is there anyway to roll back the firmware updates and return to factory settings?

---

