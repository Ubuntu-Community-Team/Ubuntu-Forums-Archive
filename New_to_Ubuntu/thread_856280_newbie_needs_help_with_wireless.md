---
title: "newbie needs help with wireless"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by huntis619 on 2008-07-11
Hi all. I have a hp zv5410us laptop. I had no problems with my wireless when I had ubuntu 7.10. Since I upgraded to ubuntu 8.04 I've been stuck with the ethernet cable. Can someone please help me.

---

### Post by RequinB4 on 2008-07-11
What is the output of ```
lspci
```

---

### Post by Inxsible on 2008-07-11
What's the wireless chip you have in there?

Had you installed some drivers in 7.10 for it to work, or did it work out of the box in 7.10?

---

### Post by huntis619 on 2008-07-11
lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
I received help from this forum site when I installed 7.10. It was my first linux install and I was up and running in 3 days.

---

### Post by Inxsible on 2008-07-11
> **huntis619 said:**
> lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
I received help from this forum site when I installed 7.10. It was my first linux install and I was up and running in 3 days.3 days is way too long ;)

Anyway.. I see that you have a Broadcom chip. there have been issues reported with those. You may want to search for Hardy and Broadcom and see some solutions.

But I know it can be done.

As a side note: Whenever you are posting outputs or some code use the [code][ /code]tags without the space of course. It helps in letting others read easily

---

### Post by james_vanb on 2008-07-11
Have you tried this?

[http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4306)

I have the same chip - Once I loaded the driver off the install cd through ndiswrapper, I followed step 3 to the end.

---

### Post by huntis619 on 2008-07-11
how do I load the driver off of the driver cd. Did you do steps 1 and 2 then install drivers. Also I tried that post and had problems with #1 which version broadcom do I use for step 2 and #2  I always seem to mess up step 6 can anyone please simplify for me. Remember I am a noob.

---

### Post by james_vanb on 2008-07-11
Download ndiswrapper from Synaptic - There are 2 applications - ndiswrapper common and ndiswrapper utils (or something like that, when you mark ndiswrapper common, it should mark the other as well).

Open Places > home

left click in open space and create folder.  I called mine Belkin as this is the wireless card I'm using.

Insert install cd - open - drag and drop all files contained in the file under xp drivers - it should be a .sys, .inf and .cat - into the file you created.

Go to the link I gave you - Step 3 begins with the following command:

```
sudo ndiswrapper -i bcmwl5
```

You have to modify that command to point to the file you created, In my case it looked like this:

```
sudo ndiswrapper -i /home/(yourusername)/Belkin/bcmwl5.inf
```

Then just copy and paste the commands that follow in Step 3 all the way to the end.

Keep in mind that commands are case sensitive i.e. my file was Belkin not belkin.

---

### Post by huntis619 on 2008-07-11
I'll try it. But I have another question can you explain to me how to do step 6?

---

### Post by avtolle on 2008-07-11
OK, you did step 5, and have opened the subject file, correct? It should be an empty file, if I understand it correcty. With the file still open, paste the script in step 6 into the file, and use the gedit command to save it (I don't know what that is, as I use nano for editing), then proceed through the remaining part of the linked piece.

---

### Post by james_vanb on 2008-07-11
Step 6 - Open wirelessfix for editing:

```
sudo gedit /etc/init.d/wirelessfix.sh
```

This should open the file in the text editor (gedit is default text editor for ubuntu - mousepad is default for xubuntu - kubuntu , etc. have their own default editors).

Copy and paste the script contained under Step 6 into the file (It should be blank when you open it) - Save and close.

---

### Post by huntis619 on 2008-07-11
OK I have the ndiswrapper installed. I put the 8.04 disc in but I don't see anything saying xp drivers. Did I miss something.

---

### Post by james_vanb on 2008-07-11
Install cd refers to the cd that came with the wireless adapter.  In my case, it came with the Belkin Wireless card I installed.  If your card is an on-board card, you may have to go to the manufacturers web site and see if you can download the drivers.

Try here:

[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&cc=us&lang=&dlc=&product=443081&](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?lc=en&cc=us&lang=&dlc=&product=443081&)

More specifically, here:

[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=&product=443081&lang=](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=&product=443081&lang=)

Try the xp driver download for Broadcom.

You will not be able to open the .exe file in ubuntu (Although it may open with Wine) - Can you open on a Windows machine and copy the drivers to transfer to you laptop?

---

### Post by huntis619 on 2008-07-11
OK here is the script for steps 5 -8. Because I did this before steps 1-4 were ok stating that the files already existed. I'm going to restart my computer and come back to the forum site. I'll let you know how it goes.sudo gedit /etc/init.d/wirelessfix.sh
steven@steven-laptop:~$ cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
steven@steven-laptop:/etc/init.d$ sudo update-rc.d wirelessfix.sh defaults
 System startup links for /etc/init.d/wirelessfix.sh already exist.
steven@steven-laptop:/etc/init.d$

---

### Post by huntis619 on 2008-07-11
OK still no wireless. I've got to be doing something wrong. agghhhhh PLEASE ANYBODY  save me......

---

### Post by james_vanb on 2008-07-11
Ok - A few things to check.  In the upper right corner of your desktop, you will wee the Network Manger.  Left click on it - Does it show your router?  If it does, click on it and it should try to connect.  Or, you can try to manually configure.  Left click and click manually configure at the bottom of the drop down.

If that doesn't work, what wireless card are you using?  Post the output of ndiswrapper -l.

---

### Post by cariboo on 2008-07-11
In a terminal type:

```
ndiswrapper -l
```

and post the output also:


```
lsmod | grep ndiswrapper
```

When using the guides, If you don't know what you are doing, follow them the way they are written, as jumping to different steps or not doing them in order can lead to what you are experiencing now.

Jim

---

### Post by huntis619 on 2008-07-11
ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
steven@steven-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,ohci_hcd


OK when I used the guide I didn't skip any steps. I just posted steps 5-8 because those were the steps I thought I messed up on. I wanted some feedback. Steps 1-4 were ok and being that I used this guide before the response to each command was that file already existed. Yes I can see my router. I put in my password and try to connect and nothing. Doing it manually I wouldn't even have a clue. thank you all for beinhg patient with me. Still no wireless.

---

### Post by james_vanb on 2008-07-11
Try turning security off on your router.  If you can now connect, the problem is configuring security.  See this thread RE setting up security:

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

To manually configure:

Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WPA personal (If no security set - Otherwise set security type as appropriate and type in your password). Set Configuration to Automatic configuration (DHCP)

---

### Post by huntis619 on 2008-07-11
Nope. That didn't work either. The manual configuration or turning my security off. I wonder why I'm having so many problems.I might have to go back to 7.10. How do I uninstall 8.04. I've been trying to get wireless since april. Everybody keeps telling totry the same guide but its not working for me. I follow all the steps but still no wireless. I'm getting tired of this 100 foot ethernet cable.

---

### Post by james_vanb on 2008-07-11
What Wireless card are you using?

---

### Post by huntis619 on 2008-07-11
a broadcom BCM4306 (rev 03)

---

