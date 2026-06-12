---
title: "HOWTO : Vodafone Datacard (HSDPA) PCMCIA on Ubuntu 6.10"
date: 2006-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by samiux on 2006-11-28
Version : 1.0 (dated 29th November, 2006)
Version : 1.1 (dated 6th January, 2007)
Author : Samiux, Hong Kong

**_Hardware_**
Datacard Manufacturer : Option
Serial Number : Starts with &#8220;NL&#8221;

**_Software_**
Operating system : Ubuntu 6.10 (Kernel 2.6.17-10-generic)
Drivers : nozomi 2.1-1 and comgt 0.32
Compiler : build-essential
Kernel headers : linux-headers-2.6.17-10 and linux-headers-2.6.17-10-generic
Dial up program : KPPP

**_Installation_**
**Step 1 : Get the compiler, kernel headers and KPPP**

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r'
sudo apt-get install kppp
sudo ln -s /lib/modules/2.6.17-10/build /usr/src/linux-headers-2.6.17-generic

**Step 2 : Get the datacard drivers**

nozomi :
[http://packages.debian.org/unstable/net/nozomi-source]("http://packages.debian.org/unstable/net/nozomi-source")

comgt :
[http://sourceforge.net/project/showfiles.php?group_id=174961]("http://sourceforge.net/project/showfiles.php?group_id=174961")

**Step 3 : Compile and install nozomi**

*Exract the nozomi-2.1.orig.tar.gz and nozomi-2.1-1.diff.gz by double click the files.*

[I]Apply the patch at the working directory via terminal, e.g. /home/samiux
[/I]
patch -p0 < nozomi-2.1-1.diff

*Change to the nozomi-2.1.orig directory and comile*

cd nozomi-2.1.orig
make
sudo make install

***(if you get an error message like no such file, do the following commands)
sudo cp nozomi.ko lib/modules/2.6.17-10-generic/kernel/drivers/pci/hotplug/
sudo depmod -a

**Step 4 : Compile and install comgt**

make
sudo make install

**Step 5 : Edit kppprc**

gedit /home/samiux/.kde/share/config/kppprc
(assume the user is &#8220;samiux&#8221;)

*** If you do not have ".kde/share/config" directories, you simply run Kppp once and the directories will be created. ***

*Copy the following to the kppprc :*

```

[Account0]
AccountingEnabled=0
AccountingFile=
Authentication=4
AutoDNS=1
AutoName=0
BeforeConnect=xterm -e /usr/local/bin/comgt -x -d /dev/modem
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
Name=Vodafone
Password=pass
Phonenumber=*99***1#
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
DefaultAccount=Vodafone
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
InitString=ATZ
InitString1=AT+CGDCONT=1,"IP","internet"
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


**Step 6 : Create a file namely &#8220;vodafone.up&#8221; at your directory, e.g. /home/samiux**

gedit vodafone.up

*Copy the following to the vodaone.up :*

```

echo "Linking modem ...."
echo "Enter your sudo password to link the modem ...."
sudo ln -s /dev/noz0 /dev/modem

```

**_Connecting to internet_**

**Step 1 : Build a link between modem and noz0**

*At the terminal, type*

sh vodafone.up

**Step 2 : Execute the KPPP to dial up**

*At the **<Application>** **<Internet**> **<KPPP>** **<GT_3G_EDGE_HSDPA>***

Before pressing the &#8220;**Connec**t&#8221; button, select the &#8220;**Configure**&#8221;.  Go to **<Misc>** and select the &#8220;**Dock into panel on connect**&#8221;.

**_Disconnect from internet_**

At the panel on the top of the screen, left click the icon (a blue world with 2 lights) and select &#8220;disconnect&#8221;.

*Tip* : Before packing your notebook computer, you should take out the datacard from the slot.  I had damaged the card not doing this.  Fortunately, I got my new one from the Smartone-Vodafone in Hong Kong.

**_Remarks_**

Recently, SmarTone Vodafone (Hong Kong) is promoting her new product of USB HSDPA modem.  However, there is no driver for that new toy at the time of this writing.

UPDATED : The USB modem requires no driver, to my knowledge.  (6th, January 2007)

Finally, enjoy surfing the internet anywhere and anytime!!! :D

---

