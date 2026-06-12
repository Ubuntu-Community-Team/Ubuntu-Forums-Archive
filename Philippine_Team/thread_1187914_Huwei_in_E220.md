---
title: "Huwei in E220"
date: 2009-06-15
forum: Philippine Team
---

### Post by llemm on 2009-06-15
Hi I am using Huawei E220 modem from Sun Broadband (/dev/ttyUSB0) and I have been using it on Ubuntu 8.04 using wvdial. The Problem is after I Updated the Kernel through Software update wvdial cant see the Modem always, sometimes it worked but  I have to reboot several times just to let the wvdial see the /dev/ttyUSB0
here is my log. Note I can connect to the /dev/ttyUSB0 using wvdial but after I reboot I wont be able connect it again.

root@rommell-desktop:~# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
root@rommell-desktop:~# lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
root@rommell-desktop:~# wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   USB0 
ttyUSB1<Info>: Exec format error
Modem Port Scan<*1>: USB1 
ttyUSB2<Info>: Exec format error
Modem Port Scan<*1>: USB2 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

root@rommell-desktop:~# wvdial defaults
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
root@rommell-desktop:~# 

rommell@rommell-desktop:~$ sudo mknod /dev/ttyUSB0 c 188 0
mknod: `/dev/ttyUSB0': File exists
rommell@rommell-desktop:~$ modprobe -r option usbserial
FATAL: Module usbserial is in use.
rommell@rommell-desktop:~$ 

Here is my wvdial configuration

root@rommell-desktop:~# more /etc/wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99# 
Password = ; 
Username = ;

I hope someone can give me an idea what to do here.

Thanks ^_^

---

### Post by GeorgeVita on 2009-06-15
Hi **llemm**,
Huawei E220 supposed to be a "standard" 3G modem. Most developers have access to this and I believe they test it before finalizing a kernel version. The 'bad' thing is that wvdial and some drivers for USB peripherals are not kept as a backwards compatible steady point (ex. usbserial). Finally most developers think that you have at least an ethernet internet connection to install/update/fix your O.S.

For your case, please do some tests and post the results to follow up:

- From terminal: **uname -a** (to see the actual kernel version)
- Boot without the modem, wait for the system to load
- From terminal try **lsusb** and then **ls /dev/ttyU***
- attach the modem, wait 15 seconds, retry **lsusb** and **ls /dev/ttyU***
- DO NOT RUN any program like wvdial, Network Manager, etc
- detach the modem, wait 5 seconds
- try again **lsusb** and **ls /dev/ttyU***

Normal & good condition is:
lsusb will list the modem only when attached
ls/dev/ttyU* must show /dev/ttyUSB0 /dev/ttyUSB1 and possibly /dev/ttyUSB2 ONLY when the modem is attached (always the same list)

Attach again the modem and try: **dmesg**
At the last 10-15 lines you can find system activity as modem recognition, driver used and /dev/ttyU... port creation.

With a newer version as 8.10 and 9.04 version 0.7.x of Network Manager included which becomes "usable" with 3G modems (especially Huawei). More stable to what you know (using 8.04) is 8.10.

If you would like to use **wvdial** you must take care NOT RUN two connecting programs (as wvdial, gnome-ppp) because /dev/ttyUSB0 will be "used/holded" by the first one. 

A typical **/etc/wvdial.conf** is:

[B][Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = pass
Phone = *99#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","internet"[/B]

Note: Init3 line sets the APN and may vary according to your provider's specs. Ask your provider or post country/provider name.

Regards,
George

---

### Post by jepong on 2009-06-15
sun broadband ba?

pls change APN to **fbband**; this work by using the mobile broadband in network manager.

I use wvdial and wvdialconf with Kubuntu since mobile broadband in Kubuntu sucks bigtime... please use sudo when running wvdial and wvdialconf.

---

### Post by llemm on 2009-06-18
Hi GeorgeVita and Jepong thanks for the reply and sorry for my late response. I only use wvdial for my dialer and nothing else. I would like to use 8.10 but as in my experience 8.04 is so much stable than 8.10 so I would like to stick with 8.04. But do you think this is the fault of a kernel? I did what you told me to do here is the output

and Jepong I do not use 8.10 I use wvdial in 8.04 so the APN stuff is not needed. ^_^

After I reboot(I only remove the module but the cable is still inserted)

rommell@rommell-desktop:~$ uname -a
Linux rommell-desktop 2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686 GNU/Linux
rommell@rommell-desktop:~$ lsusb; date
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0e8f:0002  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Fri Jun 19 00:28:23 PHT 2009
rommell@rommell-desktop:~$ 

After I inserted the modem 

rommell@rommell-desktop:~$ lsusb; date;
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0e8f:0002  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Fri Jun 19 00:29:02 PHT 2009

last lines of dmesg

rommell@rommell-desktop:~$ 
[   91.292188] vmnet1: no IPv6 routers present
[   91.511865] vmnet8: no IPv6 routers present
[  318.314415] usb 2-2: new full speed USB device using ohci_hcd and address 2
[  318.581969] usb 2-2: configuration #1 chosen from 1 choice
[  318.736201] usbcore: registered new interface driver usbserial
[  318.736874] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  318.737610] usbcore: registered new interface driver usbserial_generic
[  318.737616] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  318.753697] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for airprime
[  318.753752] airprime 2-2:1.0: airprime converter detected
[  318.753983] usb 2-2: airprime converter now attached to ttyUSB0
[  318.754119] usb 2-2: airprime converter now attached to ttyUSB1
[  318.754221] usb 2-2: airprime converter now attached to ttyUSB2
[  318.754238] usbcore: registered new interface driver airprime
[  318.786324] usbcore: registered new interface driver libusual
[  361.566626] usb 2-2: USB disconnect, address 2
[  361.567316] airprime ttyUSB0: airprime converter now disconnected from ttyUSB0
[  361.567620] airprime ttyUSB1: airprime converter now disconnected from ttyUSB1
[  361.567932] airprime ttyUSB2: airprime converter now disconnected from ttyUSB2
[  361.567968] airprime 2-2:1.0: device disconnected
[  403.341734] usb 2-2: new full speed USB device using ohci_hcd and address 3
[  403.608177] usb 2-2: configuration #1 chosen from 1 choice
[  403.611176] airprime 2-2:1.0: airprime converter detected
[  403.612013] usb 2-2: airprime converter now attached to ttyUSB0
[  403.612672] usb 2-2: airprime converter now attached to ttyUSB1
[  403.613300] usb 2-2: airprime converter now attached to ttyUSB2
rommell@rommell-desktop:~$ date;
Fri Jun 19 00:30:12 PHT 2009
rommell@rommell-desktop:~$

---

### Post by GeorgeVita on 2009-06-18
Hi **llemm**
from terminal: **sudo gedit /etc/wvdial.conf**
copy following lines (all within 'code' window) and paste into gedit window:
```
[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Username = user
Password = pass
Phone = *99#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","fbband"
```
Save and Exit from gedit.

To connect: **sudo wvdial**

In any error, post here ALL terminal output including your commands.

APN is for your provider not for the O.S., some providers don't need it because they have only one data service (if not work, try: minternet).

Regards,
George

P.S. with your test everything seems OK. If you realize any problem another time, try commands **lsusb**, **ls/dev/ttyU*** and **dmesg** to see any difference. Especially **dmesg** that will show you if ttyUSB0-1-2 are created.

---

### Post by llemm on 2009-06-22
Hi again George and sorry for my super late response ^_^ and thank you for the reply.

Good News! I used the configuration you gave me and used it for two days and the error never appeared again. So you think its my Configuration that caused the error? 

If Ever the error appears again can I update this Thread?

Thanks George and Jepong you are the Man! Mabuhay!

Thanks

llemm

---

### Post by GeorgeVita on 2009-06-22
Hi and ... Well Done!

I think the problem was into **/etc/wvdial.conf** (baud rate, APN). In any case you face a problem (ex. after an update!) post heere or send a private message!

Regards,
George

---

### Post by llemm on 2009-06-23
Hi George the error appered again but now I know the Culprit.

I Dual boot my PC with XP. I use XP's built in dialer to connect to the Internet. What happens is when I forgot to disconnect and then boot to Ubuntu the device wont let me. But when I boot back to XP, connect and then disconnect then boot back to Ubuntu Everything works fine.

So the problem is with the XP software. Everything was back to Normal when I use the ISP's Software to connect even if I forgot to disconnect I could still connect to the Internet through wvdial.

Thanks George for the time you give. the /etc/wvdial.conf configuration you gave me is valuable because its faster than my previous configuration in speed and dialing time.

Mabuhay ka!
llemm

---

