---
title: "HOWTO : HUAWEI E630 Data Card (HSDPA) PCMCIA of 3 (Hong Kong) on Ubuntu 6.10"
date: 2006-12-29
forum: Outdated Tutorials &amp; Tips
---

### Post by samiux on 2006-12-29
**HOWTO : HUAWEI E630 Data Card (HSDPA) PCMCIA of 3 (Hong Kong) on Ubuntu 6.10**

Version : 1.1 (updated on 6th January, 2007)
Author : Samiux, Hong Kong

_**Telecom Company**_
3 : [www.three.com.hk]("http://www.three.com.hk")
Plan : Turbo 3G [EasyPlus]("http://www.three.com.hk/website/template?pageid=38200&lang=eng") - minimum $98-HK for 50MB and maximum is $488-HK for unlimited usage.  The plan will automatically adjust the charge that depends on the usage.  

**_Hardware_**
Datacard Manufacturer : Option (OEM by HUAWEI)
Serial Number : Starts with &#8220;EA&#8221;
Speed : DL 3.6Mbps; UL 384kbps

**_Software_**
Operating system : Ubuntu 6.10 (Kernel 2.6.17-10-generic)
Signal program : comgt 0.32
Dial up program : KPPP

**_Installation_**
**Step 1 : Get the KPPP**

[COLOR="Red"]sudo apt-get install kppp[/COLOR]

**Step 2 : Get the datacard signal program**

comgt :
[URL="http://sourceforge.net/project/showfiles.php?group_id=174961"]http://sourceforge.net/project/showfiles.php?group_id=174961
[/URL]

**Step 3 : Compile and install comgt**

[COLOR="Red"]make
sudo make install[/COLOR]

**Step 4 : Make usbserial to work in high speed**

Reason : Since default packet setting of usbserial is in small size, the following steps to be applied to increase the speed of the usbserial.

[COLOR="Red"]sudo modprobe usbserial maxSize=2048
sudo depmod -a[/COLOR]

*** I am not sure if the usbserial.c has not been patched will work.  You can simply ignore this step. ***

**Step 5 : Edit kppprc**

[COLOR="Red"]nano /home/samiux/.kde/share/config/kppprc[/COLOR]
(assume the user is &#8220;samiux&#8221;)
*** If you do not have ".kde/share/config" directories, you simply run the kppp once and the said directories will be created. ***

*Copy the following to the kppprc and save with ctrl-o and ctrl-x :*
```
[Account0]
AccountingEnabled=0
AccountingFile=
Authentication=4
AutoDNS=1
AutoName=0
BeforeConnect=xterm -e /usr/local/bin/comgt -x -d /dev/ttyUSB0
BeforeDisconnect=
CallbackPhone=
CallbackType=0
Command=
DNS=
DefaultRoute=1
DisconnectCommand=
Domain=
ExDNSDisabled=0
Gateway=0.0.0.0
IPAddr=0.0.0.0
Name=HUAWEI-3
Password=pass
Phonenumber=*99#
ScriptArguments=
ScriptCommands=
StorePassword=1
SubnetMask=0.0.0.0
Username=user
VolumeAccountingEnabled=0
pppdArguments=defaultroute,replacedefaultroute,crtscts,modem,noipdefault,usepeerdns,novj,debug

[Account1]
pppdArguments=

[General]
AutomaticRedial=0
DefaultAccount=HUAWEI-3
DefaultModem=GT_3G_EDGE_HSDPA
DockIntoPanel=1
NumberOfAccounts=2
NumberOfModems=3
PPPDebug=0
QuitOnDisconnect=1
RedialOnNoCarrier=0
ShowLogWindow=1

[Graph]
Background=255,255,255
Enabled=true
InBytes=0,0,255
OutBytes=255,0,0
Text=0,0,0

[Modem0]
AnswerResponse=CONNECT
AnswerString=ATA
BusyResponse=BUSY
BusyWait=0
ConnectResponse=CONNECT
DLPResponse=DIGITAL LINE DETECTED
Device=/dev/ttyUSB0
DialString=ATD
Enter=CR
EscapeGuardTime=50
EscapeResponse=OK
EscapeString=+++
FlowControl=Hardware [CRTSCTS]
HangUpResponse=OK
HangupString=+++ATH
InitDelay=50
InitResponse=OK
InitString=AT+CFUN=1
InitString1=AT+CGDCONT=1,"IP","","",0,0
Name=GLOBETROTTER3G
NoCarrierResponse=NO CARRIER
NoDialToneDetection=ATX3
NoDialToneResp=NO DIALTONE
PreInitDelay=50
RingResponse=RING
Speed=460800
Timeout=82
ToneDuration=70
UseLockFile=1
Volume=0
VolumeHigh=M1L3
VolumeMedium=M1L1
VolumeOff=M0L0
WaitForDialTone=1

[Modem1]
AnswerResponse=CONNECT
AnswerString=ATA
BusyResponse=BUSY
BusyWait=0
ConnectResponse=CONNECT
DLPResponse=DIGITAL LINE DETECTED
Device=/dev/ttyS4
DialString=ATD
Enter=CR
EscapeGuardTime=50
EscapeResponse=OK
EscapeString=+++
FlowControl=Hardware [CRTSCTS]
HangUpResponse=OK
HangupString=+++ATH
InitDelay=100
InitResponse=OK
InitString=AT+cfun=1
InitString1=at+cgdcont=1,"IP","internet"
Name=GTEDGE
NoCarrierResponse=NO CARRIER
NoDialToneDetection=AT
NoDialToneResp=NO DIALTONE
PreInitDelay=52
RingResponse=RING
Speed=57600
Timeout=60
ToneDuration=70
UseLockFile=1
Volume=1
VolumeHigh=
VolumeMedium=
VolumeOff=
WaitForDialTone=0

[Modem2]
AnswerResponse=CONNECT
AnswerString=ATA
BusyResponse=BUSY
BusyWait=0
ConnectResponse=CONNECT
DLPResponse=DIGITAL LINE DETECTED
Device=/dev/modem
DialString=ATD
Enter=CR
EscapeGuardTime=50
EscapeResponse=OK
EscapeString=+++
FlowControl=Hardware [CRTSCTS]
HangUpResponse=OK
HangupString=+++ATH
InitDelay=100
InitResponse=OK
InitString=AT+cfun=1
InitString1=at+cgdcont=1,"IP","internet"
Name=GT_3G_EDGE_HSDPA
NoCarrierResponse=NO CARRIER
NoDialToneDetection=AT
NoDialToneResp=NO DIALTONE
PreInitDelay=52
RingResponse=RING
Speed=460800
Timeout=60
ToneDuration=70
UseLockFile=1
Volume=1
VolumeHigh=
VolumeMedium=
VolumeOff=
WaitForDialTone=0

[WindowPosition]
WindowPositionConWinX=487
WindowPositionConWinY=498
WindowPositionStatWinX=811
WindowPositionStatWinY=454
```

**Step 6 : Create ip-up.local**

*Reason* : Since 3 (Hong Kong) is using Microsoft server, the data card cannot detect the DNS correctly under Linux.  Thus, the following steps to be applied.

Primary DNS 	203.145.64.200
Secondary DNS 	202.67.240.222

*Tip* : If you found the 3's DNSs are too slow for you, you can simply use your fastest DNSs instead of 3.
 
[COLOR="Red"]sudo nano /etc/ppp/ip-up.local[/COLOR]

[I]Copy the following to the file and save by ctrl-o and ctrl-x.
[/I]
```
# Location : /etc/ppp/ip-up.local
PATH=/sbin:/usr/sbin:/bin:/usr/bin
export PATH
echo "created by pppd via ip-up.local" > /etc/resolv.conf
echo "nameserver 203.145.64.200" >> /etc/resolv.conf
echo "nameserver 202.67.240.222" >> /etc/resolv.conf
chmod go+r /etc/resolv.conf
```

[COLOR="Red"]sudo chmod +x /etc/ppp/ip-up.local[/COLOR]

**_Connecting to internet_**

Execute the KPPP to dial up

At the [B]<Application> <Internet> <KPPP> <GLOBETROTTER3G>
[/B]
Before pressing the &#8220;**Connect**&#8221; button, select the &#8220;**Configure**&#8221;.  Go to **<Misc>** and select the &#8220;**Dock into panel on connect**&#8221;.

**_Disconnect from internet_**

At the panel on the top of the screen, left click the icon (a blue world with 2 lights) and select &#8220;**disconnect**&#8221;.

*Tip* : Before packing your notebook computer, you should take out the data card from the slot.  

**_Remarks_**

If I have money and time, I will test the HUAWEI E220 USB modem.  

Finally, enjoy surfing the internet anywhere at anytime!!!

[B][U]HUAWEI E220 USB Modem
[/U][/B]
For USB modem, I think that driver is not required also.  (However, I have not try it).
[HUAWEI E220 HOWTO]("http://joergweis.wordpress.com/2007/01/03/huawei-e220-and-ubuntu-610/")

Samiux
Created on 30th December, 2006 (Version 1.0)

Update note (Version 1.1) (6th January, 2007) :
- cancelled the driver installation
- updated the kppprc script
- added comment to some instructions
- added red colour on commands

---

### Post by detroit/zero on 2008-01-01
> **_Installation_**
**Step 1 : Get the KPPP**

[COLOR=Red]sudo apt-get install kppp[/COLOR]

**Step 2 : Get the datacard signal program**

comgt :
[URL="http://sourceforge.net/project/showfiles.php?group_id=174961"]http://sourceforge.net/project/showfiles.php?group  _id=174961
[/URL]

**Step 3 : Compile and install comgt**

[COLOR=Red]make
sudo make install[/COLOR]

There is some info missing between steps two and three.

I put the downloaded files into a folder at ~/iplus-enable   and when trying to do make i get the message 
```
make: *** No targets specified and no makefile found
```

Where is this file supposed to go in order for this to work?

---

### Post by detroit/zero on 2008-01-02
Anyone?

Bueller? Bueller?

The rest looks pretty straightforward, I just need to know where to unpack those
 files...

---

### Post by detroit/zero on 2008-01-04
Hello?

---

### Post by detroit/zero on 2008-01-06
Lost.

Need... help..

Can't.. hold on... any.. longer.

---

### Post by detroit/zero on 2008-01-07
Is there anybody who's used this how-to or maybe found another way to make this work?

This is killing me here.

---

### Post by _blech on 2008-03-04
Hi, did you tried something described here? [http://www.tectonic.co.za/wordpress/?p=1596](http://www.tectonic.co.za/wordpress/?p=1596)

---

### Post by lkirwan on 2008-05-10
Article assumes that you have the below step completed before installing kppp in step 1.

pre-Step 1: Get the compiler, kernel headers

sudo apt-get install build-essential
sudo apt-get install linux-headers

[B]
Installation
Step 1 : Get the KPPP
[/B]
sudo apt-get install kppp

That should help you detroit/zero.

---

### Post by detroit/zero on 2008-05-11
Actually it doesn't. But, as luck would have it, Hardy Heron has built in support for the device. 

Thanks anyways!

---

### Post by lkirwan on 2008-06-06
Just a quick note, for all the Irish people out there on Three.ie. 

[B]   APN:               3ireland.ie
   Static DNS Servers:   172.31.140.69, 172.30.140.69[/B]

This helped resolve my issue of pppd modem hanging up, ie kppp exit status: 16 

Hope this will be of some benefit to someone out there.

---

