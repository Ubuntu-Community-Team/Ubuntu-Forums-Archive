---
title: "How to install Brother laser printer."
date: 2008-07-12
forum: New to Ubuntu
---

### Post by sajackson on 2008-07-12
Hi, I am still new to Ubuntu and Linux in general and was hoping someone could give me a simple step by step procedure for installing a printer with the following parameters:-

Brother HL-1450 Laser Printer
LPR Driver for LPD service downloaded
Connected to the print server port on my broadband router
Router IP: 192.168.0.1
Standard TCP/IP port
Protocol: LPR
Queue name: lpt1
PC is based on AMD Duron 1.3GHz, 512Mb DDR

I have downloaded the following driver from the Brother site - "hl1450lpr-1.1.2-1.i386.rpm". It says it is suitable for Red Hat / Mandriva (Mandrake) / SuSE but does not mention Ubuntu. Will this driver be OK with Ubuntu?

There are instructions on the Brother site here:-
[http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html]("http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html")
It mentions "rpm" and "dpkg" users, which am I?
What is the "printcap" file in Ubuntu called and where is it?
In the section headed "Network Users" would the lines I edit become:
[INDENT]:rm=192.168.0.1\[/INDENT]
[INDENT]:rp=lpt1\[/INDENT]
[INDENT]and if not what should they be?[/INDENT]
What is the command in Ubuntu to restart the LPD service?
[INDENT]Is it: /etc/init.d/lpd restart[/INDENT]

Sorry for all the questions but as you can see I have done a bit of research before asking.

Any help would be greatly appreciated.

---

### Post by bobnutfield on 2008-07-12
First of all, Ubuntu is Debian based and you will need the driver with the .deb extention, which can then be installed with your package installer.

Once the driver is installed, your GUI print managers should work (System>Administration>Printing).

.rpm files will not work in Ubuntu (unless they are converted .deb files, which isn't usually necessary).

Bob

---

### Post by sajackson on 2008-07-12
Hi bobnutfield, thanks for the quick reply. I have downloaded the Debian driver and tried to install it using the following command:-

sudo dpkg -i --force-all --force-architecture hl1450lpr-1.1.2-1.i386.deb

It fails with the following messages:-

Selecting previously deselected package hl1450lpr.
(Reading database ... 165378 files and directories currently installed.)
Unpacking hl1450lpr (from hl1450lpr-1.1.2-1.i386.deb) ...
Setting up hl1450lpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/HL1450': No such file or directory
chown: cannot access `/var/spool/lpd/HL1450': No such file or directory
chgrp: cannot access `/var/spool/lpd/HL1450': No such file or directory
chmod: cannot access `/var/spool/lpd/HL1450': No such file or directory
/var/lib/dpkg/info/hl1450lpr.postinst: 4: /etc/init.d/lpd: not found
dpkg: error processing hl1450lpr (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 hl1450lpr

When I go to the GUI print manager there is no mention of the Brother printer.

Any ideas?

---

### Post by UbuntuNerd on 2008-07-12
follow this post as i believe it will be usefull to you hope it works!!!

[http://ubuntuforums.org/showthread.php?t=105703]("http://ubuntuforums.org/showthread.php?t=105703")

---

### Post by plucky on 2008-07-12
Are you running Hardy Heron 8.04?


The Brother drivers are now in the repositories ```
sudo apt-get install brother-lpr-drivers-laser1
sudo apt-get install brother-cups-wrapper-laser1
```

See this link for [Brother Driver Packaging](https://wiki.ubuntu.com/BrotherDriverPackaging)


Good Luck

---

### Post by sajackson on 2008-07-12
Thanks very much, plucky, I am indeed running Hardy Heron 8.04, that worked perfectly!! I was able to do it all from System / Administration / Printing. Just followed the instructions on the link you gave under the section "Network printer configuration". I put in the IP address of the router and the port (lpt1) the printer is connected to!

I am now printing directly to the Brother via my network connection the same as my Windows machines do!! Well pleased.

Thanks to everyone.

---

### Post by bayvista on 2009-06-10
Hi,
I am having a problem with a HL-2140. Everything has installed correctly. When I try and print a Test Page, the motor starts up but no output. Any suggestions welcome.

---

### Post by plucky on 2009-06-11
Open Firefox and in the address bar put ```
http://localhost:631/admin/
``` This will open the cups administration interface.Check the logs for any information.

Also make sure the correct paper size is set.Usually the default is set to "letter" and should be A4 or vice versa.


Good Luck

---

