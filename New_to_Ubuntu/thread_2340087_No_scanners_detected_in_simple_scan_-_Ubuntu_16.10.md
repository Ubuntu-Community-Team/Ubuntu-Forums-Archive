---
title: "No scanners detected in simple scan - Ubuntu 16.10"
date: 2016-10-15
forum: New to Ubuntu
---

### Post by bartek85 on 2016-10-15
Hi, for a couple of Ubuntu releases, to make the scanner work, I had to do what was suggested in this thread [https://ubuntuforums.org/showthread.php?t=2043258](https://ubuntuforums.org/showthread.php?t=2043258). However, in Ubuntu 16.10 this trick does not solve the problem. Sane-find-scanner shows "found USB scanner (vendor=0x04f9 [Brother], product=0x01fe [MFC-250C]) at libusb:001:009". I have tried other solutions from this forum (all of them were for previous Ubuntu releases), but without success.
Does anyone have any ideas what to do??

---

### Post by Geoffrey_Arndt on 2016-10-16
Maybe it's time for house cleaning, . . Scan your file system including your home directories and remove all brother folders/files you find.   Afterwards, use the Printer utility in Settings to remove the device.   Re-add the printer but dont run the print test or send a print file to the spooler (until after you've installed the new drivers).   

Finally, use the latest drivers for Deb distributions via Brothers site to download and run the printer & scanner meta installer: 

note:  the meta installer will download and install all needed drivers including the scanner.   Just important not to have any old conflicting drivers still on the system before the install.

note2:  read the install instructions from Brother on the download page before starting.

[URL="http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfc250c_all&os=128&dlid=dlf006893_000&flang=4&type3=625"]http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfc250c_all&os=128&dlid=dlf006893_000&flang=4&type3=625


[/URL]

---

### Post by bartek85 on 2016-10-17
Thanks Geoffrey for th reply. I have already tried all the procedures you suggested. I have a clean Ubuntu 16.10, not an upgrade, so I shouldn't have any conflicting drivers. Printing works fine. I've tried the latest script from Brother site. I did also try installing the scanner manually and it didn't work either(I used [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)). Xsane, scan2pdf and simple-scan still show that they didn't detect any scanners.

---

### Post by Geoffrey_Arndt on 2016-10-18
Can you manually scan to a flash-stick or sd card via the menu option on the printer (versus using the PC via an app like SimpleScan)?   Manual scanning is sometimes firmware controlled and not dependent on OS's & drivers.

---

### Post by bartek85 on 2016-10-19
Yes, I can scan to memory stick, but only as a pdf file. For now I am using this option. I think I have already spent too much time making my scanner work, so I'm giving up. One again thanks Geoffrey.

---

