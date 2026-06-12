---
title: "Modem problem"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by Jvdy on 2012-12-16
hi, My name Wahyu
new to linux love to use foss
i have a new installation ubuntu precise 12.04.1
I format my hdd and have ubuntu only os in my acer aspire 4739
**Problem** is my modem doesn't work in nm-applet
i have downloaded(from another win xp) and install wvdialconf but it doesn't allow me to install .deb files so what i do is manually copy it files with sudo nautilus open .deb files in file roller and copy the files to folder location as i see in file roller folder name (Is this the right way to install?)
but it still doesn't work
yes i allready install its dependencies: debconf_1.5.42ubuntu1_all ; libc6_2.15-0ubuntu10_i386 ; libstdc++6_4.6.3-1ubuntu5_i386 ; libuniconf4.6_4.6.1-2build1_i386 ; libwvstream4.6-base_4.6.1-2build1_i386 ; libwvstreams4.6-extras_4.6.1-2build1_i386 ; network-config_0.2-1_all ; wvdial_1.61-4build1_i386 ; and edit wvdial.conf in etc/wvdial.conf based on what i found in google

still doesn't detect my usb modem stick cyrus zte 21.6 mbps like this one [**http://www.cyruspad.com/product.php?id=24**]("http://www.cyruspad.com/product.php?id=24")

also i try to enter terminal :
*sudo wvdialconf*
 got this : Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://alumnit.ca/wiki/?WvDial](http://alumnit.ca/wiki/?WvDial)

*sudo wvdial*
got this :
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory


plisss help me....
what to download what to install and howwww
plizz

---

### Post by mansonfan78 on 2012-12-16
> **Jvdy said:**
> hi, My name Wahyu
new to linux love to use foss
i have a new installation ubuntu precise 12.04.1
I format my hdd and have ubuntu only os in my acer aspire 4739
**Problem** is my modem doesn't work in nm-applet
i have downloaded(from another win xp) and install wvdialconf but it doesn't allow me to install .deb files so what i do is manually copy it files with sudo nautilus open .deb files in file roller and copy the files to folder location as i see in file roller folder name (Is this the right way to install?)
but it still doesn't work
yes i allready install its dependencies: debconf_1.5.42ubuntu1_all ; libc6_2.15-0ubuntu10_i386 ; libstdc++6_4.6.3-1ubuntu5_i386 ; libuniconf4.6_4.6.1-2build1_i386 ; libwvstream4.6-base_4.6.1-2build1_i386 ; libwvstreams4.6-extras_4.6.1-2build1_i386 ; network-config_0.2-1_all ; wvdial_1.61-4build1_i386 ; and edit wvdial.conf in etc/wvdial.conf based on what i found in google

still doesn't detect my usb modem stick cyrus zte 21.6 mbps like this one [**http://www.cyruspad.com/product.php?id=24**]("http://www.cyruspad.com/product.php?id=24")

also i try to enter terminal :
*sudo wvdialconf*
 got this : Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://alumnit.ca/wiki/?WvDial](http://alumnit.ca/wiki/?WvDial)

*sudo wvdial*
got this :
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory


plisss help me....
what to download what to install and howwww
plizz


It seems like your system is looking for the modem on a serial (com) port instead of usb.  Have you tried a different usb port?  Also, copying the files as you mentioned won't work.  Why can't you install .deb files?  What does it say when you try to?  Or does simply nothing happen?

---

### Post by Jvdy on 2012-12-16
if i double click .deb files its open software center but doesn't allow me to click install button, its **grayed out** so i decide to copy its files

---

### Post by mansonfan78 on 2012-12-16
Open the task manager and check if "polkit-gnome-authentication-agent" is running.  If not, open the run dialog (alt f2) and type "usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1" (without the quotes) and try running the .deb file again.

---

### Post by Jvdy on 2012-12-17
i've tried that also i tried to kill it and then rerun it but stil the same i can't click the install button 
pliz any other suggestion
 ?????

---

### Post by steeldriver on 2012-12-17
if you are having trouble with opening .deb files through the GUI package manager then maybe try using dpkg directly

1. open a terminal
2. cd to the directory containing the .deb file
3. type

```
sudo dpkg -i *name_of_file*.deb
```Make sure any other package managers (Software Center and/or Synaptic) are closed first otherwise you will get a file lock error

[https://help.ubuntu.com/10.04/serverguide/dpkg.html](https://help.ubuntu.com/10.04/serverguide/dpkg.html)

---

### Post by Jvdy on 2012-12-17
> **steeldriver said:**
> if you are having trouble with opening .deb files through the GUI package manager then maybe try using dpkg directly

1. open a terminal
2. cd to the directory containing the .deb file
3. type

```
sudo dpkg -i *name_of_file*.deb
```Make sure any other package managers (Software Center and/or Synaptic) are closed first otherwise you will get a file lock error

[https://help.ubuntu.com/10.04/serverguide/dpkg.html](https://help.ubuntu.com/10.04/serverguide/dpkg.html)

thanks its work 
_**but my real trouble is i can't connect to the internet cause wvdial doesn't detect my modem **_

does anyone can help?
tell me howw

---

### Post by Jvdy on 2012-12-17
still same error if i trying to enter terminal run this :
sudo wvdialconf i got error that say no modem detected like i post before
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=12409195#1](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=12409195#1)

---

### Post by steeldriver on 2012-12-18
is the modem being detected in your lsusb and/or lshw?

```
lsusb
``````
sudo lshw
```

---

### Post by Jvdy on 2012-12-18
yes i already tried it lsusb 
it detected my usb modem stick got this list

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0402:7675 ALi Corp. 
Bus 002 Device 003: ID 19d2:0154 ZTE WCDMA Technologies MSM

but i think it's not necessary cause wvdialconf will detect it so i think thats no need lsusb
lsusb only show me what is coneccted to my computer
and lshw only show all of computer hardware

any other suggestion?

---

### Post by steeldriver on 2012-12-18
Unfortunately I don't have any recent experience with modems -  however some googling on your behalf suggests some people have had an issue where the system detects and automounts the USB modem as a storage device - preventing wvdial / ppp from taking control of it

Do you see anything suspicious in the /media (or /media/*yourusername*) directories?

---

### Post by Jvdy on 2012-12-19
please help me to connect my modem

---

### Post by Jvdy on 2012-12-19
> **steeldriver said:**
> Unfortunately I don't have any recent experience with modems -  however some googling on your behalf suggests some people have had an issue where the system detects and automounts the USB modem as a storage device - preventing wvdial / ppp from taking control of it

Do you see anything suspicious in the /media (or /media/*yourusername*) directories?

i think ubuntu is not preventing wvdial  cause i have installed ubuntu 12.04 before but i do reinstall cause i just broke the system (problem is i cant logon to unity or gnome session its always log me in to lxde session and i can't chose what session to use with) with my old ubuntu i can connect my modem and use it as an mass storage too
but the odd is i must connect my venera phone to enable mobile network and eject it and then connect using my modem with nm-applet and same things happen to gnome-ppp

there is no suspicious cause i can run it in windows and its ok no problem
so i think there sould be ubuntu doesn't have libraries or some thing to connect

oh god of linux help me....

---

### Post by Jvdy on 2012-12-19
but if i do havee the same issue like you say what should i do
you found it on google
do you have the link??

maybe it should help 
thanks by the way

---

### Post by steeldriver on 2012-12-19
Here you go

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/994651](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/994651)

[http://ubuntuforums.org/showpost.php?p=11934679&postcount=16Ubuntu-](http://ubuntuforums.org/showpost.php?p=11934679&postcount=16Ubuntu-)

I didn't post them before because I'd rather CONFIRM that your problem is similar before recommending a course of action - but since you don't seem to be willing to follow through with the diagnostics that I suggested, I'll just let you figure it out yourself. Good luck!

---

### Post by Jvdy on 2012-12-19
> **steeldriver said:**
> - but since you don't seem to be willing to follow through with the diagnostics that I suggested, I'll just let you figure it out yourself. Good luck!

if you mean that lshw and lsusb
i've allready done that before 
zte modem is listed here:
[PHP]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0402:7675 ALi Corp. 
Bus 002 Device 003: ID 19d2:0154 ZTE WCDMA Technologies MSM [/PHP]

i post lsusb terminal output before
but i can't see my usb modem is listed or maybe its not detect any usb device on my computer

---

### Post by steeldriver on 2012-12-19
Hi sorry I meant whether you are seeing it auto mounted as a USB storage device in /media (or possibly /media/yourusername)

---

### Post by Jvdy on 2012-12-19
ok
now i'm at work,
this night i'll check it out...

---

### Post by Jvdy on 2012-12-23
there's nothing in  /media/
and **still no connection**
giving up troubleshot this modem , I decide to bought new modem [SIZE=1][SIZE=2]Mobinil E173 huawei hsdpa usb modem (7.2Mbps)
[SIZE=2]and it work fine[/SIZE]
[/SIZE]	[/SIZE]

---

### Post by Jvdy on 2012-12-25
but i still **wonder** if anyone can solve this modem problem

---

### Post by MishaX2 on 2012-12-25
You have to specify your device in  */etc/wvdial.conf. *You currently have a line saying:
> Modem = /dev/ttyACM0This should not be kept, since apparently your system can't find that device.
Which device right now it is exactly, I don't know. But at least that's where it's going wrong.
I will keep you updated when I find something.

Update: could you try putting this as your device:
/dev/bus/usb/002/003
I don't know if this will work, but let me know...

---

### Post by Jvdy on 2012-12-27
> **MishaX2 said:**
> 
Update: could you try putting this as your device:
/dev/bus/usb/002/003
I don't know if this will work, but let me know...

What do you mean exactly?
Enter it in terminal ???
then I enter it got this error
[HTML]/dev/bus/usb/002/003
bash: /dev/bus/usb/002/003: No such file or directory
[/HTML]

---

### Post by Jvdy on 2012-12-27
> **MishaX2 said:**
> You have to specify your device in  */etc/wvdial.conf. *You currently have a line saying:
This should not be kept, since apparently your system can't find that device.
Which device right now it is exactly, I don't know. But at least that's where it's going wrong.

I ever edit wvdial conf
I've run this command:
[PHP]sudo gedit /etc/wvdial.conf[/PHP]The config file is :
[PHP]
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
; Password = <Your Password>
; Username = <Your Login Name>
Modem = /dev/ttyACM0
Baud = 9600[/PHP]Edit
[HTML]Modem = /dev/ttyUSB0[/HTML][HTML]Modem = /dev/ttyUSB1[/HTML][HTML]Modem = /dev/ttyUSB2[/HTML][HTML]Modem = /dev/ttyUSB3[/HTML][HTML]Modem = /dev/ttyACM1[/HTML][HTML]Modem = /dev/ttyACM2[/HTML]etc 

but nothing works
allways got error saying
cannot open dev/ttyUSB0 no such file/directory
I've another modem that work fine
and it located in dev/ttyUSB2
Connect it to the same port and edit wvdial.conf to dev/ttyUSB2
still can't Detect my ZTE Modem

---

