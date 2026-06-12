---
title: "Help! Intel 537EP Modem-Ubuntu Hardy"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by mcgrg6 on 2008-11-07
Problems installing Intel537EP modem 

Hi, I posted this request in "Network & Wireless" but received no replies so maybe it got lost.   I am completely new to the Linux OS. As a result of a hard drive failure on a relatives Dell Dimension 3000 I am taking the opportunity to try Ubuntu Hardy. All goes well but I need to get the system to recognise & use my dial-up modem. Anyway I ran the scanmodem (report below) and found the modem is the INTEL537EP. I then downloaded 

intel537ep-hardy_2-Philippe.Vouters_i386.deb

and clicked on it and went through what looked like a loading process. No one else seems to go this route they all seem to go to a command prompt option with tar files and sudo commands?  
The message I got back after my approach in a file called success.txt was

Congratulations. If you are reading this file then your modem driver should be
installed properly. Remember to reboot with the proper kernel if the driver was
not able to be loaded.

-Quick Info

Your Modem should be accessible from both these locations:
/dev/537
/dev/modem

So that all looked positive but when I tried connecting with "Gnome PPP" the reply is cannot open modem. I can find no way to get the system to dial up my isp or recognise the modem.  It seems as if a bridging file or executeable is not finding the modem on /dev/modem.  I cannot see the /dev/537 option anywhere.  I am connecting to an ISP in the united kingdom is there some configuration issue?

So any help appreciated - but please note I am new to this OS and the ways of entering commands. I do know how to access the terminal and I have roamed around. 

Regards,
Mike

MODEMDATA.TXT report

-------------------------- System information ----------------------------
CPU=i686, 
Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008
scanModem update of: 2008_10_24
The modem symbolic link is /dev/modem -> /dev/537
There are no blacklisted modem drivers in /etc/modprobe* files 
Attached USB devices are:
ID 0ace:1215 ZyDAS WLA-54L WiFi
ID 058f:6387 Alcor Micro Corp. Transcend JetFlash 110 USB 2.0 Flash Drive (2GB)
ID 413c:2010 Dell Computer Corp. 
ID 413c:1003 Dell Computer Corp. 
ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse

USB modems not recognized

For candidate card in slot 01:01.0, firmware information and bootup diagnostics are:
PCI slot PCI ID SubsystemID Name
---------- --------- --------- --------------
01:01.0 8086:1080 1028:1000 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI 

Modem interrupt assignment and sharing: 
--- Bootup diagnostics for card in PCI slot 01:01.0 ----
[ 23.314637] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 22 (level, low) -> IRQ 16
[ 23.315027] 0000:01:01.0: ttyS1 at I/O 0xde08 (irq = 16) is a 16450
[ 23.315257] 0000:01:01.0: ttyS2 at I/O 0xde10 (irq = 16) is a 8250
[ 23.315468] 0000:01:01.0: ttyS3 at I/O 0xde18 (irq = 16) is a 16450
[ 23.315536] Couldn't register serial port 0000:01:01.0: -28

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 01:01.0:
Modem chipset detected on
NAME="Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI "
CLASS=0703
PCIDEV=8086:1080
SUBSYS=1028:1000
IRQ=16
IDENT=INTEL537EP

For candidate modem in: 01:01.0
0703 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI 
Primary device ID: 8086:1080
Support type needed or chipset: INTEL537EP

----------------end Softmodem section --------------
> Additional information
> =============
> 
> MODEM
> 
> eileen@eileen-desktop:~$ lspci | grep -e "537" -e
> "536" 
> 01:01.0 Modem: Intel Corporation FA82537EP 56K V.92
> Data/Fax Modem PCI (rev 04) 
> eileen@eileen-desktop:~$ 
> 
> KERNEL
> 
> eileen@eileen-desktop:~$ uname -r 
> 2.6.24-21-generic 
> eileen@eileen-desktop:~$
> 
> WVDIAL RESULT
> 
> eileen@eileen-desktop:~$ wvdial 
> --> WvDial: Internet dialer version 1.60 
> --> Cannot open /dev/modem: No such file or directory 
> --> Cannot open /dev/modem: No such file or directory 
> --> Cannot open /dev/modem: No such file or directory 
> 
> SERIAL PORT SCAN FOR MODEM
> 
> eileen@eileen-desktop:~$ sudo wvdialconf /etc/wvdial.conf 
> Editing `/etc/wvdial.conf'. 
> 
> Scanning your serial ports for a modem. 
> 
> ttyS0: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600
> baud 
> ttyS0: ATQ0 V1 E1 -- failed with 9600 baud, next try:
> 115200 baud 
> ttyS0: ATQ0 V1 E1 -- and failed too at 115200, giving up. 
> ttyS1: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600
> baud 
> ttyS1: ATQ0 V1 E1 -- failed with 9600 baud, next try:
> 115200 baud 
> ttyS1: ATQ0 V1 E1 -- and failed too at 115200, giving up. 
> ttyS2: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600
> baud 
> ttyS2: ATQ0 V1 E1 -- failed with 9600 baud, next try:
> 115200 baud 
> ttyS2: ATQ0 V1 E1 -- and failed too at 115200, giving up. 
> ttyS3: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600
> baud 
> ttyS3: ATQ0 V1 E1 -- failed with 9600 baud, next try:
> 115200 baud 
> ttyS3: ATQ0 V1 E1 -- and failed too at 115200, giving up. 
> 
> 
> Sorry, no modem was detected! Is it in use by another
> program? 
> Did you configure it properly with setserial? 
> 
> Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial) 
> 
> If you still have problems, send mail to .

---

### Post by Mark_in_Hollywood on 2008-11-07
Please post the output of your wvidal.conf file.

To get that, 

alt-F2

enter this line:

gksudo gedit /etc/wvdial.conf

when gedit opens the file, click on some blank area then:

ctrl-a

all the text should highlite.

do

ctrl-c

that will copy the text, come back to your thread there and post it.

We can go from there. I will monitor this thread for a few days and try to help.

Also, I looked at:

[http://vouters.dyndns.org:8080/Intel/](http://vouters.dyndns.org:8080/Intel/)

If you have not, then please read the 	Intel-Readme.txt at that site. Also download the most recent driver. The readme will explain how to install the driver. Before you do that, we must ask others if you need compilations software, e.g., build-essential or some such. I can't help in that area, (I'm not geek enough?!!) 

Also, please see this (brief) post:

    * DialupModemHowto
    * Intel537EP

[https://help.ubuntu.com/community/DialupModemHowto/Intel537EP](https://help.ubuntu.com/community/DialupModemHowto/Intel537EP)

and

Reading at the Google Groups for Ubuntu Modem Drivers for the 537EP, I don't see an intrepid driver as yet. You can try to Hardy driver.

---

### Post by mcgrg6 on 2008-11-07
Thanks for the reply. 

I will read through the links, here the output from the command,

[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes

one other point..whenI go into dev there is something called "modem" with a red X.  When I look at properties it ays this is,

Type:  link (broken)
Link Target: /dev/537

Important ?

Thanks again,
Mike

---

### Post by Mark_in_Hollywood on 2008-11-07
> **mcgrg6 said:**
> Thanks for the reply. 

I will read through the links, here the output from the command,

[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes

one other point..whenI go into dev there is something called "modem" with a red X.  When I look at properties it ays this is,

Type:  link (broken)
Link Target: /dev/537

Important ?

Thanks again,
Mike

As for the broken link, I can't say. I'm not a programmer. I do know a little about wvdial 'though.

You need to put your info in the lines above. I think you should put them in this order:

Name
Password
Phone
New PPPD = yes

if that doesn't work, try putting phone first. I've got to be away from the computer for a 2 to 3 hours for chores, I'll be back after that.

---

### Post by mcgrg6 on 2008-11-09
Hi there,

Apologies for not replying sooner but its been a busy weekend.

I tried moving the lines around but no luck.  When I Click on the Gnome PPP dialer and try to connect it seems unable to even find the modem?  

regards 

Mike

---

### Post by Mark_in_Hollywood on 2008-11-09
Have a close look at:

[http://archives.linmodems.org/26630](http://archives.linmodems.org/26630)

They talk specifically about your modem. 

I don't know how to fix the broken link. I suggest a new post with the subject:

Fix broken link for dial-up modem

Sorry I couldn't be more help.

---

### Post by Bartender on 2008-11-10
mcg -
I hate to break the news to you, but dial-up is a black hole with Ubuntu or most any Linux distro.
Even if you get it to work, which can be a project from hell.
The reason is, Ubuntu updates are often quite large.  In the last year I've seen several in the 30 to 40MB range, and one that was 90+MB.  Not fun on dial-up.
here's my dial-up thread from a while back.  I don't think things have changed much.
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)
If you want to get dial-up working without loss of blood, cruise eBay or rifle the neighbors' closets and find a USR external or one of those AOL-Actiontec serial/USB modems.

I've found the best solution to dial-up:  buy a Centrino laptop, install Ubuntu, then go into town and find some wi-fi.  Problem solved.  :)

---

### Post by mcgrg6 on 2008-11-12
Hi there,

Thank you all I am taking your advice and giving up at this point.  Options are to switch back to XP or arrange Broadband at the location as the PC did work on my BB system.  Understandable that dial-up is difficult to confifure as it is now pretty outdated.

Thanks again,
Mike

---

### Post by Sepero on 2008-11-25
Hey there, I package and release the Ubuntu 536ep and 537ep modems here:
[http://groups.google.com/group/ubuntu-modems](http://groups.google.com/group/ubuntu-modems)

If you decide to try out your modem again, you can contact us for help anytime. There is a Frequently Asked Questions page that should solve most common technicalities. We have just released the new packages for Ubuntu Intrepid.

Take care

---

### Post by mcgrg6 on 2008-11-27
Thank you for the advice on the Intel modem.  As I say I am moving the PC user to broadband.  We continue with Ubuntu and given time I am sure there wil be further questions but not on this subject.

---

