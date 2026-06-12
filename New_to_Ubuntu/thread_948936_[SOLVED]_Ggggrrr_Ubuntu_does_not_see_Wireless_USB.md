---
title: "[SOLVED] Ggggrrr: Ubuntu does not see Wireless USB"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Frenske on 2008-10-15
Whop ... back on Windows XP again. Ubuntu does not see my Belkin FD7050 v3 (I think) Wireless USB, whereas it works fine in Windows XP. It was working fine previously, but Ubuntu decided for no reason or so whatever that the USB dongle does not exist. I have put in other USB ports but no blinking lights. There was an update the last time I logged off. No idea what the updates were (since I am a bit of a noob I just trust the installer of Ubuntu - wrong obvious).
How can I shake Ubuntu awake that there is Wireless USB dongle???

---

### Post by GameGuru on 2008-10-15
If it isn't compatible with Linux then you can use ndiswrapper and the WinXP driver to get it to work.  I had to do that with a Linksys 802.11b wireless card I had.

---

### Post by Frenske on 2008-10-15
I use a special driver from serial monkey. The thing is that it was working just fine for weeks and suddenly it is not fine any more.

---

### Post by D3M0L1$H3® on 2008-10-15
ndiswrapper i can't get to work for any (especially my TEW-444UB), so if you can help him, plz pm me

---

### Post by halitech on 2008-10-15
unplug the usb adapter, open a terminal (applications - accessories - terminal)
post the results of
```
lsusb
```then plug the adapter back in, wait a minute and do the same command and post the results back here

---

### Post by Frenske on 2008-10-16
Sorry for not replying quicker: it was bed time for me.

Without the usb wireless dongle

```
Bus 005 Device 005: ID 05dc:a410 Lexar Media, Inc. JumpDrive 128MB/256MB
Bus 005 Device 004: ID 059b:007d Iomega Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 413c:3200 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

With the usb wireless dongle

```
Bus 005 Device 006: ID 050d:705a Belkin Components 
Bus 005 Device 005: ID 05dc:a410 Lexar Media, Inc. JumpDrive 128MB/256MB
Bus 005 Device 004: ID 059b:007d Iomega Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 413c:3200 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

I guess Ubuntu sees the card. Perhaps the update screwed up the drivers somehow. I had great difficulties with this USB Wireless dongle. Not recommended for Ubuntu.

PS It is not the FD7050 but F5D7050.

---

### Post by halitech on 2008-10-16
at least Ubuntu is seeing it so trying using ndiswrapper to reinstall the driver and hopefully it will work

---

### Post by fred_miller on 2008-10-16
MY Belkin USB wifi works just perfect with ndiswrapper and the Windows driver that came with it.

---

### Post by Frenske on 2008-10-16
Not all Belkin are the same. There 4 different version of the Belkin F5D7050 alone. Each with a different chip and different driver. Version 3 is the problem child, the black sheep in the family.

But I got it working 
```
cd usr/src/rt73-cvs-2008071311/Module
sudo modprobe -v rt73
```

This is probably something I have to do every time a new kernel is installed.

---

### Post by flakjack47 on 2008-10-17
Hello,

I tried running this command (lsusb) in a terminal, even as root, but the terminal screen went blank and shut itself down. I have a similar Belkin wireless dongle, but don't know if it is version 3 or not.

I installed Ubuntu 8.04 Hardy Heron. When I ran it on the live CD with XP still there, it registered the presence of wireless networks/routers in range, but would not let me connect to them. The same thing happened when I installed Ubuntu dual boot with xp, and when I wiped XP completely for a clean Ubuntu install. After  I unplugged the belkin dongle and plugged it back in, Ubuntu no longer acknowledged its presence.

My install CD has no errors. The terminal shuts itself down and doesn't display any info when I try some of the commands on the other forum threads. 

There are lots of things I need to tweak but have no web access - including update the ntfs driver as I can no longer read my external HDD since doing a clean ubuntu install. My previously problematic GeForce6 card is working fine at 1400x900, though need some drivers from the web for 3d acceleration. (unlike in xp with constant restarts).

Any suggestions appreciated. I have an AMD Athlon 2400, 1280mb ram. I am an Ubuntu nooB, tired of all Windows and liking the Ubuntu interface and philosophy. But I need a little assistance, via web acces, to help me to help myself.
Cheers

PS I am using an Acer Aspire One (Linux Linpus Lite OS) netbook to access this forum

---

### Post by flakjack47 on 2008-10-17
Ok, an update. I re-tried the commands in a terminal opened directly from the menu, rather than via alt-f2 and received confirmation that Ubuntu sees my USB wireless adapter. I logged on to our wireless router and managed to receive a weak signal (36% or so) for about a minute. I opened firefox which then took me to ubuntu's welcome page. But then the connection cut, and I am having a problem again. My wireless adapter is detected, the networks in range are detected, but I cannot log on to our wireless network on my ubuntu pc. The connection is fine with my liux netbook.
Any suggestions?

---

### Post by flakjack47 on 2008-10-18
Beavering away again. Tried to install ndiswrapper to see if that helps. Couldn't find it in synaptic so found a command on here somewhere to install it via terminal. I get this message:

Reading package lists ... done
Building dependency tree 
Reading state information ... done
E: couldn't find package ndiswrapper-common

Now what??? Is there a way of accessing this ndiswrapper from the install cd like windows? 

Any help appreciated.

---

### Post by philinux on 2008-10-18
sudo apt-get install ndiswrapper-common

---

### Post by flakjack47 on 2008-10-18
Thanks for trying Phil. Unfortunately I get exactly the same message as above when I use this command.

---

### Post by scorp123 on 2008-10-19
> **flakjack47 said:**
> received confirmation that Ubuntu sees my USB wireless adapter. I logged on to our wireless router and managed to receive a weak signal (36% or so) for about a minute. I opened firefox which then took me to ubuntu's welcome page. But then the connection cut  Are you perfectly sure that the port you've plugged the USB-stick into is a USB 2.0 compliant one?

Why I ask:

I have a D-Link DWL-G122 USB WiFi-Stick and it works perfectly on Linux (it uses the "rt73usb" kernel module) ... for as long as I plug into a USB 2.0 port. If I try it on USB 1.1 ports I get the behaviour you describe.

---

### Post by flakjack47 on 2008-10-20
Pretty much. The wireless adapter has worked perfectly on xp on the same machine, reporting an 'excellent' signal and no interruptions. My laser mouse is a USB2 item with no issues so far. The machine was built for me in 2004, which I know is a while back, but fairly sure I asked for USB2 ports at the time.

Is there any way of knowing for sure whether my ports are usb2 or 1.1 with a terminal command say?

---

### Post by flakjack47 on 2008-10-21
An update. I found a longer cable and plugged stright into my wireless router to see if this helped. Still no web. 

I reinstalled XP Pro on my system, and then installed Ubuntu as a dual boot. This time, it picks up my wireless dongle, and lets me log on, consistently, and with a signal of between 30-50%, though I'm getting download speeds of under 1kb/s. It took over a minute to load everything on the google homepage. 

I tried the connection direclty with a cable, and there is a connection, but again at a similar speed of under 1kb/s. Isn't this very strange that the cable connection is doing this as well?
I would buy an out of the box compatible PCI desktop adapter, but what guarantee is there of that working?

Also worth noting is that there were many packages left out of the installation when I ran a full Ubuntu install. These are present in the dual boot install - the NVidia 2D drivers for example.

Any ideas?

---

### Post by hiasakite on 2008-10-26
Hi all- my first ever post on these forums!..

I installed Ubuntu 8.04 for the first time 4 days ago on an ageing Dell Latitude (C610) having spent the previous years on win NT,2K and XP, after my previous hard-drive 'lunched itself'. The last time i used anything linux based was 15-10 years ago..

Having installed a new hard drive, and having no windows disc, I installed Ubuntu instead.

I had a belkin f5d7050 wireless stick (UK version) that I used to use with my windows disk, I literally plugged it in to my laptop 30 minutes ago, and it worked out the box..

I have not installed ndiswrapper, I've not even installed any drivers for it (ie ie literally plugged it in, once I'd worked out how to get to the wireless networks tab, selected the network and put the key in it just 'worked')...


Having read loads of 'linux has driver problems etc' I really didn't expect this (I seem to recall it took seveal hours to get the stick working with windows when I was still running W2K-)


Not sure if I just happen to have a very lucky hardware combo or something but I'm impressed- any thoughts (remember I'm completely new to Ubuntu and learning everything from scratch)?

To the OP- I hope you get your problems sorted- in theory (from my experience its should- in principal at least- work out the box)....

---

