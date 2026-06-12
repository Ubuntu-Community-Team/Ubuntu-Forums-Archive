---
title: "HOWTO : Vodafone GlobeTrotter 3G+ HSDPA PCMCIA Card (SmarTone – Hong Kong)"
date: 2006-08-22
forum: Outdated Tutorials &amp; Tips
---

### Post by samiux on 2006-08-22
**VERSION**

Ubuntu version                  : Ubuntu 6.06.1 LTS (kernel version 2.6.15-26-686)                 
nozomi version                  : 2.1 beta
gcom (or comgt) version         : 0.3


**HARDWARES AND SOFTWARES**

Card :
Manufacturer                    : Option
Serial Number                   : starts with 'NL'
Hardware Revision               : 2.1
Band setting                    : Europe 900/1800MHz (4)

Broadband :
Home network                    : SmarToneVodafone
Location                        : Hong Kong
Phone number                    : *99***1#
APN                             : internet
AT strings                      : AT+CGDCONT=1, “IP”, “internet”
Connection speed                : 1.8Mbps (download), 384Kbps (upload)

Software :
Compiler                        : build-essential
Kernel header                   : linux-headers
Drivers                         : “nozomi” and “gcom” (new name is “comgt")     
 download from [http://www.pharscape.org]("http://www.pharscape.org")
Dail up program                 : kppp


**PROCEDURE**

Install the compiler and kernel headers :
[COLOR="Blue"]sudo apt-get install build-essential
sudo apt-get install linux-headers-2.6.15[/COLOR]

[COLOR="Blue"]sudo ln -s /lib/modules/2.6.15-26-686/build /usr/src/linux-headers-2.6.15-26-686[/COLOR]

[COLOR="Red"]Delete[/COLOR] the following line from nozomi.c :
> 
#if LINUX_VERSION_CODE > KERNEL_VERSION(2,6,14)
#define KERNEL_2_6_14
#endif 


Install the drivers :
Extract the “nozomi” in a working directory and run “make” and “make install”.

(if the “make install” does not work, you should copy the “nozomi.ko” to /lib/modules/2.6.15-26-686/kernel/drivers/pci/hotplug/ and applied “sudo insmod /lib/modules/2.6.15-26-686/kernel/drivers/pci/hotplug/nozomi.ko”)

Extract the “gcom” in another working directory and run “make” and “make install”.

Install and configure the kppp :
[COLOR="Blue"]sudo apt-get install kppp
sudo ln -s /dev/noz0 /dev/modem[/COLOR]

Edit the kppprc at /home/<user name>/.kde/share/config with :

> 
[Account0]
AccountingEnabled=0
AccountingFile=
Authentication=4
AutoDNS=1
AutoName=0
BeforeConnect=xterm -e /usr/local/bin/gcom -x -d /dev/noz0
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
pppdArguments=defaultroute,noipdefault,modem,usepeerdns,novj,noauth,crtscts,debug

[Account1]
pppdArguments=

[General]
DefaultAccount=Vodafone
DefaultModem=GT_3G_EDGE_HSDPA
NumberOfAccounts=2
NumberOfModems=3
PPPDebug=0
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


Configure /etc/ppp/peers/kppp-options :
[COLOR="Red"]Uncomment[/COLOR] the "#noauth" to "noauth" and save it.


**OPERATION**
 
Insert the Vodafone modem and execute the KPPP from the menu, no need to change the default setting on the KPPP control panel.  That's all.

Make sure you disconnect the KPPP after surfing the net.


**BEWARE**

I am a newbie to Ubuntu and Linux.  I don't know why I cannot modprobe the nozomi.ko in Ubuntu 6.06.1 (kernel version 2.6.15-26-686).  I need to make a script (vodafone.up) to insmod the module and link the /dev/noz0 and /dev/modem.  Hope someone can point it out for me, thank you.

> 
#!/bin/bash
echo "loading nozomi module ..... "
sudo insmod /lib/modules/2.6.15-26-686/kernel/drivers/pci/hotplug/nozomi.ko

sudo ln /dev/noz0 /dev/modem



**REFERENCE**

[http://www.ubuntuforums.org/showthread.php?t=203342&highlight=option+vodafone]("http://www.ubuntuforums.org/showthread.php?t=203342&highlight=option+vodafone")
[http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,31/]("http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,31/")
[http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,87/]("http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,87/")

Samiux
Hong Kong
Created on 15th August, 2006

---

### Post by bryan4134 on 2006-09-25
Hi - I am also in Hong Kong and have the Vodafone 3.8MBPS USB mobile broadband - works great on windows but i would like to use in with Ubuntu - I can't seem to find any info on setting up such a USB based device.  I see that you have the PCIMIA version of the service working and just wondered if you had any suggestions.

Thanks, Bryan

---

### Post by samiux on 2006-09-25
Vodafone USB modem launched in Hong Kong recently.  I am also looking for the solution.  Since I do not have the device, I do not know if the current driver working in USB or not.

I think you can post a message on the forum at [http://www.pharscape.org](http://www.pharscape.org) to ask the author if the current driver supports USB or not.  Or, you can test it yourself in advance.

Please update us your process, thank you.

---

### Post by samiux on 2006-09-25
Brain,

I just checked with the [www.pharscape.org](www.pharscape.org) and found that the comgt 0.3 was currently not support USB.  The next version 0.4 might.  For reference, please surf [http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,114/](http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,114/)

Samiux

---

### Post by samiux on 2006-09-25
Brain,

After studying the [www.pharscape.org](www.pharscape.org) for a while, I have an idea to put the nozomi.ko in /lib/modules/2.6.15-26-686/kernel/drivers/usb/serial/.

It is just a crazy idea. ;-) 

Samiux

---

### Post by bryan4134 on 2006-09-25
Thanks for this - I'll keep trying - and let you know how it goes.  Maybe a couple of days as I am in Beijing until the end of the week.

Bryan

---

### Post by bebert on 2006-10-12
Thank you for this good topic

for mounting/unmounting automatically the module on device plug/unplug
 sudo /sbin/depmod -a

i don't know how make automaticaly an alias on device then i have added "ln -s /dev/noz0 /dev/modem" in /etc/init.d/makedev it's not a good think but it work

i have change 3 lines in kppprc :
> 7c7
-- BeforeConnect=xterm -e /usr/local/bin/gcom -x -d /dev/noz0
++ BeforeConnect=xterm -e /usr/local/bin/comgt -x -d /dev/modem
28c28
-- pppdArguments=defaultroute,noipdefault,modem,usepe erdns,novj,noauth,crtscts,debug
++ pppdArguments=defaultroute,replacedefaultroute,crtscts,modem,noipdefault,usepeerdns,novj
41c41
-- ShowLogWindow=0
++ ShowLogWindow=1
remove the space in "crt scts" it is automatically add by this forum!

---

