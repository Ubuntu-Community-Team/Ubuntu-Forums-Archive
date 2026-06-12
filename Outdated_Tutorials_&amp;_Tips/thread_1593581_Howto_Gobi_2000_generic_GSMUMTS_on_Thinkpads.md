---
title: "Howto: Gobi 2000 generic GSM/UMTS on Thinkpads"
date: 2010-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by diebels on 2010-10-11
Howto for Maverick, generic GSM/UMTS on Thinkpads.

Two things are needed to make this work on Maverick. (You also need to insert a SIM card into the slot that's covered by the battery.)
[LIST]
[*]The firmware files from Lenovo
[*]The gobi-loader that loads the firmware
[/LIST]

Download and extract windows driver install file from Lenovo. [http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/7xwc44ww.exe](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/7xwc44ww.exe) or get the latest from [http://www-307.ibm.com/pc/support/site.wss/MIGR-72938.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-72938.html)
Install a recent wine as 1.2 crashes during msi extraction: ```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get install wine1.3
```
Run the install file with wine: 
[LIST]
[*]Right click downloaded file, go to Properties -> Permissions, check "Allow executing file as a program"
[*]Right click and run with wine
[/LIST]
Extract firmware from GobiInstaller.msi. ```
mkdir ~/.wine/drive_c/DRIVERS/GOBI
wine msiexec /a ~/.wine/drive_c/DRIVERS/WWANQL/Driver/GobiInstaller.msi /qb TARGETDIR=C:\\DRIVERS\\GOBI
```

install "gobi-loader":
```
sudo apt-get install gobi-loader
```

Copy firmware into /lib/firmware/gobi. ```
sudo mkdir /lib/firmware/gobi; cd ~/.wine/drive_c/DRIVERS/GOBI/Images/Lenovo; sudo cp 6/* /lib/firmware/gobi/; sudo cp UMTS/* /lib/firmware/gobi/
```

Do a reboot or modem-manger restart and qcserial unload load. ```
sudo pkill modem-manager; sudo rmmod qcserial; sudo modprobe qcserial
```

You should now have a "New Mobile Broadband (GSM) connection..." in the nm-applet. If not, do the thing in the previous paragraph or have a look at syslog.

Setting up the Connection is easy if you know your mobile provider.  Just click the "New Mobile Broadband (GSM) connection..." and follow instructions.

If you got the "New Mobile Broadband (GSM) connection..." in the nm-applet, set up correctly for your provider, but still cannot connect, you could try a different firmware.
[quote=http://www.thinkwiki.org/wiki/Talk:Qualcomm_Gobi_2000]
```
Dir 	 Image 	 Remarks
0 	Vodafone Image 	
1 	Verizon Image 	
2 	ATT Image 	
3 	Sprint Image 	includes special Firmware
4 	T-Mobile Image 	
6 	Generic UMTS Image 	
7 	Telefonica Image 	
8 	Telecom Italia Image 	
9 	Orange Image 	
12 	DoCoMo Image 	includes special Firmware
UMTS 	Default Firmware 	the MD5-sum on the page matches these 
```
[/quote]
So if you're using Vodafone, you can try:
```
cd ~/.wine/drive_c/DRIVERS/GOBI/Images/Lenovo; sudo cp 0/* /lib/firmware/gobi/
```
Also, following tail of syslog might give you some hints:
```
tail -f /var/log/syslog
```
This device also has a GPS, but it is not working yet: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/653126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/653126)

---

### Post by akbardotinfo on 2010-11-07
WORKS PERFECTLY !!
MANY THANKS !!!



device type thinkpad X201 A39

---

### Post by zonky on 2010-11-07
Hi - just got my new HP Probook 5320m today - it has a un2420 card.

Instructions work pretty much- i had to grab the same windows files.

I used:

sudo pkill modem-manager; sudo rmmod qcserial; sudo modprobe qcserial

initially, then was able to create the connection.

After a restart, seems to me that i can then just try and open the connection and it starts to work! No need to rerun the 
sudo pkill modem-manager; sudo rmmod qcserial; sudo modprobe qcserial
 at all!

---

### Post by GodLikeCreature on 2010-11-10
> **zonky said:**
> Hi - just got my new HP Probook 5320m today - it has a un2420 card.

Instructions work pretty much- i had to grab the same windows files.

I used:

sudo pkill modem-manager; sudo rmmod qcserial; sudo modprobe qcserial

initially, then was able to create the connection.

After a restart, seems to me that i can then just try and open the connection and it starts to work! No need to rerun the 
sudo pkill modem-manager; sudo rmmod qcserial; sudo modprobe qcserial
 at all!

Hi!

I got the 5320m as well, tried the steps above, but it didn't work for me.  When running 

sudo pkill modem-manager; sudo rmmod qcserial; sudo modprobe qcserial

I get an error saying that the qcserial module does not exist.

Any ideas?

---

### Post by GodLikeCreature on 2010-11-10
> **zonky said:**
> Hi - just got my new HP Probook 5320m today - it has a un2420 card.

Instructions work pretty much- i had to grab the same windows files.

I used:

sudo pkill modem-manager; sudo rmmod qcserial; sudo modprobe qcserial

initially, then was able to create the connection.

After a restart, seems to me that i can then just try and open the connection and it starts to work! No need to rerun the 
sudo pkill modem-manager; sudo rmmod qcserial; sudo modprobe qcserial
 at all!

Btw, not related, but just wanted to check with you.

I get a strange behavior on my 5320m.  When I start the machine and log in as soon as the login screen is there, then the wireless connection usually times out and does not connect.  When that happens, I have to manually choose my wireless network and trigger the connection.  That works, but is obviously annoying.

However, if I wait a bit when the login screen is there and then login, then the wireless connection does pick up automatically.

Are you getting the same behavior?

---

### Post by zonky on 2010-11-11
Godlikecreature; Sorry, not much to offer- i got the windows drivers off a different 5320m- this laptop has never booted into windows.. Have read that windows will do odd things to the 3g?

Also- which driver are you using? 

My wlan card is: Broadcom Corporation BCM43224 

I decided to use this method to get it working:

>sudo apt-get install bcmwl-kernel-source 

Then installed the restricted SAT drivers.

---

### Post by ottosykora on 2010-11-22
Here output from the log:

```
Nov 22 21:03:07 ottomini modem-manager: Loaded plugin Longcheer
Nov 22 21:03:07 ottomini modem-manager: Loaded plugin Huawei
Nov 22 21:03:07 ottomini kernel: [11245.568132] USB Serial support registered for Qualcomm USB modem
Nov 22 21:03:07 ottomini modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted
Nov 22 21:03:07 ottomini kernel: [11245.573978] usb 1-6: Could not set interface, error -71
Nov 22 21:03:07 ottomini kernel: [11245.574388] usbcore: registered new interface driver qcserial
Nov 22 21:03:07 ottomini modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Nov 22 21:03:07 ottomini modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Nov 22 21:03:07 ottomini modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Nov 22 21:03:08 ottomini modem-manager: (net/vboxnet0): could not get port's parent device
```

---

### Post by ottosykora on 2010-11-22
here output of the lsusb:

```
Bus 005 Device 002: ID 03f0:2a1d Hewlett-Packard 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 03f0:251d Hewlett-Packard Gobi 2000 Wireless Modem
Bus 001 Device 002: ID 1fea:0008  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by ottosykora on 2010-11-22
when I try to setup new gsm connection in the network manager, I can not select a device on the first page of the setup, the drop down menu is grayed out. 
However it seems that all is detected. ?????

I can select then swisscom etc, but nothig is connecting

Gobi leader, the right firmware etc is installed

---

### Post by ottosykora on 2010-11-22
andfinaly

```
otto@ottomini:~$ dmesg |grep -i qcs
[   11.228228] qcserial 1-6:1.2: Qualcomm USB modem converter detected
[   11.231228] usbcore: registered new interface driver qcserial
[10051.981630] usbcore: deregistering interface driver qcserial
[10051.984663] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[10051.987556] qcserial 1-6:1.2: device disconnected
[10052.036587] usbcore: registered new interface driver qcserial
[10079.435943] usbcore: deregistering interface driver qcserial
[10079.484227] usbcore: registered new interface driver qcserial
[10114.805131] usbcore: deregistering interface driver qcserial
[10127.758401] usbcore: registered new interface driver qcserial
[11245.524433] usbcore: deregistering interface driver qcserial
[11245.574388] usbcore: registered new interface driver qcserial
[12160.179955] usbcore: deregistering interface driver qcserial
[12160.275287] usbcore: registered new interface driver qcserial

```

---

### Post by 4all on 2011-01-04
Thank you very much,

it almost works for me, I can connect, but sometime I'm disconnected without any special reason.

Using Vodafone Spain SIM card (Internet Contigo) with Thinkpad T510i
with firmware of file 7xwc44ww.exe (not the last one) and set :

$ md5sum /lib/firmware/gobi/*
c3d6fd93ae2e52775ef9cd8fccbc20be  /lib/firmware/gobi/UQCN.mbn
84d002b0ef003cde6c95826bfbf067fe  /lib/firmware/gobi/amss.mbn
d7496085f1af3d1bfdf0fa60c3222766  /lib/firmware/gobi/apps.mbn

Cheers

---

### Post by soundpartner on 2011-02-08
This almost works for me...
cause i cant activate the 3g connection.
when i look at it it says 

3g connection qualcom gobi 2000 
Not regiteret

i can try to connect to my provider and it try, but after about 50 seconds it tells me that the connection is disconnected.

i have tryed to use the newer networkmanager 
i am running maverick with the 2.6.35-26-generic kernel

---

### Post by joshuaos on 2011-03-18
The solution in the original post seemed to work perfectly for me, until I rebooted.  Then it works if I enter:

sudo pkill modem-manager; sudo rmmod qcserial; sudo modprobe qcserial

Any ideas how I can get it working on reboot?

---

### Post by ehime on 2011-04-14
I'm looking to do something similar on a Google CR48 with a T-Mobile SIM,
anyone try this? It looks like GOBI 2k drivers are already installed with the 
CR's Chromium OS, but possibly missing with the CR/Ubuntu 10.10 hybrid.

```
 find / | grep 'gobi' 
```

returns

```

[COLOR=#000000][FONT=Times New Roman]/home/(user)/Documents/gobi_search.txt
/lib/modules/2.6.32.26+drm33.12/kernel/chromeos/drivers/gobi
/lib/modules/2.6.32.26+drm33.12/kernel/chromeos/drivers/gobi/QCUSBNet2k
/lib/modules/2.6.32.26+drm33.12/kernel/chromeos/drivers/gobi/QCUSBNet2k/QCUSBNet2k.ko
/usr/lib/ModemManager/libmm-plugin-gobi.so
/usr/share/app-install/desktop/ggobi.desktop
/usr/share/app-install/icons/ggobi.png
/usr/src/linux-headers-2.6.35-22-generic/include/config/i2c/algobit.h
/usr/src/linux-headers-2.6.35-24-generic/include/config/i2c/algobit.h[/FONT][/COLOR]

```

---

