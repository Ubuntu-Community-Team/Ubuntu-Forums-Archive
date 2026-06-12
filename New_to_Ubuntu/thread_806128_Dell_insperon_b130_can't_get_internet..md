---
title: "Dell insperon b130 can't get internet."
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Linux_noob616 on 2008-05-24
Hi, i am using a Linksys WRT54GS router and my friend (new to Linux like me) and i are trying to get internet access on it. But maybe we're doing something wrong, We put in my WEP key, and my network name. it searched and found nothing.

Any help would be great.

---

### Post by saj0577 on 2008-05-24
Have you got roaming enabled? Does it detect the network?

Saj

---

### Post by PriceChild on 2008-05-24
Type```
sudo iwlist scan
```into a terminal, press enter and put in your sudo password, then see if your network is listed, if not then you're not in range of the router.

---

### Post by Linux_noob616 on 2008-05-24
> **saj0577 said:**
> Have you got roaming enabled? Does it detect the network?

Saj

It was but then i tried to manually configure it and then the icon that was next to the sound is gone. And i can't configure it to roam anymore =/

As the name implies, i'm a Linux Noob.

---

### Post by Linux_noob616 on 2008-05-24
tried the "sudo iwlist scan"

> sudo iwlist scan

[sudo] password for name: 

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wmaster0  Interface doesn't support scanning.



wlan0     Interface doesn't support scanning : Network is down

The PC works fine in Windows XP. Internet is connected and everything, incase you were wondering.

---

### Post by Linux_noob616 on 2008-05-24
Bump.

---

### Post by sam_delta on 2008-05-24
what network card do you have? i think it has to do with the drivers, post the output of the command ```
 lspci
``` please

sam

---

### Post by Linux_noob616 on 2008-05-24
> **sam_delta said:**
> what network card do you have? i think it has to do with the drivers, post the output of the command ```
 lspci
``` please

sam

results are:
> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


And i am not sure, about cards, went to the dell site and got the following.

Broadcom - Diagnostics Utility
Applies to:
440x 10/100 Integrated Controller

Broadcom - Driver
Applies to:
440x 10/100 Integrated Controller

Dell - Driver
Applies to:
Wireless 1350 WLAN PC Card
Wireless 1370 WLAN MiniPCI Card

Dell - Driver
Applies to:
Wireless (Japan) WLAN Card

Dell - Driver
Applies to:
Wireless 1470 Dual-Band WLAN miniPCI Card
Wireless (US) WLAN Card

Dell - Driver
Applies to:
Wireless (Except US,Japan) WLAN Card

Applies to:
(R) PRO/Wireless 2200BG Network Connection
(R) PRO/Wireless 2915ABG Network Connection
(R) PRO/Wireless Network Connection

---

### Post by sam_delta on 2008-05-25
alright, try the following

1 plug an ethernet cable into your computer to get internet access.
2 make all updates (a notification icon will appear) if not, go into system>administration>update manager, and install all available  updates.
3 with the cable still plugged, go into system>administration>hardware drivers, and see if there is a broadcom driver listed, if it is, just click on it and enable it.
4 if there is no broadcom driver listed, come back and tell us

sam

---

### Post by Linux_noob616 on 2008-05-25
Nope nothing, can't get internet on Ubuntu like that either.:(

---

### Post by Linux_noob616 on 2008-05-25
Bump bump bump (i know this is probably annoying but i need an answer bad =/)

---

### Post by sam_delta on 2008-05-25
try installing b43-fwcutter by typing with the internet cable plugged

you need a cable connection to do this.
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
``` 
make sure you answer with "yes" when asked if you want to fetch a firmware
restart pc, and check if it works or if it shows under system>administration>hardware drivers if theres a broadcom driver listed



if it dosnt work, well need to try ndiswrapper

sam

---

### Post by Linux_noob616 on 2008-05-25
But i can't get a connection with the cable plugged into the laptop.

---

### Post by Linux_noob616 on 2008-05-25
> **sam_delta said:**
> try installing b43-fwcutter by typing with the internet cable plugged

you need a cable connection to do this.
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
``` 
make sure you answer with "yes" when asked if you want to fetch a firmware
restart pc, and check if it works or if it shows under system>administration>hardware drivers if theres a broadcom driver listed



if it dosnt work, well need to try ndiswrapper

sam

Inorder of how you gave me this is what i got.

> 
sudo aptitude purge b43-fwcutter
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Initializing package states... Done 
Writing extended state information... Done 
Building tag database... Done             
Couldn't find any package whose name or description matched "b43-fwcutter" 
Couldn't find any package whose name or description matched "b43-fwcutter" 
No packages will be installed, upgraded, or removed. 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B of archives. After unpacking 0B will be used. 
Writing extended state information... Done 
Reading package lists... Done             
Building dependency tree       
Reading state information... Done 
Reading extended state information      
Initializing package states... Done 


sudo aptitude update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US 
  Could not connect to 192.168.1.100:8080 (192.168.1.100). - connect (111 Connection refused) 


sudo aptitude install b43-fwcutter
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Reading extended state information      
Initializing package states... Done 
Building tag database... Done      
Couldn't find any package whose name or description matched "b43-fwcutter" 
Couldn't find any package whose name or description matched "b43-fwcutter" 
No packages will be installed, upgraded, or removed. 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B of archives. After unpacking 0B will be used. 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Reading extended state information      
Initializing package states... Done 
Building tag database... Done

---

### Post by sam_delta on 2008-05-25
well, you need internet connection to do this by using the commands i wrote in previous posts, if you really cant get a temporary connection to fix this,  follow the steps i wrote in the following link

follow the steps on post # 9 on
[http://ubuntuforums.org/showthread.php?t=766800](http://ubuntuforums.org/showthread.php?t=766800)

it should work, but if it dont, let me know, and ill direct you into how to install ndiswrapper
sam

---

### Post by upthelum on 2008-05-25
Try [_*this*_]("http://ubuntuforums.org/showthread.php?t=370108")

---

### Post by Linux_noob616 on 2008-05-25
Tried to install the buid-essential but got this

"Error: Dependency is not satisfiable: libc6-dev|libc-dev"

---

### Post by sam_delta on 2008-05-25
you using ubuntu 32 bits? or 64?

sam

---

### Post by Linux_noob616 on 2008-05-25
> **upthelum said:**
> Try [_*this*_]("http://ubuntuforums.org/showthread.php?t=370108")

this is what i got
>  00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
        Subsystem: Dell Unknown device 01c9 
        Flags: bus master, fast devsel, latency 0 
        Capabilities: <access denied> 

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller]) 
        Subsystem: Dell Unknown device 01c9 
        Flags: bus master, fast devsel, latency 0, IRQ 16 
        Memory at dff00000 (32-bit, non-prefetchable) [size=512K] 
        I/O ports at eff8 [size=8] 
        Memory at c0000000 (32-bit, prefetchable) [size=256M] 
        Memory at dfec0000 (32-bit, non-prefetchable) [size=256K] 
        Capabilities: <access denied> 

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
        Subsystem: Dell Unknown device 01c9 
        Flags: bus master, fast devsel, latency 0 
        Memory at dff80000 (32-bit, non-prefetchable) [size=512K] 
        Capabilities: <access denied> 

And Sam, it's a 32 Bit version.

---

### Post by sam_delta on 2008-05-25
try installing build essential from the cd

Insert the CD into the drive and open a terminal, Applications -> Accessories -> Terminal, and type

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential

sam

---

### Post by Linux_noob616 on 2008-05-25
> **sam_delta said:**
> try installing build essential from the cd

Insert the CD into the drive and open a terminal, Applications -> Accessories -> Terminal, and type

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential

sam

Failed at the get update

---

### Post by sam_delta on 2008-05-25
yeah, it will fail cuz it wont be able to update from the internet, but there should be some lines where it succeed (when it updates from the cd)

try the next line, and tell us how it goes

sam

---

### Post by Linux_noob616 on 2008-05-25
Okay, i got it installed. follow the steps in the post right?

on the post that you sent me to, it can't find the "cd desktop"

---

### Post by sam_delta on 2008-05-25
"cd Desktop", its case sensitive,  "D"

sam

---

### Post by Linux_noob616 on 2008-05-25
tells me "Failed to create output directory: Permission denied" on the step before restart

---

### Post by sam_delta on 2008-05-25
type "sudo" before the command

sam

---

### Post by Linux_noob616 on 2008-05-25
Okay got it and the driver. But i have roaming set up and i'm still not getting signal. any help please?

(yes i know i'm a noob =/)

---

### Post by Linux_noob616 on 2008-05-25
Okay i got it set up and it says i'm connected. but it says when i load a page "proxy server refused connect" and then asks for my WEP key again. and when i put it in i get the same issue over and over.

---

### Post by sam_delta on 2008-05-25
.





EDIT
STOP DONT TRY THIS, i didnt read your last post until i finished typing this
lets try to fix your problem, dont try this post yet








well, last i can recomend to you is installing ndiswrapper., so here we go 

procedure taken from [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
(made necesary modifications so you can make it without an internet connection on your ubuntu pc)

Step 1 (run in terminal)

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
download and install ndiswrapper utilis from
[http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download)

Step 2

at this step, you need to download the WINDOWS wireless drivers (*.inf and *.sys files) for your specific card, you can usually find those at your manufacturer website
Paste those files into your desktop

Step 3

```
cd Desktop
```
```
sudo ndiswrapper -i driver.inf
``` WHERE "driver.inf" is the name of the windows wireless driver you downloaded and placed on the desktop

to make sure they installed correctly type
```
ndiswrapper -l
``` something like "driver.inf installed --- device presesnt" should appear

Step 4

we set up everything by typing
```
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Step 5

we remove b43-fwcutter we previously installed
```
sudo aptitude remove b43-fwcutter
```

Step 6

we make a script to Auto-set up the connection at each startup
```
sudo gedit /etc/init.d/wirelessfix.sh
```
a empty text file will open, paste the following into the file and save it

[text]#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44[/text]

save the file

and make it to run at startup with
```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
sudo update-rc.d wirelessfix.sh defaults
```

restart and it should work

sam

---

### Post by sam_delta on 2008-05-25
try using another internet application and see if it works,

---

### Post by Linux_noob616 on 2008-05-25
> **sam_delta said:**
> try using another internet application and see if it works,

Tried update. didn't work either =/

Also do i still do the above?

Edit: Didn't read your post. until just now. alright i wont.

---

### Post by Linux_noob616 on 2008-05-25
okay i got it to stay connected (forgot i used HEX and not a personal passphrase haha....) But still nothin.

---

### Post by sam_delta on 2008-05-25
could you please post here the output of ```
 iwconfig
``` while connected please

sam

---

### Post by Linux_noob616 on 2008-05-25
Here you go.

> lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:"NetworkName"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:6A:46:35   
          Bit Rate=2 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=76/100  Signal level=-37 dBm  Noise level=-72 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

---

### Post by sam_delta on 2008-05-25
alright, that sounds good, you got a connection, now, i think that the problem its that somehow your computer are trying to connect trough a proxy server which seems unavailable, let me do some research on how to disable proxy. im in xubuntu right now, so i cant play with the settings myself right now. ill get my hands into ubuntu in some minutes to play a bit with the settings and see what i can find about proxy servers.

anyone else can get a hand on this please?

thx
sam

---

### Post by Linux_noob616 on 2008-05-25
Alright, and thanks a bunch man. I know last thing you wanna do is help an idiot like me all day. But it's really a great help to me.

---

### Post by sam_delta on 2008-05-25
no worries, i like to help people like you, and thats why im here. :)
specially helping people enjoy ubuntu as much as i do
i was once in your possition seeking for help. and i found it here.

ill get back if i find something, 

any1 else that know about this "proxy error", please post
sam

---

### Post by Linux_noob616 on 2008-05-25
> **sam_delta said:**
> no worries, i like to help people like you, and thats why im here. :)
specially helping people enjoy ubuntu as much as i do
i was once in your possition seeking for help. and i found it here.

ill get back if i find something, 

any1 else that know about this "proxy error", please post
sam

It stopped saying "proxy error" and is now saying "Network Error". after it tries to load for about 5 minutes.

---

### Post by sam_delta on 2008-05-25
thats strange, have you tryied connecting without any encryption method?

sam

---

### Post by Linux_noob616 on 2008-05-25
> **sam_delta said:**
> thats strange, have you tryied connecting without any encryption method?

sam

Nope, if i turn off the encryption people can connect to me =/

---

### Post by sam_delta on 2008-05-25
yeah, but can you try turning it off really fast, just to see if the problem is encryption-related or if theres other problem

sam

---

### Post by Linux_noob616 on 2008-05-25
Okay went into my linksys settings and disabled it, still nothing. about to refreash and see if it does anything.

Edit: Didn't let me connect still

---

### Post by sam_delta on 2008-05-25
try installing another network manager such as wifi-radar
[http://mirrors.cs.wmich.edu/ubuntu/pool/universe/w/wifi-radar/wifi-radar_1.9.7-0ubuntu4_all.deb](http://mirrors.cs.wmich.edu/ubuntu/pool/universe/w/wifi-radar/wifi-radar_1.9.7-0ubuntu4_all.deb)

sry this is taking too long
sam

---

### Post by Linux_noob616 on 2008-05-25
Okay i installed it, does it just work now?

Okay i installed it and i don't know if i do anything after.
Still nothing though.

---

### Post by sam_delta on 2008-05-25
nope, open it, it should appear somewhere applications>network or internet

its a network manager

you might need to close gnome-network manager

sam

---

### Post by Linux_noob616 on 2008-05-25
Found the issue man, i feel so stupid, i turned on Manual proxy settings... turned it off just now and it works.

I'm sooo sorry man.

But thanks for your help (the networking card help was all needed cause it didn't work until then)

---

### Post by sam_delta on 2008-05-25
alright man, dont worry, those things happen to everyone.

im so glad you got your wireless working
and please, enjoy ubuntu :PP
anything you need, ill be around
sam

---

