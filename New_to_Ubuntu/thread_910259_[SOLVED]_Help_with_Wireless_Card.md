---
title: "[SOLVED] Help with Wireless Card"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by RussW210 on 2008-09-04
Hello everyone, I am new to Ubuntu and need some help.

I just received my Dell Inspiron 530 yesterday with built-in Wireless 802.11g PTI Card.  The computer came with Vista installed but I wanted to try Ubuntu so I uninstalled Vista and loaded Ubuntu fine.

My problem: I can't get connected to the Internet with my wireless card... and I can't receive updates because I can't connect to the Internet.

Looking at the back of my computer at the wireless card, the "AIR" light is not lit up, which I take to mean that I am not open to receiving a signal.  I played around with the Network Settings and it won't locate my wireless router.  It was locating the router just fine on Vista.  Am I missing a driver or something?

Really appreciate any help I can get... and hope I am giving enough information... really frustrated and have been playing with this all morning... including going through the help and troubleshooting menu's on Ubuntu.

---

### Post by nothingspecial on 2008-09-04
First we need to know exactly which card you have.

Open up a terminal and paste this into it

```
lshw -C network
```

Then copy and paste what it says here.

---

### Post by RussW210 on 2008-09-04
I am using the BCM4318 [AirForce One 54g] 802.11g Wireless Lan Controller.

Sorry, cant copy it because I am on my laptop (to get internet) and trying to install on my desktop...

It does say "network DISABLED" under the Wireless Interface (below the BCM controller.  What other information can I copy over for you?

---

### Post by RussW210 on 2008-09-04
Here, I will copy most of it by hand:

WARNING: you should run this program as a super-user.
*-network
  description: Ethernet interface
  product: 82562V-2 10/100 Network Connection
  vendor: Intel Corporation
  ...

*-network
  description: Network controller
  product: BCM4318 [AirForce One 54g] 802.11g Wireless Lan Controller
  vendor: Broadcom Corporation
  physical id: 1
  bus info: pci.....
  version: 02
  capabilities: bus master:
  configuration: driver=b43-pci-bridge latency=64 module=ssb

*-network DISABLED
  description: Wireless interface
  physical id: 1
  logical name: wlan0
  serial: ----------
  capabilities: ethernet physical wireless
  configuration: broadcast = yes multicast=yes, wireless=IEEE 802.11g

---

### Post by halitech on 2008-09-04
check here, post 88

[http://ubuntuforums.org/showthread.php?t=190177&page=9](http://ubuntuforums.org/showthread.php?t=190177&page=9)

---

### Post by nothingspecial on 2008-09-04
Russ. It`s not the  done thing to have 2 threads about the same thing on the same forum. 

Anyway,

First check if you need to enable a restricted driver. The restricted drivers thing is somewhere in your menus, I have an older version of Ubuntu and it has changed so I don`t know exactly where.

If that doesn`t work install ndiswrapper

```
sudo apt-get install ndiswrapper ndisgtk
```

Then download the windows drivers for your driver. Open the windows drivers application in your menus and use it to install the inf file located in the drivers.exe.

---

### Post by RussW210 on 2008-09-04
I would love to try ndiswrapper but unfortunately my computer didnt give me "ndisgtk" when I installed ubuntu.

---

### Post by halitech on 2008-09-04
you may have to connect up with a wired connection to get ndiswrapper, ndiswrapper-common and ndisgtk installed and then we can try your wireless setup

---

### Post by RussW210 on 2008-09-04
I just brought my computer downstairs and connected it with a wire directly from the router and still got nothing.  Wasn't able to connect that way either.

---

### Post by MegaJim on 2008-09-04
Doesn't ndiswrapper/ndisgtk come on the 8.04 live cd?

---

### Post by RussW210 on 2008-09-04
That is what I thought MegaJim but when I tried the install command it couldn't find it.

---

### Post by halitech on 2008-09-04
> **RussW210 said:**
> I just brought my computer downstairs and connected it with a wire directly from the router and still got nothing.  Wasn't able to connect that way either.

in a terminal with the wire connected, type in```
ifconfig
``` and give us the output

---

### Post by RussW210 on 2008-09-04
I get the error message:

Couldn't find package ndiswrapper.

---

### Post by RussW210 on 2008-09-04
How can I copy stuff over to this forum?  I am typing on my laptop and getting information from my desktop (which won't connect to the internet).

---

### Post by halitech on 2008-09-04
did you run```
ifconfig
``` again with the wired connection?

---

### Post by halitech on 2008-09-04
> **RussW210 said:**
> How can I copy stuff over to this forum?  I am typing on my laptop and getting information from my desktop (which won't connect to the internet).

if you have a thumb drive you can copy the information to a text file and then paste it from the system with the connection

---

### Post by RussW210 on 2008-09-04
Trying to connect the wire directly to the computer again... will have shortly.

---

### Post by RussW210 on 2008-09-04
Here is what I get:

Edited

---

### Post by halitech on 2008-09-04
ok, still with the wire connected, in a terminal do```
sudo dhclient eth0
``` and post back any messages

---

### Post by RussW210 on 2008-09-04
OK, I got:

Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
Edited

---

### Post by halitech on 2008-09-04
ok, according to this
```
DHCPACK of 192.168.2.9 from 192.168.2.1 
``` you should have an ip address with the wired connection. see if you can load up a webpage now

---

### Post by RussW210 on 2008-09-04
Oh my god it worked!  Google connected!

What happened?  Did I do anything?  If I restart the computer will it stop working?

---

### Post by RussW210 on 2008-09-04
Unfortunately, I think it is only working because I have the wire connected.  This is only a temp. solution... I definitely need wireless because of the location of the computer from my router.

---

### Post by halitech on 2008-09-04
> **RussW210 said:**
> Oh my god it worked!  Google connected!

:D

> What happened?  Did I do anything?  If I restart the computer will it stop working?

we told the computer to ask for an IP address from the router and it did so :)

it should stay working as long as the cable is connected on startup. Now we can start working on your wireless. 

in the terminal, type the following
```
sudo apt-get install ndiswrapper ndisgtk
```

---

### Post by RussW210 on 2008-09-04
I get the same error message when I tried that before:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndiswrapper

---

### Post by halitech on 2008-09-04
d'oh, try this
```
sudo apt-get install ndiswrapper-common ndisgtk
```

---

### Post by RussW210 on 2008-09-04
Still get the same error message:

"Couldn't find package ndiswrapper-common"

---

### Post by halitech on 2008-09-04
can you post the output of```
cat /etc/apt/sources.list
```

---

### Post by RussW210 on 2008-09-04
Here you go:

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution. 
 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted 
 
## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted 
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe 
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
## team, and may not be under a free licence. Please satisfy yourself as to  
## your rights to use the software. Also, please note that software in  
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse 
 
## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 
 
## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu 
## users. 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner 
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner 
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by RussW210 on 2008-09-04
Looks like a bunch of the hardy-updates and hardy-securities are restricted.  Maybe that has something to do with it?

---

### Post by RussW210 on 2008-09-04
I am also going into the update manager now that I have a WIRED connection and downloading the 112 updates they say I should have.

---

### Post by MegaJim on 2008-09-04
what happens if you try to run

```
sudo apt-get update
```

also, if you type

```
sudo apt-get install ndis 
```
then hit tab twice, apt-get should print a list of all the modules that start with "ndis", this may help you find the appropriate package

---

### Post by RussW210 on 2008-09-04
does sudo apt-get update do the same thing as the update manager?  I will try it after I finish downloading these 112 updates from the update manager.

---

### Post by nothingspecial on 2008-09-04
Right, back. Sorry this isn`t our jobs, just had to give my kids tea and then read stories (I love "The Gruffallo")

As soon as the updates have finished installing
```

sudo apt-get install ndiswrapper-common ndisgtk
```

---

### Post by RussW210 on 2008-09-04
OK the updates installed and I did the ndiswrapper-common command and it is installing now... clicked Y for Yes...

---

### Post by RussW210 on 2008-09-04
New driver is available for update: Broadcom B43 Wireless Driver.  Installing and restarting now... we'll see how this works...

---

### Post by RussW210 on 2008-09-04
OK now I checked to enable the Broadcom Driver and I got a screen that says "Configuring b43-fwcutter"... should I check "fetch and extract firmware" and continue?

---

### Post by nothingspecial on 2008-09-04
Yep

---

### Post by RussW210 on 2008-09-04
You guys are awesome and I can't thank you enough... my computer has recognized my router and I have successfully connected wirelessly with the wire unplugged.

Bless you all... no matter how little I understand of what just went on (haha) you guys were still a lot better than the Windows support when I was running 97.

So all I had to do was install the updates with a wired connection, then enable the Broadcom driver, then it recognized a whole bunch of routers (including mine)...

thanks again guys!

---

### Post by nothingspecial on 2008-09-04
Hey Russ, Mark this thread as solved by clicking on the thingy that says thread tools near the top of the page. That way, anyone who has the same issue as you will know that this thread has their solution.

Glad you got it sorted.

:guitar:

---

### Post by halitech on 2008-09-04
glad that we were able to get things running for you :)

---

