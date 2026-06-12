---
title: "verizon DSL connect problem ubuntu 7.10"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by RickyFingers on 2008-04-22
I'm not very experienced with Linux or networking, configuring network/internet connections. I've been booting my PC with
Ubuntu LiveCD 7.10 Gnome and it looks great. I'd toss out XP and go for the full install of ubuntu/linux if I could get my internet connection to work. My ISP is Verizon through a Westell DSL modem. I’ve read in these forums and others that this has been a problem and still is (Version DSL that is). I was under the impression that Ubuntu would automatically detect the Ethernet connection. Shall I switch my ISP? Can someone recommend one that will work with Linux? Or has someone been able to figure out an easy way to get around Verizon's lack of vision.

I’ve tried the sudo ppoeconfig, poff DSL-provider, ifconfig and have been through the documentation.

thanks for your time

---

### Post by nicedude on 2008-04-22
To start tell me more about your machine Make? Model? brand of ethernet network chipset?

you can use the following to check wired adapter availability
ifconfig -a -v

and post the text of the results along with answers about yoour box if you know them.

---

### Post by propwashz on 2008-04-22
I´m new to linux,too -- but not to the westell modem (I hate it!)
I don´t remember off the top of my head,so you´ll have to google it,but you need the default IP address of the Westell modem itself--
THEN , either from windows or linux (it shouldn´t matter),open a browser and type in [http://the](http://the) IP of the modem (something like 192.168.1.1--but look it up) in the address bar and hit enter.This will open the menu interface of the modem.Change it to BRIDGED mode(instead of DHCP)--THEN connect a router to the modem--your computer to the router--put in your DSL name and pasword in the menu item that asks for it in the router,save and exit--and voila´ --Hardy(or any linux distro) and windows both connect--
This is how I got a reliable no hassel connection with the westell modem--with ALL operating systems--if you only have one computer--somebody might have an easier answer--but I know this one works (going on 4 years now without a glitch)

---

### Post by RickyFingers on 2008-04-23
I have been unable to get into my Westell Wirespeed CR90 modem to try and reset it to BRIDGED. I search a lot of forums and followed a lot of directions. But no joy Mr. Propwashz.

In windows my ipconfig looks like:
Windows IP Configuration
Ethernet adapter Local Area  Connection:

Connection Specific DNS Suffix:
IP Address: 71.107.230.xxx
Subnet Mask: 255.255.255.0
Default Gateway: 71.107.230.1
Mac address : 00-50-70-85

the hardware is VIA Rhine II Fast Ethernet Adapter

Intel(R)
Pentium(R) 4 CPU 2.80GHz,
2.79GHz, 480 MB RAM 60 GB hard drive

Output from ifconfig:

eth0  Link encap:Ethernet HWaddr 00:50:70:85:71:DC
      inet6 addr: fe80::250:70ff:fe85:71dc/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX packets:3 errors:0 dropped:0 overruns:0 frame:0
      TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:1578 (1.5 KB) TX bytes:5746 (5.6 KB)
      Interrupt:18 Base address:0xe800

eth0:avah Link encap:Ethernet HWaddr 00:50:70:85:71:DC
          inet addr:169.254.8.208  Bcast:169.254.255.255 Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          Interrupt:18 Base address:0xe800

lo  Link encap:Local Loopback
    inet addr:127.0.0.1 Mask:255.0.0.0
    inet6 addr: ::127.0.0.1 Scope:Host
    UP LOOPBACK RUNNING MTU:16436 Metric:1
    RX packets:16 errors:0 dropped:0 overruns:0 frame:0
    TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:1184 (1.1 KB) TX bytes:1184 (1.1 KB)

---

### Post by propwashz on 2008-04-23
First ,with the computer connected to the westell modem by ethernet(NOT usb), try following the instructions [here]("http://www.shaka.com/support/verizon/Westell_Wirespeed_220015_Bridge_convert.pdf")

even if your modem model isn´t that exact one,the intructions should be the same..

Then--
1. unplug the ethernet cable from the back of your computer,and plug it into the WAN port on your router

2. plug the ethernet cable that came with your router into a lan port on the router,and into the ethernet port on the back of your computer

3. follow the instructions that come with your router for setting up your router with the name and password for your DSL account (can´t give specific intructions here ,because I don´t know what kind of router you have/will get)

ALSO--don´t put your modem into bridge mode until you DO have a router ready to hook up--because it will no longer assign your computer an IP address and you won´t be connected to the internet anymore unless you fiddle with other settings which will just complicate things....your router will assign your IP address now and save your login info so you are always connected to the internet..

AND--if you have ever had your modem connected to your computer by USB instead of ethernet under windows UNINSTALL the software for the USB connection thru add-remove programs before you st..art all this,just to avoid conflicts in windows(it won´t have any effect in linux)

---

### Post by propwashz on 2008-04-23
the word (here) in the above post is a link to a pdf file with instructions==forgot to make the link a different color so you could tell,but it still works

---

### Post by propwashz on 2008-04-23
Here´s a webpage with some slightly different instructions for putting the modem in bridge mode--I used the ones in the pdf file with my modem,but if they don´t work for you--try **_[these]("http://www.voipmechanic.com/westelltobridge.htm")_**

---

### Post by propwashz on 2008-04-23
more bridged mode - router instructions ***_[here]("http://www.dslreports.com/faq/9265")_***

let me know when you get connected--I´ll quit sending instructions:)

---

### Post by RickyFingers on 2008-04-23
I don't have a router. I'm going directly from the ethernet port from the PC into the ethernet port on the modem Westell CR90.

---

### Post by propwashz on 2008-04-24
> **RickyFingers said:**
> ......................Shall I switch my ISP? Can someone recommend one that will work with Linux? ***Or has someone been able to figure out an easy way to get around Verizon's lack of vision.***

I’ve tried the sudo ppoeconfig, poff DSL-provider, ifconfig and have been through the documentation.

thanks for your time

The way I got around Verizon´s lack of linux and/or BSD support --was to buy a cheap router.No wireless,only one computer at the time,but the router keeps me connected no matter which OS I boot into,without having to configure anything...and it was surely easier than changing ISPs.:)

Good luck--

---

### Post by RickyFingers on 2008-04-24
NICEDUDE wrote, "

 I know why your DSL doesn't work
DSL modems operate with PPPOE (point to point protocol over Ethernet) This requires support for PPPOE either from the PC (in the case of a direct connection) or a router (which then can handle it for you) Some Linux guru's should have spotted this but no one did I guess. I was about to suggest checking some other things when it came to me that you don't use a router and I was sure when I looked at your windows IP & Gateway and seeing that your windows IP was a WAN ip (71.107.XX.XX) not a LAN ip (192.168.X.X) Wow now that I figured that out how to get it fixed.

You could buy a router (Netgear or Linksys Preffered) for $40-$70 and it will handle your pppoe for you with a little bit of config work.

OR

You can install a linux software that will enable PPPOE support for your system $0. While I figure this is what you will want to do, in the future you might look at a router down the road because on top of adding wireless capability they come with firewalls built in to make internet life much easier.

All that said the problem was I found several places telling how to do PPPOE but they all wanted you to download a program from inside linux which isn't possible for you since you have no NET with linux. Finally I found the program at a Ubuntu Deb package site (deb packages are programs all packaged up that when you download them you can just doubleclick and install them provided they were packaged for your operating system). Well here are some links to instructions and the software you need. So you will need to download these links from inside Windows and then put them on a disc or drive that you can access from Ubuntu. You need to read up on what you will have to do to install and configure as even though I have DSL I use a router so I have never used the software in question.


Forum post with instructions
[http://ubuntuforums.org/archive/index.php/t-214734.html](http://ubuntuforums.org/archive/index.php/t-214734.html)

Source for software in question
[http://packages.ubuntu.com/gutsy/pppoe](http://packages.ubuntu.com/gutsy/pppoe)
And a configuration program for the above
[http://packages.ubuntu.com/gutsy/pppoeconf](http://packages.ubuntu.com/gutsy/pppoeconf)

Well that should keep you busy for a while and at least you learned something new today "

-----

Thanks for the super effort! You really are THE NICEDUDE. There are several postings/threads by very frustrated people who want to use Ubuntu but can't connect to the internet so they give up. This weekend I buying a KVM box/switch so I can get both my PC's hooked up to one monitor, keyboard and mouse. I'm also going to get a Linksys wired/wireless router and hook or try to hook myself up this weekend. I have no problem learning something new, that's one of the reasons I'm here. You are awesome nicedude, Thanks! Your solution should be posted for all to see in the Tips and Tricks section or somewhere the public can find it.

---

### Post by RickyFingers on 2008-04-27
I'm typing this online from a LiveCD Ubunto 7.10, The solution to my problem was to get behind a router. So now connect to the DSL box through a Linksys router and all my LiveCD distros can access the internet. Thanks to all that helped me get on line. Now I'm going recover a windows 98 machine that I was using as a doorstop and put it better use.

Thanks again!

---

