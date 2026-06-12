---
title: "[SOLVED] Installing Wireless (Please help, this is really frustrating)"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by mal_conductor on 2008-07-25
I am trying to enable my wireless card.
Chipset: Broadcom BCM4306
Card: Dell Wireless 1350 WLAN Mini-PCI

I have read a number of installation guides and this is what I understand:

- Option 1 is to install ndiswrapper and chipset driver.
   o It is preferred that the driver be downloaded  from the ndiswrapper website.

- Option 2 Chipset driver and Firmware
   o For a lucky few the Chipset driver is included in Hardy
   o But the firmware needs to be downloaded separately
   o This method is preferred over using ndiswrapper
   o Can be done from [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net)

Question 1:  Do I understand this correctly?

Question 2: (I preferred to use Option 2: Chipset Driver + Firmware)
The driver for my Chipset is included in Hardy.  Do I just install the Firmware and that’s all?
Or do I need to enable the driver or the firmware or compile something or what?

Question 3: What is “Afterwards, don't forget to run aptitude update to fetch the lists” [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net)
		

I have read so many guides.  Some I have no clue what they talk about, some of them are very good, but I did not find a step-by-step guide for option 2 above.

---

### Post by kool_kat_os on 2008-07-25
> **mal_conductor said:**
> 

Question 3: What is “Afterwards, don't forget to run aptitude update to fetch the lists” [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net)
		


```
sudo aptitude update
```

---

### Post by DagMan on 2008-07-26
This is old but probably still aplicable [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by mal_conductor on 2008-07-26
Hello Ayuthia,

Please consider a posting I did on the Beginner Forum.  Also these are the results from the commands you requested from a user with similar issues.

Thank you,
Mal_conductor


=====================================
I am trying to enable my wireless card.
Chipset: Broadcom BCM4306
Card: Dell Wireless 1350 WLAN Mini-PCI

I have read a number of installation guides and this is what I understand:

- Option 1 is to install ndiswrapper and chipset driver.
o It is preferred that the driver be downloaded from the ndiswrapper website.

- Option 2 Chipset driver and Firmware
o For a lucky few the Chipset driver is included in Hardy
o But the firmware needs to be downloaded separately
o This method is preferred over using ndiswrapper
o Can be done from [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net)

Question 1: Do I understand this correctly?

Question 2: (I preferred to use Option 2: Chipset Driver + Firmware)
The driver for my Chipset is included in Hardy. Do I just install the Firmware and that’s all?
Or do I need to enable the driver or the firmware or compile something or what?

Question 3: What is “Afterwards, don't forget to run aptitude update to fetch the lists” [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net)


I have read so many guides. Some I have no clue what they talk about, some of them are very good, but I did not find a step-by-step guide for option 2 above.

Output from:  lshw -C network, uname -a
,  lspci -nn|grep 14e4

ubuntu@DELL1150:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:11:43:62:98:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:0f:54:eb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

ubuntu@DELL1150:~$ uname -a
Linux DELL1150 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

ubuntu@DELL1150:~$ lspci -nn|grep 14e4
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

---

### Post by AlexenderReez on 2008-07-26
for me...i prefer ndiswrapper because it lest pain...you just need to search ndiswrapper in synaptic...install it..it should appears under menu list or control center ...(search for it)..insert driver cd...open ndiswrapper,click install driver button...

you may want to restart ur network connection to detect it...i use wifi-radar instead of network-manager-gnome because i feel it is better...

> sudo /etc/init.d/networking restart

> sudo iwconfig

---

### Post by Brightbelt on 2008-07-26
Hi,
  If you want to use Ndiswrapper, here are some basic facts:

- Ndiswrapper runs off of the INF file (filename.inf for example) that is included in the Windows version driver for your wireless card. AND it also needs the System file of the SAME name (samefilename.sys). You just need to make sure these 2 files are side by side in whatever directory you decide to put them in before you install the inf. 

- The easiest way to install Ndiswrapper is through the Synaptic Package Manager. And make sure you install 'Ndisgtk', which is the graphical user interface (gui) version. It makes life easier when you're frustrated and wanting to get this done asap. 

- Copy the Inf and Sys file to your desktop...

- Click the System/Administration menu (I'm guessing - it's near there somewhere) and look for 'Wireless Windows Drivers'. Choose that. 

- That'll bring up the Interface for Ndiswrapper. Click the "+ Add" button and browse to your inf file and click 'Ok'. 

- Reboot and that should do it. 

I hope this helps,....Frank B.

---

### Post by Ayuthia on 2008-07-26
Thanks for posting all your information!  The card that you have (4306 rev 03) is a Broadcom card so there is a native linux driver that is built in the kernel that Hardy uses.  However, it does lack the firmware needed to make it work.  This answers Question 2 for you.  If you have a working wired internet connection in Ubuntu, all you should need to do is enable the driver (System->Administration->Hardware Drivers) and it will download the firmware for you and you should be ready to go.

You also do have another option and that is to go with NDISwrapper.  It uses the Windows (XP and possibly older, but not Vista) drivers to get the wireless running.  To use NDISwrapper with your card, you will have to find an XP wireless driver for your card and then you will have to do some additional configuration to block out the native linux Broadcom driver along with add an additional script to reload the b44 driver after NDISwrapper so that your wired ethernet connection can still work.  Here is a link that has done pretty well for most Broadcom owners:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
It provides a list of drivers that have been successful (looks like yours is Step 2b).

I would recommend trying to install the firmware first just to see if it works before trying the NDISwrapper route.  I say this mainly because there are not too many steps to it and if it does not work, all you have lost is some time.  However, if you do the NDISwrapper route first and it does not work, you will have to back out all the configuration that you did so that you can make the native linux driver work.

Here are my responses to some of your questions:
Response for Option 1:
For NDISwrapper, it is preferred that you use the Windows drivers that came with your computer as long as it is not Vista.  If you can't find it, sometimes you can go to your computer's website and download the drivers from there.  NDISwrapper website does have a big list of drivers there, but a lot of stuff has been there for some time and the links are no longer valid.

Response for Option 2:
Right now the Linux native Broadcom module does come with the kernel but it does need some proprietary firmware to make it work.  Because of this, the firmware could not be included.  That is why you have to download the firmware.  As I mentioned earlier, I prefer trying this before going the NDISwrapper route because there is no configuration needed for this option.  As for the ubuntu.cafuego.net repository, I have never tried it so I am not for sure if it will make things easier or not.  NDISwrapper does come with the Hardy install CD so if you are just looking to install NDISwrapper, I would not add that repository.

Answer to your questions:
You seem to have a good idea about your options.  I would not go and compile NDISwrapper from the source unless you cannot get the firmware installed and working and had no success with the Hardy version of NDISwrapper.

As for the last question about the apt-get update after adding ubuntu.cafuego.net to your sources.list.  The sources.list file is a list of repositories (sites that contain packages to install).  All it contains are websites to where the packages can be downloaded.  In order for Ubuntu to grab the list of packages available from those repositories, you have to do an apt-get update.  This will download the list of packages that are currently out there and the process will also compare the list to what you currently have installed.  If there are newer packages available an icon usually comes up on your panel to let you know that there are updates available.

So when you add ubuntu.cafuego.net to your sources.list and run apt-get update, you will get the list of packages available from them.  If you don't run it, you will not be able to see their package list.

Sorry for the long answers.  Hopefully this answers your questions and helps you out.

---

### Post by dmizer on 2008-07-26
Your best bet for help is to stick with one thread.  If you want help, you should post the results of those commands in your original thread here: [http://ubuntuforums.org/showthread.php?t=870552](http://ubuntuforums.org/showthread.php?t=870552)

Double posting is against forum policy, closing thread.

edit:
Since Ayuthia put so much work into a reply for this, I decided to merge the threads.  Carry on.

---

### Post by mal_conductor on 2008-07-28
Thanks Ayuthia.  Worked great.

---

