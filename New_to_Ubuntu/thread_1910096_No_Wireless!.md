---
title: "No Wireless?!"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by Jake Sweeney on 2012-01-16
Hello everyone!
I am very new to Ubuntu and I've just recently purchased a reaktek rtl8192cu wireless adapter.The thing is though, I can't get it to connect to ANY wireless network. The device did come with some drivers but I have absolutely no idea what they mean and how to install them! HELP :(

---

### Post by jfbooth on 2012-01-16
> **Jake Sweeney said:**
> Hello everyone!
I am very new to Ubuntu and I've just recently purchased a reaktek rtl8192cu wireless adapter.The thing is though, I can't get it to connect to ANY wireless network. The device did come with some drivers but I have absolutely no idea what they mean and how to install them! HELP :(

I am no Linux whiz .. but will tell you what I know.

You will probably have to install some Linux driver(s).  To do that the easiest way, you need to connect your computer to the Internet via ETHERNET cable.  You get the drivers off the 'net and until you get the WIFI drivers, an Ethernet connection will get you online.

Then .. you have to find the correct driver(s) and any DEPENDENT packages.  It appears there is one available from the Realtek support site.  Go to [www.realtek.com](www.realtek.com), click on DOWNLOADS, and SEARCH for rtl8192cu.  FIND the correct LINUX driver for YOUR product.  Download it and save it to your Ubuntu desktop.

Unfortunately, you may be in for a frustrating task for a beginner because the download is a zip file .. which is OK, ... your Ubuntu will unzip it.  Inside the zip is (among other things) the driver you need, but you have to COMPILE it before it will work.

THEREFORE, I suggest you go to the networking section of this forum and ask over there for help in proceeding.  1.  There may be an easier way to get your Realtek Wifi card to work in Ubuntu.  2.  If NOT, someone can help you compile and install the one Realtek provides.

Sorry I could not be more help.  Maybe this will get you started.

---

### Post by Naggobot on 2012-01-16
I downloaded the driver package from Realtek just out of curiosity. 

There is a readme file, see section 8. 
"8. install.sh 
        Script to compile and install WiFi driver easily in PC-Linux"

Now there is no guarantee that it actually works but the probability is high. If you dare to run this install.sh script I might recommend doing so with root privileges.

1. Download the driver package
2. Unzip the zip file
3. Open terminal
4. cd. to the unzipped folder
5. type 

```
sudo ./install.sh 
```hope for the best and fear for the worst. There actually is no reason for anything to go wrong, I just want to warn you. There is also a documentation folder. I might recommend checking that also. It may contain something more and better information than just reference to install script. General principle is that never install anything except from repositories through Synaptic/Software center. Installing the driver like this violates this principle and if something goes wrong I have no idea how to remove the failed installation. 

I have never had to specially install a wifi driver with ubuntu. When I install the ubuntu I have network cable attached and the b43-fwcutter has gotten the source from net,  compiled and installed it. 

Before doing the installation from command line or before downloading any packages connect Internet cable and check system->administration->hardware drivers. With luck your driver is there already and all you need to do is activate it. 

good luck.

---

### Post by Naggobot on 2012-01-16
> I suggest you go to the networking section of this forum and ask over  there for help in proceeding.  1.  There may be an easier way to get  your Realtek Wifi card to work in Ubuntu.


I second this very warmly. All in all I suspect that there is some 100% better way to do this than by compiling and installing.

---

### Post by gandaran on 2012-01-16
> **Jake Sweeney said:**
> Hello everyone!
I am very new to Ubuntu and I've just recently purchased a reaktek rtl8192cu wireless adapter.The thing is though, I can't get it to connect to ANY wireless network. The device did come with some drivers but I have absolutely no idea what they mean and how to install them! HELP :(
which ubuntu version do you have?
if it is 11.10 and you have wired internet run this install command
```
 sudo apt-get install linux-backports-modules-cw-3.1-oneiric-generic
```
I believe rtl8192cu driver is included in this package or maybe I'm wrong but try it, it's the easiest way to install drivers.

---

### Post by Jake Sweeney on 2012-01-16
Thank you so much gandaran! It works! you would not believe how long I have spent trying to make this driver. I really appreciate that thank you :D__

---

