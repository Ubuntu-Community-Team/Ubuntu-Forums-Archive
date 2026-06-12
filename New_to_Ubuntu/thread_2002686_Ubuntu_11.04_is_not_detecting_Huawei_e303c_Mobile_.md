---
title: "Ubuntu 11.04 is not detecting Huawei e303c Mobile broadband modem"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by umashblaze on 2012-06-13
Hi techies

Cheers to you. 
Just help me out here for getting my Mobile broadband connection activated in Ubuntu 11.04. I've tried and become tired of trying various options myself and solutions found in lot many forums. 

***_Tech details_***:
OS: Ubuntu 11.04
USB Device: Huawei e303c Data-card
Operator: Tata Docomo 3G (Location: Pune, India)

***_Things I tried_***:
- Installed the driver tool (Mobile Partner Linux) that came-up with the Device.
- Installed apps like usb_modeswitch, wvdial, gnomeppp, sakis3G and followed the procedure gievn in the forums.
- Actually, when '**lsusb'** cmd is fired, it is showing my Huawei device with its DeviceID:VendorID. But when the network manager is used to set-up a new mobile broadband connecion(by selecting '**Add**'), it is not showing the 'Huawei device'. Still, I forwarded with the default (Any device) option. But, in no way, the device is getting recognized. Also when the device is inserted, the installed 'Mobile-Partner' is not coming-up (In programs too, it is not there to open manually).  

Show me a solution.

Thanks in advance :)

---

### Post by praneeth900 on 2012-08-27
Hi, I have same issue. Please help.

---

### Post by Rajasekar Kudumban on 2012-10-05
Hi Guys,
Sorry for answering this much late. I guess that you have installed linux drivers given with huawei?
Actually usb_modswitch is the one,which switches a dongle to either storage or modem.
It have certain rules to behave according to the devices connected.
When u install the given driver, it will replace the default rules(actually the rules will be in rules.d folder) with the specific huawei one.
All u have to do is to restore the default rules of usb_modeswitch.
If u got ur device detected in **lsusb **then the problem can be solved easily.
Follow the steps:
1.Download latest usb_modeswitch from here
 [http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-1.2.4.tar.bz2](http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-1.2.4.tar.bz2)
2. Then download usb_modeswitch data from here 
[http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-data-20120815.tar.bz2](http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-data-20120815.tar.bz2)
3.Extract them.
4.Open terminal
5.Change to respective directory
6.First run make file in usb_modeswitch folder,by using command sudo make install-static(If ur system doesnt have TCL u should add -static)
7.Then also install data file too.
8.If u have problem installing, refer readme given with them.
9.After installing,simply restart and u will find ur device detected in network configuration.
P.S: I also from India(Tamilnadu) and bought huawei303c and made the same mistake.
After extensive research i founded this solution. If u have any doubts,reply.All d best.;)

---

### Post by greattime on 2012-12-30
Hi i have the same problem, brought huawei e303c recently but not able to connect to internet using it in ubuntu 10.04. I had installed usb_modeswitch and still not able to connect my lsusb result is

[COLOR=Navy]Bus 001 Device 003: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard[/COLOR]

i think it is being detected as modem,but while installing the driver it was showing lot of errors that i posted under another thread please look at it here [http://ubuntuforums.org/showthread.php?t=2051295](http://ubuntuforums.org/showthread.php?t=2051295)
is there any dependencies that i should install to solve those errors,and in network manager, when we choose mobile broadband the huawei device is not found. So i tried to connect it using wvdial , it is succesfully connecting using wvdial but is not able to browse the net, or no data flow, the wvdial output i am giving here

[COLOR=Navy]--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
CONNECT 7200000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Dec 31 00:48:13 2012
--> Pid of pppd: 3084
--> Using interface ppp0
--> local  IP address xxx.xx.xxx.xx
--> remote IP address xx.xx.xx.xx
--> primary   DNS address xxx.xxx.xxx.x
--> secondary DNS address xxx.xxx.xxx.xxx
[/COLOR]
hope you can help me out.
[]("http://ubuntuforums.org/showthread.php?t=2051295")

---

