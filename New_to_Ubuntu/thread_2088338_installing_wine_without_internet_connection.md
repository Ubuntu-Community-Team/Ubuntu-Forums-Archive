---
title: "installing wine without internet connection"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by iboontoo on 2012-11-26
Hi everyone,

I'm trying to install wine on my ubuntu, but I don't have internet  connection in ubuntu. I need wine to install my internet provider's software to connect to DSL.
I downloaded the tar ball, extracted it with command "tar". But, the "configure" file inside the archive is not executable. I tried "sudo chmod +x configure" but it didn't help. The same is true with the "wineinstall" file. 
Since I don't havr internet in ubuntu, I couldn't use apt-get or the like.

Any help is appreciated.

Cheers,
iboontoo

---

### Post by squakie on 2012-11-26
I think you are going to find that installing a windows program for accessing the net in wine is not going to work for you.  That software is only known within wine, not on your entire linux installation.

Perhaps you could tell us more specifically what you need to do:

 - do you connect to the DSL modem via a hardwire or wireless?

 - is the DSL modem a USB dongle?

 - what is the make of the DSL modem?

 - what DSL service do you need to connect to?

Usually these things can all be configured in native linux.  The windows program in wine is not going to work for you.

---

### Post by iboontoo on 2012-11-26
good to know that!

- do you connect to the DSL modem via a hardwire or wireless?
hardwire

 - is the DSL modem a USB dongle?
dsl modem
 - what is the make of the DSL modem?
sphairon turbolink IAD
 - what DSL service do you need to connect to?
the provider is Alice dsl in Germany.

---

### Post by squakie on 2012-11-26
I'm not familiar with either, but that's because I live in the central north area of the U.S. and we just have U.S. "branded" equipment and services here.  However, I'm sure it is going to be very similar.  If you have the modem connect via hardwire (by cat5 I hope, not USB?) what happens when you try to connect?  I'm sure there will need to be domain servers, userid and password, etc., all set up.  This can be done in Ubuntu from what I've seen fairly easily, but since I'm no expert on that, I'll leave it to someone with connecting to DSL service experience to help you.  I'll try PM'ing a couple a see if they can help.

---

### Post by ajgreeny on 2012-11-26
Connect the modem to your machine then run ```
lsusb
```if you attach it by USB  or ```
sudo lshw -c network
```if attached by other means.

One or other, or maybe both, should tell us what chipset is used and give a clue where to go for drivers etc etc.

---

### Post by grahammechanical on 2012-11-26
Do you have a user guide for the Turbolink? That should tell you how to enter the modem/router's set up program to put in the details of your internet service provider.

I found this for you:

[http://support.microsoft.com/kb/309044]("http://support.microsoft.com/kb/309044")

I was looking for a user guide in the form of a PDF document that you could download. May be one of these links will give you the information you need.

I am assuming that the issue is your need to get the modem connecting to the ISP. With a cable connection from Ubuntu to the modem you should not have any problems. But if the modem is not connecting to the ISP then you will not have an Internet connection.

In regards to my router the user guide said this:

> Open your web browser and go to [Http://192.168.1.254](Http://192.168.1.254)
Enter admin as the Username
Enter the Serial Number as the Password.

You can find the Serial Number on the Setup Sticker included with this Thomson Gateway and on the bottom of the router itself.

May be you have something similar for your router.


Regards.

---

### Post by iboontoo on 2012-11-26
the output of 
```
sudo lshw -c network
```is
```
 *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: f0:bf:97:8d:60:ac
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f0100000-f013ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: cc:af:78:bd:95:3e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-31-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0000000-f000ffff

```by the way, I tried to set connection from within ubuntu. AFAIK there are at least 2 ways to do this. one is using the network connection gui, and one is to use /etc/network/interfaces. Are these the correct ways to solve this problem?
I tried to copy the settings from windows connection to setup the connection in ubuntu, but there are problems. 
first, in windows there are IP address, subnet mask and dns servers, but no default gateway specified. and with these settings in ubuntu connection manager (or whatever it is called) it does not work. I use the username and password that my internet provider gave me but it doesn't connect.
second problem is that the abovementioned ip address and dns server etc. change everytime I connect in windows.

And to make my problem clear, I have dual boot windows 7 and ubuntu, in windows I can connect to internet with the Alice software, but in ubuntu I cannot.

Thanks in advance for any help!

---

### Post by Shuudoushi on 2012-11-26
> **iboontoo said:**
> the output of 
```
sudo lshw -c network
```is
```
 *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: f0:bf:97:8d:60:ac
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f0100000-f013ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: cc:af:78:bd:95:3e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-31-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0000000-f000ffff

```by the way, I tried to set connection from within ubuntu. AFAIK there are at least 2 ways to do this. one is using the network connection gui, and one is to use /etc/network/interfaces. Are these the correct ways to solve this problem?
I tried to copy the settings from windows connection to setup the connection in ubuntu, but there are problems. 
first, in windows there are IP address, subnet mask and dns servers, but no default gateway specified. and with these settings in ubuntu connection manager (or whatever it is called) it does not work. I use the username and password that my internet provider gave me but it doesn't connect.
second problem is that the abovementioned ip address and dns server etc. change everytime I connect in windows.

And to make my problem clear, I have dual boot windows 7 and ubuntu, in windows I can connect to internet with the Alice software, but in ubuntu I cannot.

Thanks in advance for any help!
 
 It seems you are missing the drivers for your networking card. Go to the manufactures web-site and download them to a disc/USB stick and install the drivers. That should do the trick. If it doesn't you may need to pull your laptop apart and make sure the networking card is attached right.

---

### Post by squakie on 2012-11-26
The wired connection looks like it is fine - and the OP said they were using the wired connection to their DSL modem.  It's the wireless side that isn't configured but they sounded like they weren't using that.

OP:  are you talking about ALICE the programming tool, or ALICE the AI program?  If ALICE the programming tool, everything I have found so far in searching the net is at least a couple of years old.  Makes me wonder if this will even run with the current versions of ubuntu.

---

### Post by iboontoo on 2012-11-27
@Squakie,

Alice is the name of my internet provider. they are in Germany, [www.alice-dsl.de](www.alice-dsl.de)
now they are merged into O2.

@all
I still don't know what my problem is, let alone how to solve it.
I tried to update the driver for my network adapter (atheros ar8131) but I couldn't. After I ran "sudo /etc/init.d/networking restart,stop,start",... commands, I think I messed up my network configurations.

---

### Post by squakie on 2012-11-27
I just looked at that website but it's all in German(?).  Have you tried emailing them and asking them if they have instructions for setting up the connection using linux?

From what you said it would appear some of the "settings" are dynamic.  I'm sure there's a way to do that in the config as well - what we need is for someone who knows how to set up a DSL connection to respond.  I did PM a couple of the experts on this but they haven't replied yet.

---

### Post by iboontoo on 2012-11-27
Hi again,
I just went to my office and used internet via LAN cable. So, the problem shouldn't be about network adapter driver. The problem is that I can connect to DSL internet from windows (running the internet provider software which is alice-dsl.de) but in ubuntu, I cannot configure the connection.
If someone could tell me what I should put in the settings of "connection manager" or how to set etc/network/interfaces, that should solve it.
I already tried to copy settings from windows connection to ubuntu, but it doesn't work.

by the way, the title of this thread is misleading, should I post another thread?

---

### Post by Shuudoushi on 2012-11-27
LOL!!! I think I just figured out your problem! Your modem may be setup to use dynamic IP's. Go into your modems settings manager and change it to a static IP for all ports. That should fix your problem. This whole time i was sure it was an Ubuntu problem. Lol.

---

### Post by squakie on 2012-11-28
There's nothing wrong with dynamic IP addresses.  This still needs to be set up via /etc/network/interfaces - but I don't know how.  It seems to me there is a series of commands you can enter at the command line to set everything up.  This is what the OP needs help with.

I'll try looking around and see if I can find something that we might be able to follow to help you out.  I'm actually quite surprised (and a little disappointed) that no one has come to help on this.  I know there is also a [networking forum]("http://ubuntuforums.org/forumdisplay.php?f=336") - perhaps the people there might be of help.

I'm sorry I'm not knowledgeable enough myself to help you, but I'll go looking for things.

EDIT:  I found [this old thread]("http://ubuntuforums.org/showthread.php?t=1413113&highlight=setting+wired+connection+DSL") - it's a couple of years old so not current.  However, it does talk about using pppoeconfig to set it up.  Perhaps that can help.

---

### Post by iboontoo on 2012-11-30
Thanks for your effort. I really appreciate it. I will try this pppoe when I get home and will report the result.

---

### Post by iboontoo on 2012-11-30
I tried ```
sudo pppoeconf
``` and now it works!:guitar:

Thanks to everyone who helped.:popcorn:

---

### Post by squakie on 2012-11-30
> **iboontoo said:**
> I tried ```
sudo pppoeconf
``` and now it works!:guitar:

Thanks to everyone who helped.:popcorn:

Man am I glad that worked for you!

---

