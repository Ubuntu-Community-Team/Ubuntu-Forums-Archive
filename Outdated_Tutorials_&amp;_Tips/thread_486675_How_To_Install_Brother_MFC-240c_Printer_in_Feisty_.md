---
title: "How To Install Brother MFC-240c Printer in Feisty X64"
date: 2007-06-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Seisen on 2007-06-28
**[SIZE="6"]How To install your Brother MFC-240C in Feisty X64[/SIZE]**

The first step in installing your MFC-240C in Feisty 64-bit  is to download the LPR driver and the cupswrapper driver. The LPR driver can be downloaded here. 
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html")
and the cupswrapper driver can be downloaded here.
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")
Make sure when you download the drivers that you download the drivers for Debian and not Redhat. 

After you have downloaded the drivers you need to install them. Make sure that you install the LPR driver first before you install the cupswrapper driver. To install the LPR driver put this in the terminal. For anybody who doesn't know to open the terminal it can be found by going to Applications>Accessories>Terminal.

```
sudo dpkg -i --force-architecture mfc240clpr-1.0.0-9.i386.deb
```  and to install the cupswrapper

```
sudo dpkg -i --force-architecture mfc240ccupswrapper-1.0.0-9.i386.deb
```

After both of those install successfully open up firefox or whatever other browser you use and put this in. 
[http://localhost:631]("http://localhost:631")

If for some reason you get a error saying page not found than you need to start cups by putting this in the terminal
```
sudo /etc/init.d/cupsys start
```


Click on “Manage Printers” and confirm that the device name is listed there. If the device name is NOT listed there, click on "Add Printer" and install the driver following the on-screen instructions.

If you cannot print you need to install this file.
```
sudo apt-get install lib32stdc++6
```

If you get this error 
```
mkdir: cannot create directory `/var/spool/lpd/mfc240c': No such file or directory
chown: cannot access `/var/spool/lpd/mfc240c': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc240c': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc240c': No such file or directory
``` you need to do this

```
sudo mkdir /var/spool/lpd
sudo mkdir /var/spool/lpd/mfc240c
```





[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html")

---

### Post by GWN on 2007-07-07
Great article Seisen.  I'd finally got my Brother printer working by following your instructions.

I had encountered some problems along the way and thought I'd pass the info onto you and let you decide whether or not to update your article. 

i)  Must cd to the directory with the .deb file
II) Needed to create the lpd and mfc240c directories in spool

The entire screen capture is as follows (I kept careful notes as I'm a Linux and Ubuntu newbie...hope this helps):

*************************************************************************************

How To Install Brother MFC-240c Printer in Feisty X64
UbuntuForum - Thu, 2007-06-28 15:10
How To install your Brother MFC-240C in Feisty X64

The first step in installing your MFC-240C in Feisty 64-bit is to download the LPR driver and the cupswrapper driver. The LPR driver can be downloaded here.
[http://solutions.brother.com/linux/s...r_drivers.html](http://solutions.brother.com/linux/s...r_drivers.html)
and the cupswrapper driver can be downloaded here.
[http://solutions.brother.com/linux/s...s_drivers.html](http://solutions.brother.com/linux/s...s_drivers.html)
Make sure when you download the drivers that you download the drivers for Debian and not Redhat.

After you have downloaded the drivers you need to install them. Make sure that you install the LPR driver first before you install the cupswrapper driver. To install the LPR driver put this in the terminal. For anybody who doesn't know to open the terminal it can be found by going to Applications>Accessories>Terminal.

Code: sudo dpkg -i --force-architecture mfc240clpr-1.0.0-9.i386.deb and to install the cupswrapper

Code: sudo dpkg -i --force-architecture mfc240ccupswrapper-1.0.0-9.i386.deb After both of those install successfully open up firefox or whatever other browser you use and put this in.
[http://localhost:631](http://localhost:631)

If for some reason you get a error saying page not found than you need to start cups by putting this in the terminal
Code: sudo /etc/init.d/cupsys start
Click on “Manage Printers” and confirm that the device name is listed there. If the device name is NOT listed there, click on "Add Printer" and install the driver following the on-screen instructions.

If you cannot print you need to install this file.
Code: sudo apt-get install lib32stdc++6

[http://solutions.brother.com/linux/s..._install6.html](http://solutions.brother.com/linux/s..._install6.html)
Categories: linux


RESULTS after downloading LPR and CUPS packages from the Brother website:
*********************************************************************************************************************************************************
*********************************************************************************************************************************************************
Notes:  Get error message
=========================
my_pc@Sandbanks:~$ sudo dpkg -i --force-architecture mfc240clpr-1.0.0-9.i386.deb
Password:
dpkg: error processing mfc240clpr-1.0.0-9.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc240clpr-1.0.0-9.i386.deb
my_pc@Sandbanks:~$ 


Must cd to the directory with the .deb file:
cd /home/my_pc/WebDownloads/MySoftware/Brother/
=================================================
my_pc@Sandbanks:~/WebDownloads/MySoftware/Brother$ sudo dpkg -i --force-architecture mfc240clpr-1.0.0-9.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 103503 files and directories currently installed.)
Preparing to replace mfc240clpr 1.0.0-9 (using mfc240clpr-1.0.0-9.i386.deb) ...
Unpacking replacement mfc240clpr ...
Setting up mfc240clpr (1.0.0-9) ...
mkdir: cannot create directory `/var/spool/lpd/mfc240c': No such file or directory
chown: cannot access `/var/spool/lpd/mfc240c': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc240c': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc240c': No such file or directory

my_pc@Sandbanks:~/WebDownloads/MySoftware/Brother$ 


There is NO lpd directory in spool:
===================================
my_pc@Sandbanks:~/WebDownloads/MySoftware/Brother$ ls /var/spool
anacron  cron  cups  mail  openoffice
my_pc@Sandbanks:~/WebDownloads/MySoftware/Brother$ 


Need to create the lpd and mfc240c directories in spool:
========================================================
sudo mkdir /var/spool/lpd
sudo mkdir /var/spool/lpd/mfc240c


Now run the command to install mfc240clpr-1.0.0-9.i386.deb (success!!!):
========================================================================
my_pc@Sandbanks:~/WebDownloads/MySoftware/Brother$ sudo dpkg -i --force-architecture mfc240clpr-1.0.0-9.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 103503 files and directories currently installed.)
Preparing to replace mfc240clpr 1.0.0-9 (using mfc240clpr-1.0.0-9.i386.deb) ...
Unpacking replacement mfc240clpr ...
Setting up mfc240clpr (1.0.0-9) ...

my_pc@Sandbanks:~/WebDownloads/MySoftware/Brother$ 


Now run the command to install mfc240ccupswrapper-1.0.0-9.i386.deb:
===================================================================
my_pc@Sandbanks:~/WebDownloads/MySoftware/Brother$ sudo dpkg -i --force-architecture mfc240ccupswrapper-1.0.0-9.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package mfc240ccupswrapper.
(Reading database ... 103503 files and directories currently installed.)
Unpacking mfc240ccupswrapper (from mfc240ccupswrapper-1.0.0-9.i386.deb) ...
Setting up mfc240ccupswrapper (1.0.0-9) ...
cp: `/usr/lib/cups/filter/brlpdwrappermfc240c' and `/usr/lib64/cups/filter/brlpdwrappermfc240c' are the same file
 * Restarting Common Unix Printing System: cupsd                                                                                                      [ OK ] 

my_pc@Sandbanks:~/WebDownloads/MySoftware/Brother$ 


Following the instructions, found my printer (manage printer), but could NOT print.  Needed to install lib32stdc++6: 
====================================================================================================================
my_pc@Sandbanks:~/WebDownloads/MySoftware/Brother$ sudo apt-get install lib32stdc++6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lib32gcc1 libc6-i386
The following NEW packages will be installed:
  lib32gcc1 lib32stdc++6 libc6-i386
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 3950kB of archives.
After unpacking, 10.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libc6-i386 2.5-0ubuntu14 [3617kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main lib32gcc1 1:4.1.2-0ubuntu4 [22.7kB]                                                                          
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main lib32stdc++6 4.1.2-0ubuntu4 [311kB]                                                                          
Fetched 3950kB in 14s (277kB/s)                                                                                                                             
Selecting previously deselected package libc6-i386.
(Reading database ... 103506 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.5-0ubuntu14_amd64.deb) ...
Selecting previously deselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.1.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package lib32stdc++6.
Unpacking lib32stdc++6 (from .../lib32stdc++6_4.1.2-0ubuntu4_amd64.deb) ...
Setting up libc6-i386 (2.5-0ubuntu14) ...

Setting up lib32gcc1 (4.1.2-0ubuntu4) ...

Setting up lib32stdc++6 (4.1.2-0ubuntu4) ...

my_pc@Sandbanks:~/WebDownloads/MySoftware/Brother$

---

### Post by Seisen on 2007-07-08
I will add those things that you had problems with into the how-to so everything is all together. Thanks for letting me know what other problems you had and how to fix them. I am glad to here that everything went well except for a few minor things.

---

### Post by uranus124 on 2007-08-02
Ok, I followed all the steps to install the printer.  MFC-240c is available in CUPS and i intalled lib32stdc++6 but still nothing...any idea on what I should do?

P.S. I'm running it on the following architecture.
Amd Athlon 4200+ dual core 64 bit

---

### Post by Seisen on 2007-08-03
Is there any errors that are coming up, if so post them?

---

### Post by uranus124 on 2007-08-05
Thank you Seisen for you reply but i managed to solve my problem.  In my printer dialog box, I found that for some reason the printer was set to Network Printer instead of Local Printer. By changing that, I got it too work.

Is there any way to use the scanning function of the MFC-240c in Ubuntu?

Thanks in again for your efforts.

---

### Post by Seisen on 2007-08-05
I know you have to use xsane or something like that, let me see what I can find out.

---

### Post by Seisen on 2007-08-06
Okay I found it. You need to go [http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html)  and download the the brscan2 driver ver. 0.2..3-0. Then to get everything setup do this

1. Install The latest versions of Sane and Xsane

 ```
sudo apt-get install sane xsane
```

2. Install the Brother scanner driver

```
 dpkg -i brscan2-0.2.3-0.i386.deb
```

3. Modify the /etc/fstab file
If the line which starts with "none /proc/bus/usb" or "usbfs /proc/bus/usb" does not exist in the /etc/fstab file, run the following command:

```
echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab 
```

If the line which starts with "none /proc/bus/usb" or "usbfs /proc/bus/usb" does exist in the /etc/fstab file, edit the line as below:


```
none /proc/bus/usb usbfs auto,devmode=0666 0 0
```

4. Modify the USB access control

```
umount /proc/bus/usb
mount /proc/bus/usb
mknod -m 666 /dev/usbscanner c 180 48
```
[URL="http://solutions.brother.com/linux/sol/printer/linux/sane_install.html"]
http://solutions.brother.com/linux/sol/printer/linux/sane_install.html[/URL]

---

### Post by Cone on 2007-08-21
Well THAT's interesting.  I pretty much used your guide to get myself set up on Debian (thanks, by the way.  Very useful.).  Whenever I print, two commands ran by the "lp" user use up a high amount of CPU, and it makes my computer as well as my printer both run/print rather slow.

The commands are "brmfc240cfilter" and "usb".  I've seen "usb" use up to ~50% of my CPU according to top, and I get like..1 page per minute out of the printer (B&W scans.  PDFs from texasmath.org to be precise).

Anyone else having similar experiences? :S

EDIT: I'm actually not using 64 bit and didn't do the 64 bit parts of the guides.  Google just gave me this page before it gave me Brother's website, and the 2 Ubuntu Forum posts had trouble shooting that helped.

---

### Post by Cone on 2007-08-22
Just did a fresh install of Ubuntu to see if it was something with my set up.  Installed Ubuntu, installed drivers, and that's it.  Same problem.

Could it be the whole Whatever -> PostScript -> GhostScript to convert to native thing that's messing it up?  The processes never max out my CPU usage.

---

### Post by Seisen on 2007-08-22
Which drivers did you install?

---

### Post by Cone on 2007-08-22
mfc240clpr-1.0.0-9.i386.deb
mfc240ccupswrapper-1.0.0-10.i386.deb
and
brscan2-0.2.3-0.i386.deb

Everything "works", but the printing from the computer gives me ~1 page per minute (or less).  When I do a copy using the printer itself (which doesn't have anything to do with the computer) it prints at a wonderful speed, and the scanner works wonderfully too.

I don't think it is the processing (PostScript -> Native cycle), however(I'm probably wrong.).  Whenever I set it to "Fast" it goes really fast, though it puts everything really lightly on the page.  Everything else (including "Fast Normal") gives the normal terrible print speed.

It prints a little bit, stops, prints a little more, stops, and does that until it's finished.  Every time it stops, there's a red light at the back of the inside of the printer that I can see move across (quickly) and back (slowly) before it continues to print.  This doesn't occur when I use the "Copy" functionality.

Done lots of Googling and tried tons of things, including...
Rebooting with the printer not plugged in and plugging it in after
Turning off Bi-Directional printing
Changing the printers.conf DeviceURI from usb://Brother/MFC-240C to file://dev/usblp0

None of these have made ANY differences whatsoever. (They all worked for various people with various other devices)

---

### Post by Cone on 2007-08-22
tail /var/log/cups/error_log gives me an ever expanding log.

```
D [22/Aug/2007:17:49:35 -0500] cupsdReadClient: 8 POST / HTTP/1.1
D [22/Aug/2007:17:49:35 -0500] cupsdAuthorize: No authentication data provided.
D [22/Aug/2007:17:49:36 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [22/Aug/2007:17:49:36 -0500] cupsdAuthorize: No authentication data provided.
D [22/Aug/2007:17:49:36 -0500] CUPS-Get-Default
D [22/Aug/2007:17:49:36 -0500] CUPS-Get-Default client-error-not-found: No default printer
D [22/Aug/2007:17:49:36 -0500] cupsdProcessIPPRequest: 6 status_code=406 (client-error-not-found)
D [22/Aug/2007:17:49:36 -0500] Get-Printer-Attributes ipp://localhost/printers/Lazy
D [22/Aug/2007:17:49:36 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [22/Aug/2007:17:49:36 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [22/Aug/2007:17:49:36 -0500] cupsdAuthorize: No authentication data provided.
D [22/Aug/2007:17:49:36 -0500] CUPS-Get-Printers
D [22/Aug/2007:17:49:36 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [22/Aug/2007:17:49:36 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [22/Aug/2007:17:49:36 -0500] cupsdAuthorize: No authentication data provided.
D [22/Aug/2007:17:49:36 -0500] Get-Printer-Attributes ipp://localhost/printers/Lazy
D [22/Aug/2007:17:49:36 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [22/Aug/2007:17:49:36 -0500] cupsdCloseClient: 8
D [22/Aug/2007:17:49:38 -0500] cupsdAcceptClient: 7 from localhost (Domain)
D [22/Aug/2007:17:49:39 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [22/Aug/2007:17:49:39 -0500] cupsdAuthorize: No authentication data provided.
D [22/Aug/2007:17:49:39 -0500] CUPS-Get-Printers
D [22/Aug/2007:17:49:39 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [22/Aug/2007:17:49:40 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [22/Aug/2007:17:49:40 -0500] cupsdCloseClient: 7
D [22/Aug/2007:17:49:40 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [22/Aug/2007:17:49:40 -0500] cupsdAuthorize: No authentication data provided.
D [22/Aug/2007:17:49:40 -0500] CUPS-Get-Default
D [22/Aug/2007:17:49:40 -0500] CUPS-Get-Default client-error-not-found: No default printer
D [22/Aug/2007:17:49:40 -0500] cupsdProcessIPPRequest: 6 status_code=406 (client-error-not-found)
D [22/Aug/2007:17:49:40 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [22/Aug/2007:17:49:40 -0500] cupsdAuthorize: No authentication data provided.
D [22/Aug/2007:17:49:40 -0500] CUPS-Get-Printers
D [22/Aug/2007:17:49:40 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [22/Aug/2007:17:49:40 -0500] cupsdReadClient: 6 POST / HTTP/1.1
D [22/Aug/2007:17:49:40 -0500] cupsdAuthorize: No authentication data provided.
D [22/Aug/2007:17:49:40 -0500] Get-Printer-Attributes ipp://localhost/printers/Lazy
D [22/Aug/2007:17:49:40 -0500] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [22/Aug/2007:17:49:41 -0500] cupsdReadClient: 8 POST / HTTP/1.1
D [22/Aug/2007:17:49:41 -0500] cupsdAuthorize: No authentication data provided.
D [22/Aug/2007:17:49:41 -0500] cupsdAcceptClient: 7 from localhost (Domain)
D [22/Aug/2007:17:49:41 -0500] Get-Printer-Attributes ipp://localhost/printers/Lazy
D [22/Aug/2007:17:49:41 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [22/Aug/2007:17:49:41 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [22/Aug/2007:17:49:41 -0500] cupsdAuthorize: No authentication data provided.
D [22/Aug/2007:17:49:41 -0500] CUPS-Get-Printers
D [22/Aug/2007:17:49:41 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [22/Aug/2007:17:49:41 -0500] cupsdAcceptClient: 10 from localhost (Domain)
D [22/Aug/2007:17:49:41 -0500] cupsdCloseClient: 8
D [22/Aug/2007:17:49:41 -0500] cupsdCloseClient: 7
```

(Yeah, it's now nicknamed "Lazy")

Upon printing, it writes this

```
D [22/Aug/2007:17:51:12 -0500] print_job: auto-typing file...
D [22/Aug/2007:17:51:12 -0500] print_job: request file type is application/postscript.
D [22/Aug/2007:17:51:12 -0500] add_job: requesting-user-name="cone"
I [22/Aug/2007:17:51:12 -0500] Adding start banner page "none" to job 12.
D [22/Aug/2007:17:51:12 -0500] Discarding unused job-created event...
I [22/Aug/2007:17:51:12 -0500] Adding end banner page "none" to job 12.
I [22/Aug/2007:17:51:12 -0500] Job 12 queued on "Lazy" by "cone".
D [22/Aug/2007:17:51:12 -0500] Job 12 hold_until = 0
D [22/Aug/2007:17:51:12 -0500] Discarding unused printer-state-changed event...
D [22/Aug/2007:17:51:12 -0500] job-sheets=none,none
D [22/Aug/2007:17:51:12 -0500] banner_page = 0
D [22/Aug/2007:17:51:12 -0500] [Job 12] argv[0]="Lazy"
D [22/Aug/2007:17:51:12 -0500] [Job 12] argv[1]="12"
D [22/Aug/2007:17:51:12 -0500] [Job 12] argv[2]="cone"
D [22/Aug/2007:17:51:12 -0500] [Job 12] argv[3]="evince-print"
D [22/Aug/2007:17:51:12 -0500] [Job 12] argv[4]="1"
D [22/Aug/2007:17:51:12 -0500] [Job 12] argv[5]="BRBlue=0 BRDocument=Photo BRSlowDrying=OFF BRColorMediaType=Plain BRContrast=0 BRColorEnhancem$
D [22/Aug/2007:17:51:12 -0500] [Job 12] argv[6]="/var/spool/cups/d00012-001"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[9]="SERVER_ADMIN=root@cone-desktop"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[10]="SOFTWARE=CUPS/1.2.8"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[12]="TZ=America/Monterrey"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[13]="USER=root"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[16]="IPP_PORT=631"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[17]="CHARSET=utf-8"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[18]="LANG=en_CA"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[19]="PPD=/etc/cups/ppd/Lazy.ppd"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[20]="RIP_MAX_CACHE=8m"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[21]="CONTENT_TYPE=application/postscript"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[22]="DEVICE_URI=usb://Brother/MFC-240C"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[23]="PRINTER=Lazy"
D [22/Aug/2007:17:51:12 -0500] [Job 12] envp[24]="FINAL_CONTENT_TYPE=printer/Lazy"
I [22/Aug/2007:17:51:12 -0500] Started filter /usr/lib/cups/filter/pstops (PID 10264) for job 12.
I [22/Aug/2007:17:51:12 -0500] Started filter /usr/lib/cups/filter/brlpdwrappermfc240c (PID 10265) for job 12.
I [22/Aug/2007:17:51:12 -0500] Started backend /usr/lib/cups/backend/usb (PID 10269) for job 12.
D [22/Aug/2007:17:51:12 -0500] Discarding unused job-state event...
D [22/Aug/2007:17:51:12 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [22/Aug/2007:17:51:12 -0500] [Job 12] Page = 612x792; 9,9 to 603,783
D [22/Aug/2007:17:51:12 -0500] [Job 12] slow_collate=0, slow_duplex=0, slow_order=1
D [22/Aug/2007:17:51:12 -0500] [Job 12] Before copy_comments - %!PS-Adobe-3.0
D [22/Aug/2007:17:51:12 -0500] [Job 12] %!PS-Adobe-3.0
D [22/Aug/2007:17:51:12 -0500] [Job 12] %%Creator: xpdf/pdftops 3.00
D [22/Aug/2007:17:51:12 -0500] [Job 12] %%LanguageLevel: 2
D [22/Aug/2007:17:51:12 -0500] [Job 12] %%DocumentSuppliedResources: (atend)
D [22/Aug/2007:17:51:12 -0500] [Job 12] %%DocumentMedia: plain 611 791 0 () ()
D [22/Aug/2007:17:51:12 -0500] [Job 12] %%BoundingBox: 0 0 611 791
D [22/Aug/2007:17:51:12 -0500] [Job 12] %%Pages: 1
D [22/Aug/2007:17:51:12 -0500] [Job 12] %%EndComments
D [22/Aug/2007:17:51:12 -0500] [Job 12] Before copy_prolog - %%BeginDefaults
D [22/Aug/2007:17:51:12 -0500] [Job 12] Before copy_setup - %%BeginSetup
D [22/Aug/2007:17:51:12 -0500] [Job 12] Before page loop - %%Page: 2 1
D [22/Aug/2007:17:51:12 -0500] [Job 12] Copying page 1...
D [22/Aug/2007:17:51:12 -0500] [Job 12] pagew = 594.0, pagel = 774.0
D [22/Aug/2007:17:51:12 -0500] [Job 12] bboxw = 612, bboxl = 792
D [22/Aug/2007:17:51:12 -0500] [Job 12] PageLeft = 9.0, PageRight = 603.0
D [22/Aug/2007:17:51:12 -0500] [Job 12] PageTop = 783.0, PageBottom = 9.0
D [22/Aug/2007:17:51:12 -0500] [Job 12] PageWidth = 612.0, PageLength = 792.0
D [22/Aug/2007:17:51:12 -0500] Discarding unused printer-state-changed event...
D [22/Aug/2007:17:51:12 -0500] [Job 12] Printer using device file "/dev/usblp0"...
D [22/Aug/2007:17:51:12 -0500] [Job 12] backendRunLoop(print_fd=0, device_fd=4, use_bc=0)
D [22/Aug/2007:17:51:12 -0500] Discarding unused printer-state-changed event...
D [22/Aug/2007:17:51:12 -0500] cupsdCloseClient: 7
D [22/Aug/2007:17:51:12 -0500] [Job 12] Wrote 1 pages...
D [22/Aug/2007:17:51:12 -0500] PID 10264 (/usr/lib/cups/filter/pstops) exited with no errors.
D [22/Aug/2007:17:51:12 -0500] [Job 12] Read 1024 bytes of print data...
D [22/Aug/2007:17:51:12 -0500] [Job 12] Wrote 1024 bytes of print data...
D [22/Aug/2007:17:51:12 -0500] [Job 12] Read 2354 bytes of print data...
D [22/Aug/2007:17:51:12 -0500] [Job 12] Wrote 2354 bytes of print data...
D [22/Aug/2007:17:51:12 -0500] [Job 12] Read 1024 bytes of print data...
D [22/Aug/2007:17:51:12 -0500] [Job 12] Wrote 1024 bytes of print data...
D [22/Aug/2007:17:51:12 -0500] [Job 12] Read 1024 bytes of print data...

```
then it does a bunch more Read/Writes and then it mixes this intermittently in between the stuff pasted earlier

```
D [22/Aug/2007:17:51:16 -0500] [Job 12] Wrote 8192 bytes of print data...
D [22/Aug/2007:17:51:16 -0500] [Job 12] Read 8192 bytes of print data...
D [22/Aug/2007:17:51:16 -0500] [Job 12] Wrote 8192 bytes of print data...
D [22/Aug/2007:17:51:16 -0500] [Job 12] Read 8192 bytes of print data...

```

Printing ends with
```

D [22/Aug/2007:17:52:05 -0500] [Job 12] Read 8192 bytes of print data...
D [22/Aug/2007:17:52:06 -0500] [Job 12] Wrote 8192 bytes of print data...
D [22/Aug/2007:17:52:06 -0500] [Job 12] Read 1998 bytes of print data...
D [22/Aug/2007:17:52:06 -0500] [Job 12] Wrote 1998 bytes of print data...
D [22/Aug/2007:17:52:06 -0500] PID 10269 (/usr/lib/cups/backend/usb) exited with no errors.
D [22/Aug/2007:17:52:06 -0500] [Job 12] File 0 is complete.
```

(Note that I've (obviously) set it to debug logging <<)

---

### Post by Cone on 2007-08-22
If I start a job and then cancel it shows in the log ALL of the remaining data being fed straight through to the printer and then saying the print job finished successfully.

That would lead me to conclude that it was running out of memory except for the fact that it only sends it 32 kB at a time and the printer has 16 MB of memory.

---

### Post by Cone on 2007-08-24
> Dear Sir/Madam,

This is the Japanese Solutions Center.
Thank you for your inquiry.

We are very afraid to say there is no solution for
the slow print under Linux environment.
We apologize for the inconvenience caused by this.


Best regards,
Brother Solutions Center

I guess the solution is to not buy Brother in the future. (Before you say anything, yes, I did do my research.  [Looked perfect.  I will edit that page soon, though.]("http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-MFC-240C")):(:mad::confused:

---

### Post by Seisen on 2007-08-24
Is thier a particular reason why you have it set as a network printer, just curious. I don't personally own the printer I made this guide for somebody.

---

### Post by Cone on 2007-08-24
..I do?  If so, that could be the problem.  <<

Well, when I set it to LPR/LPRng Print System in the KDE Control Module program, it still prints the same.

At this point I've pretty much come to accept that if I want decent print speeds I boot Windows, and if I want to buy a printer, I don't buy Brother.  :)

EDIT: I think I might be having a problem with Debian/Ubuntu recognizing my USB 2.0 ports as 2.0.  My spec sheet says they are, and Windows acts like they are, but the Hardware Information (whatever it's called) thing on Gutsy Gibbon (I downloaded the Tribe 5 CD to see if it would work better on there with the new version of CUPS and all.  it didn't.) showed 1.0 on most and 1.1 on one or two.

cone@cone:~$ lspci -v | grep USB
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 **[OHCI])**
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 **[OHCI])**
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20 **[EHCI])**

I guess I've found the problem?

EDIT AGAIN: It is indeed mounting as USB 1.0, though my keyboard is working at 2.0.  The box for the printer says it's 2.0 compatible, and my cable says USB 2.0 compatible.

```
Bus 001 Device 010: ID 046a:0048 Cherry GmbH 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046a Cherry GmbH
  idProduct          0x0048 
  bcdDevice            0.26
  iManufacturer           0 
  iProduct                1 Das Keyboard


Bus 001 Device 014: ID 04f9:01ab Brother Industries, Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04f9 Brother Industries, Ltd
```

How do I fix that? <<

---

### Post by Seisen on 2007-08-24
Try putting your keyboard in the usb port where the printer is and vice versa and see if that works.

---

### Post by Cone on 2007-08-24
No change.  This is weird. :\

EDIT: OK, so I was wrong in saying that the keyboard was USB 2.0.  Just apt-got usbview and it shows the speed on the keyboard as 1.5 (1.0's rate), the printer as 12 (1.1's), and my flash drive whenever I plug it in (anywhere) as 480 (2.0).  Doesn't change my situation much, however.

The device config and relevant interface: 
```
usblp / usb-storage
Serial Number: BROD7F933097
Speed: 12Mb/s (full)
USB Version:  1.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 8
Number of Configurations: 1
Vendor Id: 04f9
Product Id: 01ab
Revision Number:  1.00

Config Number: 1
	Number of Interfaces: 3
	Attributes: c0
	MaxPower Needed:   2mA

	Interface Number: 0
		Name: usblp
		Alternate Number: 0
		Class: 07(print) 
		Sub Class: 01
		Protocol: 02
		Number of Endpoints: 2

			Endpoint Address: 01
			Direction: out
			Attribute: 2
			Type: Bulk
			Max Packet Size: 64
			Interval: 0ms

			Endpoint Address: 82
			Direction: in
			Attribute: 2
			Type: Bulk
			Max Packet Size: 16
			Interval: 0ms
```

---

### Post by SabrinalovesUbun2 on 2007-09-27
I have intel x86, do your instructions apply for me too?

(I managed to get the printer working last week, I thought the scan option is included, but it doesn't seem to be.)

I downloaded the "brscan2 driver ver. 0.2..3-0" from Brother site to my desktop, then did

step 1:
sudo apt-get install sane xsane

step 2:
dpkg -i brscan2-0.2.3-0.i386.deb

but it says:

dpkg: error processing brscan2-0.2.3-0.i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
brscan2-0.2.3-0.i386.deb

---

### Post by Seisen on 2007-09-27
I replied back to your PM but to answer your other question if you have a 64-bit processor and you are running 64-bit Ubuntu then yes but if you are running a 32-bit processor the instructions are slightly different.

---

### Post by Matthaeus on 2007-10-11
I'm having a lot of trouble setting up a brother DCP-130 on ubuntu64...it's really the last step in making this system usable.

I followed your guide (expect swap out the MFC-240 with DCP-130, & downloaded the 130 files).

When i run 
```
sudo dpkg -i --force-architecture dcp130ccupswrapper-1.0.0-10.i386.deb
```
I get these errors.
```
 sudo dpkg -i --force-architecture dcp130ccupswrapper-1.0.0-10.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 107498 files and directories currently installed.)
Preparing to replace dcp130ccupswrapper 1.0.0-10 (using dcp130ccupswrapper-1.0.0-10.i386.deb) ...
/var/lib/dpkg/info/dcp130ccupswrapper.prerm: 3: /usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: not found
dpkg: error processing dcp130ccupswrapper-1.0.0-10.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/dcp130ccupswrapper.postinst: 3: /usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: not found
cp: cannot stat `/usr/share/cups/model/brdcp130c.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dcp130ccupswrapper-1.0.0-10.i386.deb

```

And when i go to install the printer, the DCP-130c driver/model isn't there. I've tried a few different models (with the cups driver) and none of them would print the test page.

I have ran this
```
sudo apt-get install lib32stdc++6
``` 

Any help would be much appreciated.

Thanks, Matt.

---

### Post by Seisen on 2007-10-17
Sorry I didn't get back with you before this but try this link I think this should fix your problem if you need help with it just let me know.

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#80]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#80")

---

### Post by Matthaeus on 2007-10-22
First, thanks for replying. I somehow didn't notice your response until today :)

I am having a lot of trouble carrying out the steps listed in your post.

> 
1-1. Comment out the lines which include "lpadmin" from:
/var/lib/dpkg/info/cupswrapperXXXX.prerm
/var/lib/dpkg/info/cupswrepperXXXX.postinst
1-2. Uninstall cupswrapper
dpkg -r cuprwrapperXXXX
dpkg --purge cupswrapperXXXX

I do not have these files 
> /var/lib/dpkg/info/cupswrapperXXXX.prerm
/var/lib/dpkg/info/cupswrepperXXXX.postinst 
Instead i have these (i assume they are the same/different name).
> /var/lib/dpkg/info/dcp130ccupswrapper.prerm
/var/lib/dpkg/info/dcp130ccupswrapper.postinst
lpadmin doesn't appear in any.

> @BSG:~$ sudo dpkg --purge dcp130ccupswrapper
dpkg: error processing dcp130ccupswrapper (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 dcp130ccupswrapper


So i did a force all remove/purge for these steps.

> 2-1.Unpack the package
dpkg --unpack cupswrapperXXXX.x.x.x-x.dpkg
I had to
> @BSG:~$ sudo dpkg --unpack --force-architecture dcp130ccupswrapper-1.0.0-10.i386.deb


> 2-2.Open /usr/local/Brother/cupswrapper/cupswrapperXXXXX to edit.
This folder does not exist!
I have /usr/local/Brother, but there's not cupswrapper

----------------------------------------

I started mucking around, and i extracted the cupswrapper.deb, and noticed there was a folder with matching file names to the steps above, so i moved the cupswrapper folder to /usr/local/Brother/cupswrapper/

After trying numerous things i
> sudo gedit /usr/local/Brother/cupswrapper/cupswrapperdcp130c
 
and changed
> 
lpadmin -p ${printer_name} -E -v $port -P /usr/share/cups/model/br${printer_model}.ppd
to
> lpadmin -p dcp130c -E -v $port -P /usr/share/cups/model/brdcp130c.ppd

then i did
> 
@BSG:~$ sudo sh /usr/local/Brother/cupswrapper/cupswrapperdcp130c

and it worked!! (i think i may have done a few other things....but i don't know if they actually did anything)

At some point i also installed the printer by just going sys->admin->printing->then selecting the auto-detected printer, AND then loading the brdcp130c.ppd driver which i copied from another folder (/usr/share/cups/model/) after executing the shell script.
For anyone who finds this post and is having trouble with their dcp-130c, 
[URL="http://ubuntuforums.org/showthread.php?t=278923&highlight=amd64+brother"]
this thread got the scanner going[/URL].

Printing is noticeably slower than windows....this isn't a big deal (i'm happy it's working), but is this typical? I think i have read about this.

Will all programs ie 64 & 32 bit now be able to use the printer, or is this something completely different? (I only have 64bit printing programs atm) Is there a way i can test 32 printing?

Thanks for your help Seisen.

---

### Post by McNee on 2007-11-20
Ok, I've done some searching and this is the only thread I find on the MFC240 - do these instructions work ok for 7.10 or is there anything new that I need to be aware of?

---

### Post by Seisen on 2007-11-23
I personally don't own the printer myself so as far as I know nothing has changed  but if you run  into problems feel free to post what kind of problems you are having.

---

### Post by TyLLy_4 on 2010-04-28
Trying this in 9.10 noetworked install. -Drivers dont appear in the list. cant print. 

get this error when i try to install cupswrapper. 

```
l30@l30-laptop:~/Desktop$ sudo dpkg -i --force-architecture mfc240ccupswrapper.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 200049 files and directories currently installed.)
Preparing to replace mfc240ccupswrapper 1.0.1-1 (using mfc240ccupswrapper.deb) ...
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Unpacking replacement mfc240ccupswrapper ...
Setting up mfc240ccupswrapper (1.0.1-1) ...
/usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: 70: cannot create /usr/share/cups/model/brmfc240c.ppd: Directory nonexistent
/usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: 274: cannot create /usr/share/cups/model/brmfc240c.ppd: Directory nonexistent
chmod: cannot access `/usr/share/cups/model/brmfc240c.ppd': No such file or directory
cp: cannot stat `/usr/share/cups/model/brmfc240c.ppd': No such file or directory
chmod: cannot access `/usr/share/ppd/brmfc240c.ppd': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 


```

Help will be uch appreciated thx

---

### Post by Cone on 2010-04-28
Don't have much time to reply right now, but in the places where it tells you the directory doesn't exist, create the directory and then try installing again.

---

### Post by TyLLy_4 on 2010-04-28
Errr that dosent make sense ... Inf you notice its telling me that it cant find that .pdd file not the directory. I folowed your instusctions and now i get this. 

```
l30@l30-laptop:~/Desktop$ sudo dpkg -i --force-architecture mfc240ccupswrapper.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 200160 files and directories currently installed.)
Preparing to replace mfc240ccupswrapper 1.0.1-1 (using mfc240ccupswrapper.deb) ...
lpadmin: The printer or class was not found.
rm: cannot remove `/usr/share/cups/model/brmfc240c.ppd': Is a directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Unpacking replacement mfc240ccupswrapper ...
Setting up mfc240ccupswrapper (1.0.1-1) ...
rm: cannot remove `/usr/share/cups/model/brmfc240c.ppd': Is a directory
/usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: 70: cannot create /usr/share/cups/model/brmfc240c.ppd: Is a directory
/usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: 274: cannot create /usr/share/cups/model/brmfc240c.ppd: Is a directory
cp: omitting directory `/usr/share/cups/model/brmfc240c.ppd'
chmod: cannot access `/usr/share/ppd/brmfc240c.ppd': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

```

Pleeeeease help 
Pretty pleaseee (with sprinkles on top):lolflag:

---

### Post by Cone on 2010-04-29
Sorry, guess I wasn't clear enough (and sorry for slow response, busy with tons of school work).

```

mkdir /usr/local/Brother/Printer/mfc240c/cupswrapper/ -p
mkdir /usr/share/cups/model/ -p

```

Probably will need to sudo those.

What I'm guessing you did was

```

mkdir /usr/share/cups/model/brmfc240c.ppd -p

```
in which case you would likely need to remove the directory with that name.

(Also, I did not realize you could have directories with dots in the middle, though I guess it makes sense with the ones with dots at the start.)

Let me know if it does/doesn't help. :)

---

### Post by TyLLy_4 on 2010-04-30
> **Cone said:**
> Just did a fresh install of Ubuntu to see if it was something with my set up.  Installed Ubuntu, installed drivers, and that's it.  Same problem.

Could it be the whole Whatever -> PostScript -> GhostScript to convert to native thing that's messing it up?  The processes never max out my CPU usage.

Thank you CONE!! 

That solved my problem! i can now print! What a hassle, im almost sorry i picked a 64bit distro. well .. except that im running twice as fast as my XP based :D 

Thanks so very much to you and everybody else that posted here.

---

