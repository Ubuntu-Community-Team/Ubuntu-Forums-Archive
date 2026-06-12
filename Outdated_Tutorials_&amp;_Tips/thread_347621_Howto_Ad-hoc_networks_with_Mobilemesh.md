---
title: "Howto: Ad-hoc networks with Mobilemesh"
date: 2007-01-27
forum: Outdated Tutorials &amp; Tips
---

### Post by spd106 on 2007-01-27
If you want to create an mobile ad-hoc mesh network with several nodes that are able to dynamically alter paths to find each other, then this is for you. See [http://www.mitre.org/work/tech_transfer/mobilemesh/](http://www.mitre.org/work/tech_transfer/mobilemesh/) for more information.

This guide charts the method I used to set up a small test network of three nodes sharing an Internet connection. If you have any problems or difficulties please post them below. Most of this guide uses a terminal for issuing commands, when it comes to editing files I have mentioned gedit, but there is no other dependence on GNOME. I have tested this guide on Ubuntu 6.10 (Edgy) i386 only. All systems were fully up-to-date as of 26 January 2007. Please make sure that you have the Universe repository enabled before you begin.

[SIZE="3"]** Step 1: What you will need**[/SIZE]
In order to run mobilemesh you will need at least one network card that is already setup and known to be working. If you are going to use wireless then please ensure you have a driver that works, I have tested this only on madwifi and an NDISwrapped Broadcom card (v1.33).

**Wired/Infrastructure mode**
Mobilemesh does work on wired/infrastructure networks quite happily, but it won't take advantage of the dynamic routing. 

**Ad-hoc mode**
If you want to use ad-hoc mode then so far I have come accross three scenarios
(i) Some cards, such as those running ndiswrapper, should work simply by changing the interface into ad-hoc mode. ```
sudo iwconfig wlan0 mode ad-hoc
``` 
(ii) At the moment the bcm43xx driver does not support ad-hoc mode with the kernel's softmac stack, so you will have to replace it with the new dscape stack or switch to ndiswrapper.
(ii) For madwifi you will need to create a VAP in adhoc mode with the wlanconfig tool. Unfortunately Ubuntu doesn't include wlanconfig by default, so you will have to build madwifi from source. There may be a way to build just the tools, but I haven't found it yet.

[SIZE="3"]** Step 2: Install**[/SIZE]
Before you enable adhoc mode you will first need to download and install some software. Mobilemesh is packaged and ready for Edgy in the Universe repository. You can get it through Synaptic or at a terminal with ```
sudo apt-get install mobilemesh
```
Alternatively you can download the [package]("http://packages.ubuntu.com/edgy/net/mobilemesh") and install off-line. All dependencies are included on a default install of Ubuntu. 
After installation I found that it didn't create the /var/run/mobilemesh directory. So I had to create it manually.
```
sudo mkdir /var/run/mobilemesh
```
[SIZE="3"]
** Step 3: Enable connections**[/SIZE]
Assuming you have the interface in adhoc mode, you will need to attach it to an ssid (with WEP encryption).```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid mobilemesh
sudo iwconfig wlan0 key 012345678910
``` Next you will need to assign the interface an ip address. Here we will use local-link addresses, replace the Xs with any unique combination of numbers (1-255). ```
sudo ifconfig wlan0 169.254.X.X
```You should now have an adhoc network and be able to ping directly with other nodes that are in range.
[SIZE="3"]
** Step 4: Configure**[/SIZE]
Take note of the interface names you will be using, e.g. eth0, eth1, wlan0 etc. These need to added to the /etc/mobilemesh/mmrp.conf.
```
gksudo gedit /etc/mobilemesh/mmrp.conf
```It should look something like this ```
#
# Config File for Mobile Mesh Routing Protocol
# 
# This file is used to:
#   1) Specify configuration parameters for the routing protocol:
#        port         <Udp Port Number>
#        alpha        <float value>, where (1.0 <= value <= 2.0) 
#        minTxDelay   <unsigned int value>
#        maxTxDelay   <unsigned int value>
#        updatePeriod <unsigned int value>
#        maxAge       <unsigned int value>
#
#   2) Specify the interfaces that will participate in the MMRP 
#        interface <dev name> 
#
#   3) Specify external routes that should be advertised within the MMRP cloud
#        external <ip address> <netmask> <metric>
#
#

port 20471
alpha 1.0
minTxDelay 1
maxTxDelay 4
maxAge 20
updatePeriod 4

interface wlan0         # [color=red]<- Change/add interface here[/color]

#external 0.0.0.0 0.0.0.0 7

# Don't delete this line! 
```If you want to advertise an external internet connection then uncomment the external line, first making sure you have turned on ip forwarding and masquerading or setup firestarter.
[SIZE="3"]
** Step 5: Enable Mobilemesh**[/SIZE]
Each interface you want to use will need to have an mmdiscover daemon attached to it.```
sudo mmdiscover -i wlan0
```
Finally start mmrp to manage the routing protocols. ```
sudo mmrp
```
To check that it is up and working, view the kernel routing table. ```
ip route
``` 
[SIZE="3"]
** Step 6: Uninstallation**[/SIZE]
To bring down the mobilemesh daemons you can kill them directly. ```
sudo killall mmrp
sudo killall mmdiscover
``` Mobilemesh can be uninstalled through synaptic or apt.

[SIZE="3"]** Troubleshooting**[/SIZE]
A. First time through I found it useful to append the -z switch to check for error messages.
B. Check that you have named each of the interfaces to be used in the /etc/mobilemesh/mmrp.conf file and that they each have an instance of the mmdiscover daemon attached to them.
C. Remove any interfaces from the /etc/mobilemesh/mmrp.conf file that are not being used by mobilemesh.
D. Run tcpdump or wireshark to catch packets as they are sent between nodes.
E. If you have difficulty changing the interfaces to ad-hoc mode or changing the wireless network settings, it might be a good idea to comment out the relevant sections of the /etc/network/interfaces file. Be sure not to delete this file or alter the Lo interface.
F. According to the information I gathered mobilemesh is a set of userspace tools, so it shouldn't need root privilege. However, when trying to run as a normal user it complains about access to certain root owned files. This is why I have chosen to run all commands as root, though I'm not sure if this presents a security risk.

[SIZE="3"]** Credits**[/SIZE]
Thanks to Mitre for creating this software tool and releasing it under an open source license. Also, thanks go to the Debian and MotU teams for packaging Mobilemesh.

---

### Post by Triorph on 2007-02-13
nice howto, you said that broadcom drivers don't support this using the softmac stack, would you care to explain how to change them to dscape stack?

---

### Post by spd106 on 2007-02-13
I was hoping no-one would ask that question. Basically it is going to involve big changes to the system, such as rolling your own kernel. I haven't tried this yet since it's a bit out of my league. 

However, there is a thread at linux questions about doing just this.
See [http://www.linuxquestions.org/questions/showthread.php?t=444476](http://www.linuxquestions.org/questions/showthread.php?t=444476)

The simpler way is to use ndiswrapper, at least for the foreseeable future.

---

### Post by UAhmad on 2008-11-10
Hi Guys i want to use this tool in for my project to demonstrate what happen when we add more nodes to Mobile Mesh Network.I've successfully install the software. All i need is some other tools that can monitor the performance of the network by adding more services on the such as voice , ftp,..etc.

If anyone can help me..Please 


Cheers
Uahmad

---

