---
title: "Wireless Internet Problem"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by oobrokensilence on 2008-06-14
well first off im a nube to the Linux environment. i thought i had everything going ok when i was trying to connect to my wireless connection. i installed ndiswrapper and its utilities and they installed fine. and i downloaded my wireless driver and placed the .exe on my desktop. and did an install of the driver into ndiswrapper. i thought everything was going ok until i checked to see if it was there and it sais....that my wireless driver is invalid. im just not sure what to do next.

---

### Post by WBL on 2008-06-15
Are you using the latest Ubuntu release?  Because for me, connecting to wireless internet is as simple as a few clicks...

-WBL

---

### Post by wormser on 2008-06-15
What type of wireless card and which version of Ubuntu?  Post the results of the following command.

```
lspci
```

---

### Post by oobrokensilence on 2008-06-15
the version of ubuntu is 7.10 and my wireless card is Broadcom 801.11b/g WLAN



mike@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by EtniesBMX on 2008-06-15
nidiswrapper only wants the ".inf" file associated with your wireless card.

 If you have the disc that came with your wireless card, the .inf file will be on there. If not, put google to work and find it that way. Good luck!

---

### Post by wormser on 2008-06-15
This is your card.

> 06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)I have a Broadcom card and installed it with System> Administration> Hardware Drivers (Restricted Drivers Manager).  Just follow the wizard.

You did not say which version of Ubuntu.  It looks like you have a 64 bit machine.  I am unsure if this method will work with 64 bit but it is worth a shot.  You might want to search for a guide for 64 bit Broadcom installs.

---

### Post by amazingtaters on 2008-06-15
He's running Gutsy. There really shouldn't be any problems, I have the same wireless card in my lappy and it runs with the open source drivers in Gutsy. Try native drivers instead of ndiswrapper, that may clear you up. If not post back.

---

### Post by oobrokensilence on 2008-06-15
thanks, ill have a go at it and see how it works out.

---

### Post by Tomatz on 2008-06-15
First you must try to get an internet connection via ethernet. If you can do that you will be able to install your driver easily with the **restricted drivers manager**.



If you cant do that below is a howto to get your wifi working with ndiswrapper:




**[COLOR="#00ff00"]Step 1[/COLOR]**

**R click** on the following links and **"save as"**

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) 

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb)

[B]
[COLOR="#00ff00"]Step 2[/COLOR][/B]

**R click** and **save as**, the following links:

[http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip) *[COLOR="Red"](unzip this when downloaded)[/COLOR]*

[http://www.fjall.org/d505/wlan/bcmwl5.inf](http://www.fjall.org/d505/wlan/bcmwl5.inf)
[B]
[COLOR="#00ff00"]Step 3[/COLOR][/B]

_[COLOR="DarkOrange"]Put ALL the files you downloaded onto a flash drive[/COLOR]_

**[COLOR="#00ff00"]Step 4[/COLOR] **

Now go to your ubuntu box, switch it on (if needed) and put the flash drive in the usb port. Then copy all the files from the flash drive onto the desktop.

**[COLOR="#00ff00"]Step 5[/COLOR]**

Double click the **ndiswrapper-common** file that should be on your desktop and install it. Then do the same with the **ndiswrapper-utils** file. 

**[COLOR="#00ff00"]Step 6[/COLOR]**

Now open a **terminal** *(applications, accesories)* and copy and paste the following:

```
sudo gedit /etc/modprobe.d/blacklist
```

Press enter and a text (config) file will open.** Scroll to the bottom of the file and type:**

```
blacklist bcm43xx
```

**Save** the file then **reboot**
[B]
[COLOR="#00ff00"]Step 7[/COLOR][/B]

Once your box has rebooted, open a terminal and type:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
```

Then in the same terminal type:

```
sudo ndiswrapper -m
```

**Now reboot** (again :P)
[B]
[COLOR="#00ff00"]Step 8[/COLOR][/B]
[B]
L click on the network icon in the systray to connect to wifi networks!!![/B]


Hope that fixes your problem :)

---

### Post by oobrokensilence on 2008-06-15
when i tried to install the ndiswrapper-utils file it sais error: dependency is not satisfiable: libc6. i have no idea what that means.

---

### Post by Tomatz on 2008-06-15
> **oobrokensilence said:**
> when i tried to install the ndiswrapper-utils file it sais error: dependency is not satisfiable: libc6. i have no idea what that means.

Below is a link to the package libc6. Install this before the ndiswrapper package. R click "save as":

[http://ftp.cs.umn.edu/pub/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu3_i386.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu3_i386.deb)


If you need any more dependancys then post back ;)

---

### Post by oobrokensilence on 2008-06-15
also when i left click on the network connection icon it only sais enable networking with a check next to it. shoudnt there be a wireless networking option also?

---

### Post by Tomatz on 2008-06-15
> **oobrokensilence said:**
> also when i left click on the network connection icon it only sais enable networking with a check next to it. shoudnt there be a wireless networking option also?

Not if you have no wifi drivers :)

---

### Post by Tomatz on 2008-06-15
Off now its 12:00 am here. Hope you have no more problems, if you do i will post back tomorow.

:)

---

### Post by oobrokensilence on 2008-06-15
its still saying the same thing. can i just use the ndiswrapper from my boot cd? that seems to install fine.

---

### Post by Tomatz on 2008-06-16
> **oobrokensilence said:**
> its still saying the same thing. can i just use the ndiswrapper from my boot cd? that seems to install fine.

Well if you already have it installed then you can skip that step altogether. I didn't realise hardy had Ndiswrapper on the disc, i've never had to try.

---

### Post by Tomatz on 2008-06-16
> **oobrokensilence said:**
> its still saying the same thing. can i just use the ndiswrapper from my boot cd? that seems to install fine.


What same thing, is it still asking for libc6?

---

### Post by oobrokensilence on 2008-06-16
it was doing that same thing but i installed it off of my boot cd so now everything is good. sorry for the confusion![http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

not sure what to do next though

---

### Post by Tomatz on 2008-06-16
> **Tomatz said:**
> First you must try to get an internet connection via ethernet. If you can do that you will be able to install your driver easily with the **restricted drivers manager**.



If you cant do that below is a howto to get your wifi working with ndiswrapper:




**[COLOR="#00ff00"]Step 1[/COLOR]**

**R click** on the following links and **"save as"**

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) 

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb)

[B]
[COLOR="#00ff00"]Step 2[/COLOR][/B]

**R click** and **save as**, the following links:

[http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip) *[COLOR="Red"](unzip this when downloaded)[/COLOR]*

[http://www.fjall.org/d505/wlan/bcmwl5.inf](http://www.fjall.org/d505/wlan/bcmwl5.inf)
[B]
[COLOR="#00ff00"]Step 3[/COLOR][/B]

_[COLOR="DarkOrange"]Put ALL the files you downloaded onto a flash drive[/COLOR]_

**[COLOR="#00ff00"]Step 4[/COLOR] **

Now go to your ubuntu box, switch it on (if needed) and put the flash drive in the usb port. Then copy all the files from the flash drive onto the desktop.

**[COLOR="#00ff00"]Step 5[/COLOR]**

Double click the **ndiswrapper-common** file that should be on your desktop and install it. Then do the same with the **ndiswrapper-utils** file. 

**[COLOR="#00ff00"]Step 6[/COLOR]**

Now open a **terminal** *(applications, accesories)* and copy and paste the following:

```
sudo gedit /etc/modprobe.d/blacklist
```

Press enter and a text (config) file will open.** Scroll to the bottom of the file and type:**

```
blacklist bcm43xx
```

**Save** the file then **reboot**
[B]
[COLOR="#00ff00"]Step 7[/COLOR][/B]

Once your box has rebooted, open a terminal and type:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
```

Then in the same terminal type:

```
sudo ndiswrapper -m
```

**Now reboot** (again :P)
[B]
[COLOR="#00ff00"]Step 8[/COLOR][/B]
[B]
L click on the network icon in the systray to connect to wifi networks!!![/B]


Hope that fixes your problem :)

Go to **step 6** :)

Just open a terminal like it says and paste the text from the box into it, press enter. 

Then enter your password and a configuration file will appear (its just a plain text file) then add the text from the **_second_ step 6 code box**[COLOR="DarkOrange"](blacklist bcm43xx)[/COLOR] to the **bottom** of the configuration file. 

Then save it and **[COLOR="Red"]Reboot[/COLOR]** (the reboot is very important). go to step 7. ;)


If you just try to just do as the how to says step by step you will find it easy. I remember when i was new to linux i used to think too much about tasks and get myself confused (which is not hard for me to do) ;)

---

### Post by oobrokensilence on 2008-06-16
ok so i did that and it seems that my wireless driver is showing up! But its not roaming for wireless networks.

---

### Post by Tomatz on 2008-06-17
> **oobrokensilence said:**
> ok so i did that and it seems that my wireless driver is showing up! But its not roaming for wireless networks.


So you cant see wireless networks broadcasted?

If this is so you may be able to connect to your wireless network if you set the wireless connection up manually. All you need to do is enter the SSID (broadcasted name of your router) and password ;)

---

### Post by oobrokensilence on 2008-06-17
what is this native drivers program that was mentioned earlier in the thread? it is still not working, i thought i had it and then i didnt. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

---

### Post by Tomatz on 2008-06-17
> **oobrokensilence said:**
> what is this native drivers program that was mentioned earlier in the thread? it is still not working, i thought i had it and then i didnt. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:


I suggest you do a fresh install with the **Ethernet plugged into the laptop**.

Once you have access to the Internet via the Ethernet. **Your wireless will be set up automatically by clicking on the notification from the restricted drivers manager**.


Sorry you have had so much hassle getting it to work :(

Don't give up it will be worth it in the end ;)

---

