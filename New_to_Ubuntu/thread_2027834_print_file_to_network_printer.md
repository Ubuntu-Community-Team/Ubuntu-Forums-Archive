---
title: "print file to network printer"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by paul1945 on 2012-07-17
I have an old Dos program that runs in DosBox and has been configured for Windows to produce a print file  (.prn) that contains all the print codes as well as the text to be printed. There are special utilities for Windows that automatically pick up a .prn file and send it to the printer; and then delete the  file so it does not print a second time. 
Is such an utility available for Ubuntu 12.04 or is it possible to accomplish this by means of a set of Linux commands?
The location of the printer is smb://192.168.1.2/HPLaserJ

---

### Post by paul1945 on 2012-07-18
I have to qualify this a little. I have made a printraw.sh file to print the UNNAMED.RAW file created by one program with the command:
lp -d HP-LaserJet-m2727-MFP /home/paul/dosdrive/document/UNNAMED.RAW
and that works a treat; so far so good.
Is there any way to get Ubuntu (I guess CUPS) to poll for a newly generated file like UNNAMED.RAW and print this automatically, rather than having to execute this manually?

---

