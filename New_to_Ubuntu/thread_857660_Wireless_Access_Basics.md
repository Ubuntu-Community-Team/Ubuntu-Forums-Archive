---
title: "Wireless Access Basics?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by stackman1 on 2008-07-12
Hello All.  I am new to Ubuntu.  I have 2 laptops the one that I am communicating to you with is a Dell Inspiron 1100.  It runs Windows XP and connects wirelessly to my Linksys WRT54G (Firmware version 8.2.03) using a Linksys Wireless-G Notebook Adapter (WPC54GS V2)- a  pcmcia card.  It runs fine.

I decided to take my other laptop a Dell Inspiron 2500 and turn it into a Ubuntu only machine.  I increased the memory to 512mb and burned an ISO of Ubuntu 7.10 and loaded it.  Got 7.10 loaded and through the help of this board I have already fixed the resolution problem by modifying the Xorg.conf, so I am feeling pretty confident (haha).  I am writing because my Ubuntu laptop won't connect with my router when I insert my pcmcia card into it and reboot.  I have been reading a bunch of other threads but have not figured it out to yet.  I have tinkered a bit and have run the iwconfig and ifconfig but have no way of copying them over.  The device manager recognizes Broadcom AirForce 4318 but when I run iwconfig it tells me the 'access point is invalid'.

A lot of the threads have instructions about trying different things like fwcutter and ndiswrappers etc...which I am not against trying.....but part of the reason I wanted to build a linux laptop was so I could finally understand how things work.  Besides Microsoft is so unintuitive and bloated I never understood how I was fixing things or what actually was wrong in a given situation; just typing commands in that someone else told me to until it was fixed.

So I would like to ask those that respond for two things: help with connecting to my router but also patience with my questions that deal with the big picture.  If you would like to help me maybe you could answer my first question which has to do with how things work.

As I said I loaded 7.10 and have gotten a bit familar with the desktop environment but have added no packages.  I have not run my router software on the machine because I don't understand why I should have to.  I did bring up the Network Settings and typed in my ESSID, Password and WEP Key but as I said it tells me my access point is invalid.

So here are my questions:
1.  The lights on my card are on and I know the router is working because when I use the card in this XP machine it is fine - does it matter - that I am trying to access the same router - alternately from a Linux machine using the same pcmcia card?

2.  The router is broadcasting a general signal and if it is true that the card doesn't care what machine it is in and the card i lit up....then the problem must lie in the settings I have established on the Network Settings panel...right?  But they are so straight forward....ESSID, Wep, WEP Password...

Is my fundamental understanding correct?  Thanks for playing along.
Peter

---

### Post by TSS on 2008-07-12
Great questions!

1.) It does matter, because of drivers.  Because your computer comes preloaded with Windows, the driver for your wireless card is already integrated into the system.  On Ubuntu, you might have to take extra steps to make sure that Ubuntu has/knows what driver to use with your wireless card.

2.) Your answer to this question is above.  Linux does not have a driver that works with Broadcom 4318.  The reason is that Broadcom is a vendor that likes to keep its specifications seceret, and thus it is difficult for the open source community to write a driver for it.

Don't worry though, you have other options!  Ndiswrapper is a program that wraps around a Windows driver so Ubuntu can understand how to use it.  You can get your wireless card working using Ndiswrapper.  

Use this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

As you can see under testimonials, people have used that guide with your card succesfully.  I have a Broadcom wireless card myself, and it just takes a little extra work to get it working.

On a completly underelated note, you might want to consider changing your wireless network from WEP to WPA.  WEP is an insecure protocal, and anyone with a laptop who knows how to use Google could discover your key!

TSS

---

### Post by stackman1 on 2008-07-12
Thanks for the quick reply.  One thing that I don't understand is why Broadcom even appears in the Nickname of eth0

When I go to the Dell website for my specs - I see no hardware reference to anything Broadcom - 

CardBus controller = 02Micro 0z6933 and as I have said my pcmcia card is a Linksys.....so what is Broadcom actually a vendor of?  Is it hardware or software?

PS.  I will look into all your links....but would like to bounce questions off you if you don't mind?

---

### Post by TSS on 2008-07-12
I don't mind at all!

First, I think the eth0 you are thinking about is your wired connection (Ethernet 0).  Your wireless card should come up as wlan0 or something similar, once you get it working.  

As for the Broadcom part, Broadcom makes wireless cards, among other things.  I was basing my last post off of: "The device manager recognizes Broadcom AirForce 4318".  If you are working with a Broadcom 4318, then the guide I posted previously is correct, but I guess I'm not really sure where the Device Manager is getting Broadcom from.  I checked the specs of your laptop as well and I can't find anything about Broadcom either.

But here is someone who worked with what I think is your PCMIA card: [http://kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php](http://kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php)
Do you have the CD with XP drivers for your PCMIA card?

---

### Post by stackman1 on 2008-07-13
TSS...I went to that link you showed me and it looks like it is a good fit very clear about what to do.  He used the same exact card as me so I will go ahead and try his idea about 'wrapping' my windows driver from my pcmcia cd and I loading it into memory for every boot up.  Makes sense.  I'll post how that goes.

As to the broadcom issue.  From the contents of the link, he says that you have to 'blacklist' the broadcom driver....so my guess is that when Ubuntu *tries* to supply a driver for the card the Broadcom Airforce is probably the closest one??

One of the comments to the link referenced wpa security and I know you had suggested upgrading from wep so assuming I get my ubuntu laptop connected then the next step will be to upgrade to WAP.  It mentions having to download wpasupplicant package from apt-get.  The _ndiswrapper_ module for the card fix is obtained graphically via the Synaptics Package Mgr; whereas _wpasupplicant_ is done via apt-get.  Two different ways of bringing downloading utilities from the Ubuntu libraries?

Quick question on that then... when my XP and UBuntu laptops are both working, the change process to Wap would be to start on the router and change the security type and then go into each laptop and change to Wap?

Better stop here with my questions, getting too far ahead.

---

### Post by TSS on 2008-07-13
> **stackman1 said:**
> TSS...I went to that link you showed me and it looks like it is a good fit very clear about what to do.  He used the same exact card as me so I will go ahead and try his idea about 'wrapping' my windows driver from my pcmcia cd and I loading it into memory for every boot up.  Makes sense.  I'll post how that goes.

As to the broadcom issue.  From the contents of the link, he says that you have to 'blacklist' the broadcom driver....so my guess is that when Ubuntu *tries* to supply a driver for the card the Broadcom Airforce is probably the closest one??

One of the comments to the link referenced wpa security and I know you had suggested upgrading from wep so assuming I get my ubuntu laptop connected then the next step will be to upgrade to WAP.  It mentions having to download wpasupplicant package from apt-get.  The _ndiswrapper_ module for the card fix is obtained graphically via the Synaptics Package Mgr; whereas _wpasupplicant_ is done via apt-get.  Two different ways of bringing downloading utilities from the Ubuntu libraries?

Quick question on that then... when my XP and UBuntu laptops are both working, the change process to Wap would be to start on the router and change the security type and then go into each laptop and change to Wap?

Better stop here with my questions, getting too far ahead.

The wireless problem is a big enough problem to handle in itself, and I am not quite convinced that Broadcom is the way to go.  Ignore the Broadcom issue for now and try the method that is supposed to work with your Linksys Wireless-G Notebook Adapter.  You are right about the bcm43xx driver though, it is as close as Linux can get to supporting Broadcom cards out of the box.

The Synaptic Package Mgr is just a graphical program manager for apt.  Same functionality as apt-get, just with a GUI.  Two ways of getting the same thing :-). 

You are right about the process of changing to WPA.  As long as you chose a strong pass phrase, it should be secure enough.  

Post here with updates about your PCMCIA card!

---

### Post by jualin on 2008-07-13
Make sure that you know the exact model of your wireless card by typing on the terminal > lspci
lspcmcia This will list of of the hardware that you have. And therefore you will see the exact model for your wireless adapter. Good luck!

---

### Post by pofigster on 2008-07-13
Broadcom makes the chipset inside of the wireless card.  You could have a card made by Linksys that uses the Broadcom 4318 (or whatever).  For example, my ENCORE ENLI-N wireless card uses the Ralink chipset.

The Broadcom is actually more important than the Linksys part of the card, because it defines what drivers you need.

---

### Post by issih on 2008-07-13
Essentially, the linux kernel tries to load the best fit driver it can for the hardware it sees.

These drivers are known as modules. You get specific modules that are designed to be used as drivers for different wireless cards, and what is probably happening is that one is being selected as the best fit, and loaded, but it isn't actually the right one, so your card isn't working.

Ndiswrapper is simply another module, that operates by using information taken from the windows drivers. If you re going to use ndiswrapper you need to ensure that it is loaded in preference to any other module that the kernel thinks might support your card.

It is sometimes therefore necessary to blacklist certain modules so that the right module is loaded. If things don't work with ndiswrapper you might well need to look into blacklisting the modules that the kernel is currently trying to use.

Hope that makes sense :)

P.S. As suggested above, using lsusb and lspci to try and find out the actual hardware manufacturer (rather than the vendor) is often a good start.

---

### Post by TSS on 2008-07-13
I'd like a little knoweldge of my own for a situation like this.  Are the XP drivers that came with the card (I assume on a CD) actually drivers for any Broadcom 4318 card?  Or do they support Broadcom 4318, but have specific functionality for his card as well?  Which driver is the right choice to use in this situation?

---

### Post by issih on 2008-07-13
Honest answer is that it varies.. Some times the drivers that come bundled with the card are best, sometimes the hardware manufacturers generic ones are best, it just depends on what model you have and how lucky you are. Some vendors change enough that the generic ones don't work, some stick close enough to the reference design that they do, its a movable feast. Generally the ones that come on the windows cd are a good place to start.

If that doesn't work out, you can look at the ndiswrapper website:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

They have a list of specific cards and the drivers reported to work with them. If your specific model (ideally even down to the vendor id) is in that list then you can grab the drivers suggested there.

---

### Post by stackman1 on 2008-07-13
Hello Guys and Gals?...I followed the instructions provide by TSS's link [http://www.kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php](http://www.kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php)

He had the same card as I did Linksys WPC54GS V2 w/ Speedbooster.  Did the entire list of instructions and it went clean but there was no outcome; my **iwconfig** that I ran afterward showed:

lo  no wireless extensions
eth0 IEEE 802.11b/g ESSID: "wabash_router" Nickname="Broadcom 4318"
Mode=managed Access Point = Invalid

When I run **lspci**:
the network controller line says:
Network Controller: Broadcom Corp BCM4318 (AirForce One 54G) 802.11g wireless Lan Controller (rev 2)

When I run **lspcmcia**:
Socket 0 Bridge: (yenta cardbus) (bus ID: 0000:01:03:0)
Socket 1 Bridge: (yenta cardbus) (bus ID: 0000:01:03:0)

I also went to the link:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)
and checked and this is what it says:

   
   [I][I]1. Card: Linksys WPC54GS v2 SpeedBooster, 54mbps/125mbps – [http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416827132&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416827132&pagename=Linksys%2FCommon%2FVisitorWrapper)

    *
      Chipset: Broadcom BCM4318 Airforce One 54g 802.11g Wireless LAN Controller (rev 02)
    *
      pciid: 14e4:4318 (rev 02)
    *
      Driver: Linksys Driver CD: /mnt/cdrom0/Driver/NT/LSBCMNDS.inf, **bcmwl5.sys, LSBCMNDS.cat**
    *
      Other: Kernel: 2.6.15-1-586tsc, Ndiswrapper: 1.5-1 via Debian Etch, wpasupplicant: 0.4.9-1. Works fine, per WPA . Reports speed up to 125Mb/s.[/I][/I]

When I followed the ndiswrapper instructions: I was not told to bring in **bcmwl5.sys, LSBCMNDS.cat**.  Should I redo?

Thanks 

Finally as a separate but related issue.  As I said I am running two Dell Inspirons but only have one wireless card and are swapping back and forth to see what happens when I insert it in my Inspiron 2500 (Gutsy Gibbon) and then back to my Dell Inspiron 1100 to get on the internet.

I have an External HD (Western Digital) sitting in between and would like to use it to move bmp's or copies of msgs between the two laptops so I don't have to type out the stuff but as luck would have it, while FILE BROWSER can see the drive when I try to open it, it says CANNOT OPEN VOLUME...is there an easy way to fix this....would make life easier....

Thanks for all your help Peter

---

### Post by stackman1 on 2008-07-13
Quick follow on question...as I was doing the ndiswrapper instructions I was looking in the manual to see what they were actually doing and if I understand it all correctly the depmode and modprobe commands were making sure that the needed modules were loaded into memory instantly and during future boot ups.  So when I ran into trouble, I rebooted but stopped the startup via the escape key to see the commands that bootfile was going to run and saw nothing that reflected my ndiswrapper stuff; I looked in the vmlinuz and initrd files (at least the files that are not load modules) and saw nothing.  I went through all the system logs and saw nothing as well.

My **bootfile** appears to be only four lines:
Root (hd0,0)
Kernel /boot/vmlinuz-2.6.22.14-generic Root= UUID (hex #s)
Initrd /boot/initrd.img-2.6.22.14-generic
Quiet

Shouldn't I see the options that I supposedly loaded via NDISwrapper and which log is the right one to view - syslog, kern log??

---

### Post by rizitis on 2008-07-13
Sorry Wrong Post

---

### Post by TSS on 2008-07-13
That's too bad that the first try didn't work, but you can still get your wireless working!  I saw you tried a few things with ndiswrapper, did you follow the guide I posted ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)?](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)?)

If you load up the guide and search for AirForce, you will see that there are people who have gotten their wireless card to work using that guide, who have the same wireless card as you!

Don't worry about the files listed on the Ndiswrapper website, the guide gives you a link to a download that has all the files you need.  Give that guide a try and post back here with any issues you have.  It's a fairly detailed process, so make sure you follow all the steps.

---

### Post by stackman1 on 2008-07-13
Thanks TSS - I must have passed over that first link of yours, I will try that next and report back.

Do you have any thoughts about the bootfile....I was assuming that by following the ndiswrapper routine it would have modified my bootfile parameters but there appears to be no trace....

---

### Post by stackman1 on 2008-07-13
Well, I can't seem to catch a break....the latest link that I am attemting to use requires an internet connection.  Up till now I have been swapping my pcmcia card to my XP laptop and communicating with the board but have no way of downloading to my Ubuntu laptop because my external hard drive doesn't work with the Ubuntu laptop.  Seems like I am going backwards....

When I bring my Ubuntu laptop downstairs and place it next to the cable modem and plug the ethernet cable directly into my laptop, I get nothing.  Looks like now my first step is to get my Inspiron 2500 Gutsy Gibbon laptop to accept a direct ethernet feed from the cable modem.

As I stated at the beginning, I am a newwwwwbie so is my problem with my ethernet port a driver problem as well....do I need to obtain an Ubuntu acceptable driver for my ethernet connection?

Should the ethernet port be listed by issuing an lspci command.

I will not give up!
Thanks

---

### Post by stackman1 on 2008-07-13
> **stackman1 said:**
> Well, I can't seem to catch a break....the latest link that I am attemting to use requires an internet connection.  Up till now I have been swapping my pcmcia card to my XP laptop and communicating with the board but have no way of downloading to my Ubuntu laptop because my external hard drive doesn't work with the Ubuntu laptop.  Seems like I am going backwards....

When I bring my Ubuntu laptop downstairs and place it next to the cable modem and plug the ethernet cable directly into my laptop, I get nothing.  Looks like now my first step is to get my Inspiron 2500 Gutsy Gibbon laptop to accept a direct ethernet feed from the cable modem.

As I stated at the beginning, I am a newwwwwbie so is my problem with my ethernet port a driver problem as well....do I need to obtain an Ubuntu acceptable driver for my ethernet connection?

Should the ethernet port be listed by issuing an lspci command.

I will not give up!
Thanks

That link that I am trying to follow by the way TSS is the one you suggested:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202:%20Download%20and%20Extract%20Drivers]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202:%20Download%20and%20Extract%20Drivers")

---

### Post by TSS on 2008-07-13
> **stackman1 said:**
> Well, I can't seem to catch a break....the latest link that I am attemting to use requires an internet connection.  Up till now I have been swapping my pcmcia card to my XP laptop and communicating with the board but have no way of downloading to my Ubuntu laptop because my external hard drive doesn't work with the Ubuntu laptop.  Seems like I am going backwards....

When I bring my Ubuntu laptop downstairs and place it next to the cable modem and plug the ethernet cable directly into my laptop, I get nothing.  Looks like now my first step is to get my Inspiron 2500 Gutsy Gibbon laptop to accept a direct ethernet feed from the cable modem.

As I stated at the beginning, I am a newwwwwbie so is my problem with my ethernet port a driver problem as well....do I need to obtain an Ubuntu acceptable driver for my ethernet connection?

Should the ethernet port be listed by issuing an lspci command.

I will not give up!
Thanks

The Ethernet is a good first step.  I'm trying to find specs for your computer online, but I cant seem to find two that agree.  It would be really awesome if you could figure out a way to post the output of 'lspci', here.   It would speed things up a lot.

Also, for your external hard drive, you might try pulling it in while the computer is off, and then starting the computer up.

EDIT: Try this... maybe you could just type it over if it works:
```
 lspci | grep 'Ethernet'
```

---

### Post by stackman1 on 2008-07-14
Thanks for hanging in there TSS.  I agree the first step is probably to get my ethernet port working.  As I have mentioned, I have a Western Digital External Drive that could serve as a go between to paste clips etc about my progress.  It isn't working either and I probably have the same issue of having to reload drivers I suspect?  So I am resetting my focus to getting my ethernet port working.  I looked through my original work order (2002) and have printed out the specs for the Inspiron 2500 and there is no mention anywhere about the ethernet card (no 10/100 Cardbus).  It has two ports, one for the phone line and one for the ethernet, and of course I know it works because when the laptop was running XP it was fine.  I assume this is because XP loaded the necessary drivers at startup?  
I went to the Dell website and searched under their network drivers for the Inspiron 2500 and while I see some drivers for 10/100 cardbuses I think I may call Dell to get them to tell me which one to download.
I have an external iomega CD writer so I can burn a disk and then upload the disk into my 2500.
Can you think of anything else I might need beside the recommended driver to put on the CD?
Thanks.

---

### Post by stackman1 on 2008-07-14
Well even my External CD-R/W crapped out on me so I bought a usb flash drive (which I should have done a long time ago).  So I will try to post some images.....I called Dell to find out the proper driver to re-establish my ethernet port.  It came in a compressed zip file which I have expanded - below are the contents (hopefully) of the driver file (R36933.exe):

---

### Post by stackman1 on 2008-07-14
Geesh ... how do I get my .bmps to appear normal size instream and not as an attachment?  I am having a really bad day...I don't see any help tips on the Ubuntu site for pasting...no does this message header offer an icon that doesn't ask for an url.....

---

### Post by stackman1 on 2008-07-14
Hopefully this is better; here are the windows files associated extracted from the executable that Dell says is the proper driver to restore communication to my ethernet port: 

/media/disk/R36933/ADDEM900.TXT
/media/disk/R36933/EL575ND3.SY_
/media/disk/R36933/EL575ND4.SY_
/media/disk/R36933/EL575ND5.SY_
/media/disk/R36933/NET575N5.INF
/media/disk/R36933/net575n5.cat
/media/disk/R36933/tc575ndi.dl_
/media/disk/R36933/Un3c575.exe

I assume Un3c575.exe is the setup program but I am not sure if I should even attempt to run it on my Ubuntu machine.  It is a windows program after all.  I have read that Wine might be helpful but don't know anything about it, plus I have read it is not a good idea.  

So am I back to using a utility like ndiswrapper?  If so do I include all the files except the txt and exe?

Here is the long awaited look at my pci.

peter@i2500:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
01:03.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
01:03.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
01:0b.0 Communication controller: Agere Systems WinModem 56k (rev 01)
peter@i2500:~$ 
peter@i2500:~$ lspci | grep 'Ethernet'
peter@i2500:~$ 

Thoughts?

---

### Post by stackman1 on 2008-07-16
Back on the wireless front...I went through the routine as laid out by the link: [http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318]("http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318")
and it looked like it did everything flawlessly except allow me to connect to the web.

**Here is the iwlist from the log:**
Log of iwlist scan 
 Tue Jul 15 19:29:14 2008

lo        Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:1D:7E:E8:74:86
                    **ESSID:"minnesota_router"**
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

**Here are the iwconfig and ifconfig:**
peter@i2500:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  **Access Point: Not-Associated   **
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

peter@i2500:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:BF:76:15:64  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:38000000-38002000 

eth0:avah Link encap:Ethernet  HWaddr 00:14:BF:76:15:64  
          **inet addr:169.254.5.61  Bcast:169.254.255.255  **Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Memory:38000000-38002000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6904 (6.7 KB)  TX bytes:6904 (6.7 KB)

Questions:
1. The iwlist showed the correct essid, so I assume that means the wireless signal is being received?
2. The access point is *not associated*.....meaning??
3. The inet addresses in bold are supposed to reflect what device address?

Any thoughts will be greatly appreciated.

---

