---
title: "New to Linux! Please Help!"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by jsdieorksw on 2008-04-28
I'm new to linux, I'm currently dual-booting with vista and ubuntu 7.10 on my laptop. Ubuntu seems to be working fine except for my internet connection.  It works fine with Vista so I know it's not the connection.  I've tried several things that people wrote about in their threads but still no luck.  Could anyone spare some time to help an Ubuntu newbie get connected?

---

### Post by Monicker on 2008-04-28
> **jsdieorksw said:**
> I'm new to linux, I'm currently dual-booting with vista and ubuntu 7.10 on my laptop. Ubuntu seems to be working fine except for my internet connection.  It works fine with Vista so I know it's not the connection.  I've tried several things that people wrote about in their threads but still no luck.  Could anyone spare some time to help an Ubuntu newbie get connected?

You might want to say what you have already tried, so that people don't suggest things which did not work for you.

Is this a wireless or wired connection which is having problems?

---

### Post by oedha on 2008-04-28
you also should tell about what device is that ? name and type

---

### Post by jsdieorksw on 2008-04-28
Well actually most people will start out by asking me to enter this into my terminal: lshw -C network 

then most people will stop posting on my threads so I'm not sure what works and what doesn't. anyway this is what it says 

*-network UNCLAIMED 
description: Ethernet controller
product: AR5006EG 802.11 b/g Wireless PCI Express Adapter 
vendor: Atheros Communications, Inc. 
physical id: 0 
bus info: pci@0000:01:00.0 
version: 01
width: 64 bits 
clock: 33MHz 
capabilities: cap_list 
configuration: latency=0
*-network 
description: Ethernet interface 
product: RTL-8139/8139C/8139C+ 
vendor: Realtek Semiconductor Co., Ltd. 
physical id: 1 
bus info: pci@0000:02:01:0
logical name: eth0
version: 10
serial: 00:1b:38:f9:31:d8
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list ethernet physical 
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes 

I hope this information can get some things started

---

### Post by yogo on 2008-04-28
I would try it hard wired, then if you connect effortlessly, you have to work on wireless settings.

---

### Post by jsdieorksw on 2008-04-28
Might be a good idea, I won't go into a whole thing about my situation but I really need my wireless connection to be working ASAP, I'm actually planning on paying someone to come out and set everything up for me, but if I could get it up and running on my own beforehand so I can cancel the appointment and not have to pay that would be great.  In other words, I really need my wireless connection working.

---

### Post by Monicker on 2008-04-28
> **jsdieorksw said:**
> Well actually most people will start out by asking me to enter this into my terminal: lshw -C network 

then most people will stop posting on my threads so I'm not sure what works and what doesn't. anyway this is what it says 

*-network UNCLAIMED 
description: Ethernet controller
product: AR5006EG 802.11 b/g Wireless PCI Express Adapter 
vendor: Atheros Communications, Inc. 
physical id: 0 
bus info: pci@0000:01:00.0 
version: 01
width: 64 bits 
clock: 33MHz 
capabilities: cap_list 
configuration: latency=0
*-network 
description: Ethernet interface 
product: RTL-8139/8139C/8139C+ 
vendor: Realtek Semiconductor Co., Ltd. 
physical id: 1 
bus info: pci@0000:02:01:0
logical name: eth0
version: 10
serial: 00:1b:38:f9:31:d8
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list ethernet physical 
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes 

I hope this information can get some things started

*sigh*  I see that you opened several threads in regards to a wireless problem.  In a couple of those threads you did not give the information that was requested in order to help you better.

Are you talking about a wireless connection again???

If so, give the outputs of the following command:

```
iwconfig
```

Take a good look at this:
[http://ubuntuforums.org/showpost.php?p=4259805&postcount=14]("http://ubuntuforums.org/showpost.php?p=4259805&postcount=14")

---

### Post by yogo on 2008-04-28
Understandable, wireless is easy but first I would say connect hardwired. Afterwards several people can help you out, last time I had to it was was ndiswrapper, not sure if that is required now but I am running out the door, someone should be able to help you out, I would google your wireless adapter listed above with Ubuntu and that should get you started.

Try this link, just a quickie [http://ubuntuforums.org/showthread.php?t=520903](http://ubuntuforums.org/showthread.php?t=520903)

---

### Post by jsdieorksw on 2008-04-28
I'm sorry if i didn't provide the info that was asked, please keep in mind that I am indeed a newbie with ubuntu. anyway when i type in command i get this: 

lo            no wireless extensions

eth0       no wireless extensions 


That sounds bad

---

### Post by billgoldberg on 2008-04-28
Well, it can be that the wireless card is not supported by ubuntu.

You could try ndiswrapper.

But it might be easier to just go out and buy a wireless usb adaptar the works "out-of-the-box" with ubuntu.

You'll find a list of supported cards here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)

---

### Post by Monicker on 2008-04-28
> **jsdieorksw said:**
> I'm sorry if i didn't provide the info that was asked, please keep in mind that I am indeed a newbie with ubuntu. anyway when i type in command i get this: 

lo            no wireless extensions

eth0       no wireless extensions 


That sounds bad

No drivers are being loaded for the wireless.   I think you will have to use ndiswrapper.

[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/]("http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/")

---

### Post by jsdieorksw on 2008-04-28
I've seen ndiswrapper mentioned in several places, what is it and would it help?

---

### Post by Monicker on 2008-04-28
> **jsdieorksw said:**
> I've seen ndiswrapper mentioned in several places, what is it and would it help?

ndiswrapper lets you use the windows drivers under linux for the wireless.  I think its your only option if you want the wireless to work.

---

### Post by MidChaos on 2008-04-28
ndiswrapper is used for particular chipsets in wireless cards. Basically what it can do if you are using one of the particular chipsets is use the Windows driver to make your card work.

Can you tell us the make/model of your computer?

---

### Post by Sjovan on 2008-04-28
Yeah, try ndiswrapper. ndiswrapper uses windows wirelessdrivers. A quick search in the forum will help you set up ndiswrapper :)

---

### Post by jsdieorksw on 2008-04-28
Ok when i type the command in this is what i get 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:02.1 Display contoller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)  
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01) 
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by jsdieorksw on 2008-04-28
I'm using a Compaq Presario A900

---

### Post by MidChaos on 2008-04-28
It looks like a common problem with your wireless card model. It is being misdetected as a previous one instead of what it is. I see there is a nice solution here:

[http://ubuntuforums.org/showthread.php?t=766529&highlight=ar5007eg](http://ubuntuforums.org/showthread.php?t=766529&highlight=ar5007eg)

Scroll down that page until about the 4th to last post, they have step by step instructions on what they did to get it working. You can try those and if it is or is not working after that please post back so that we can tell if this gets resolved.

---

### Post by jsdieorksw on 2008-04-28
Ok thanks, I'll give it a try and post back in a few

---

### Post by jsdieorksw on 2008-04-28
Nope, I went through the list of instrustions, entering in the codes and the first one didn't work; it said 
Resolving snapshots.madwifi.org... failed: Name or service not known 

then for the next one it asked for my Gutsy Gibbon CD and i don't have it with me at the moment

any suggestions?

---

### Post by MidChaos on 2008-04-28
Not sure why it wouldn't do the wget, I see the file is there on the server. As far as asking for the CD, you can disable the CD as a repository resource in Synaptic. As I am not at an Ubuntu machine I can't give you detailed instructions, but someone (hopefully) can give you step by step if you need it to disable the CD as a resource.

Out of curiosity, did you cut and paste the command or retype it when you did the first wget?

---

### Post by jsdieorksw on 2008-04-28
I'm gonna try the ndiswrapper suggestion, that or I guess I could get a new wireless card that works out of the box that would get me connected. Would this be the simplest solution?

---

### Post by jsdieorksw on 2008-04-28
I retyped but I'm sure I typed it correctly if thats what you mean

---

### Post by MidChaos on 2008-04-28
I've done ndiswrapper, it's not too bad, there's some good walkthroughs. I was trying to find the easiest solution, but feel free to try any suggested. As far as buying more computer equipment I really don't like doing that unless it's absolutely necessary. As other people seem to have gotten your card to work I would exhaust the things you can try before spending more money.

---

### Post by MidChaos on 2008-04-28
> **jsdieorksw said:**
> I retyped but I'm sure I typed it correctly if thats what you mean

Not questioning your typing skills, I would just suggest trying to cut and paste instead.

---

### Post by jsdieorksw on 2008-04-28
I'm gonna try ndiswrapper, hopefully it will work, post back later

---

### Post by jsdieorksw on 2008-04-28
I'm such a newbie, can anyone help out with ndiswrapper now? I downloaded through my Vista OS on the ndiswrapper website, can anyone help out with how to install it to ubuntu so i can connect to the internet?

---

### Post by WoodyMahan on 2008-04-28
It looks like the list of instructions offered by MidChaos in post #18 of this thread requires that you have some sort of internet connection on your laptop.  If you don't have an ethernet cord plugged in providing an alternate connection on your machine then that is probably what caused the commands to fail on you.

---

### Post by jsdieorksw on 2008-04-28
Makes sense, thanks. No, i don't have a cord plugged in or anything, just wireless, i've been switching between my OSs all day in order to use the internet on Vista and trying to get the web working through Ubuntu

---

### Post by MidChaos on 2008-04-28
> **WoodyMahan said:**
> It looks like the list of instructions offered by MidChaos in post #18 of this thread requires that you have some sort of internet connection on your laptop.  If you don't have an ethernet cord plugged in providing an alternate connection on your machine then that is probably what caused the commands to fail on you.

I should have thought of that... :oops:

---

### Post by yogo on 2008-04-28
> **jsdieorksw said:**
> Makes sense, thanks. No, i don't have a cord plugged in or anything, just wireless, i've been switching between my OSs all day in order to use the internet on Vista and trying to get the web working through Ubuntu


You are in good shape and this should be easy to remedy. Figure out everything you need like ndiswrapper, drivers, etc to get your wireless going. Download them all at once on a windows box, burn a cd, write to a memory card, but get all these files in one place. That way when you boot into Ubuntu you will not have troubles installing anything. Just do so from the cd/usb drive etc.

Now, I had troubles about a year ago, I needed ndiswrapper and posted this thread.
[http://ubuntuforums.org/showthread.php?t=521474](http://ubuntuforums.org/showthread.php?t=521474)

The second reply has a link about ndiswrapper.

I am sure if you follow that thread, it should resolve your issues.

As for buying another wireless card I would not, your wireless is built-in?

The tread is only three pages and should provide what you need, our wireless has never failed since I did that.

---

### Post by jsdieorksw on 2008-04-28
I installed ndiswrapper using synaptic package manager, i just made a new boot cd of ubuntu, i'm gonna look over this thread to see if it can help, thanks so much guys! i'll let you know if it works!

---

### Post by jsdieorksw on 2008-04-28
Didn't work, the thread kinda just tells me to do things without telling me how to do it, i'm not that familiar with ubuntu yet and it was all kinda confusing to me

---

### Post by jsdieorksw on 2008-04-28
Didn't work, the thread kinda just tells me to do things without telling me how to do it, i'm not that familiar with ubuntu yet and it was all kinda confusing to me. I'll just go out and buy a new wireless card that will work with ubuntu on my laptop

---

### Post by MidChaos on 2008-04-28
Out of curiosity, did you try the link I gave you earlier with a wired connection?

---

### Post by yogo on 2008-04-28
> **jsdieorksw said:**
> Didn't work, the thread kinda just tells me to do things without telling me how to do it, i'm not that familiar with ubuntu yet and it was all kinda confusing to me. I'll just go out and buy a new wireless card that will work with ubuntu on my laptop

Sorry been kinda busy this morning.
As for ndiswrapper, it is fairly simple and straight forward. Install the driver for your wireless and you should connect, have you installed your driver?

Found this comment by raiwo here on another thread, may be your answer.

A quick howto for how I got my Atheros AR5007EG WLAN card working in Gutsy:

1. Install ndiswrapper. (sudo apt-get install ndiswrapper) You can also install ndisgtk to get a graphical interface for this. (sudo apt-get install ndisgtk)

2. Download [http://blakecmartin.googlepages.com/...er-0.1b.tar.gz]("http://blakecmartin.googlepages.com/atheros-ar5007eg-installer-0.1b.tar.gz") However, you only need the .inf-file that is inside (I believe it's called net5211.inf)

3. Install the .inf file in ndiswrapper, either with ndisgtk or the command "sudo ndiswrapper-i net5211.inf"

4. Disable the ath_pci module in the restricted manager.

5. Reboot, and you should be fine

taken from somewhere...

I know he has an 07 and yours is an 06 but it should work.

---

### Post by MidChaos on 2008-04-28
> **yogo said:**
> I know he has an 07 and yours is an 06 but it should work.

His is an 07 as well, it is being misread. I checked the computer specs on the Compaq website to make sure.

---

