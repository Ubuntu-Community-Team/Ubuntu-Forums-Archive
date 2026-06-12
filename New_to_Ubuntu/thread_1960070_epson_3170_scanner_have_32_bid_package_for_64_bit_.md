---
title: "epson 3170 scanner have 32 bid package for 64 bit system"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by mikeprosceo on 2012-04-16
I am using 64 bit ubuntu 11.10 and the only epson driver I can find for my perfection 3170 is 32 bit. Alien won't even convert the rpm package to a deb because of the wrong environment. Is there a way to force the 32 bit to work in the 64 bit environment? I have a brother 32 bit lazer printer and was able to make it work in my 64 bit with the help of Brother. I have searched all over the web but have dead ended. Please help.

---

### Post by marcisim on 2012-07-08
I' ve got ubuntu 10.04 and i'm trying ti have my **epson perfection 3170 photo** working.
I followed [this thread]("http://ubuntuforums.org/showthread.php?t=1052521"), in particular the instructions posted by Ronok (but i did not install the package libstdc++5 since I've got libstdc++6).

Before doing that, i got:

[INDENT]**sane-find-scanner** --> found USB scanner (vendor=0x04b8 [EPSON], product=0x0116 [EPSON Scanner]) at libusb:002:003

**xsane** --> Failed to start scanner: invalid argument 			 		[without opening any window]

**iscan** --> Could not send command to scanner. Check the scanner's status

**scanimage -L** --> No scanners were identified. If you were expecting something different, check that the scanner is plugged in, turned on and detected by the sane-find-scanner tool (if appropriate). Please read the documentation which came with this software (README, FAQ, manpages). 			 		
[/INDENT]
After the changes (including commenting out epson2 and auncommenting epson in  **/etc/sane.d/dll.conf**) I get:

[INDENT]**sane-find-scanner** --> found USB scanner (vendor=0x04b8 [EPSON], product=0x0116 [EPSON Scanner]) at libusb:002:003

**xsane** --> **OPEN THE PREVIEW WINDOW** but after pressing the SCAN button i get: **Failed to start scanner: invalid argument **

**iscan** --> Could not send command to scanner. Check the scanner's status

**scanimage -L** --> FATAL: Error inserting parport_pc  (/lib/modules/2.6.32-25-generic/kernel/drivers/parport /parport_pc.ko): Operation not permitted
FATAL: Error inserting parport_pc (/lib/modules/2.6.32-25-generic/kernel/drivers/parport/parport_pc.ko): Operation not permitted
**device `epson:libusb:002:003' is a Epson  flatbed scanner**

[/INDENT]Do you have any idea?

---

### Post by kimbanda2008 on 2012-10-30
I have exactly the same problem with ubuntu 12.10.  Last year the scanner (epson perfection 3170) worked fine under ubuntu 11.10 with simple-scan, but now i cannot install it. 
thanks

---

