---
title: "need assistance with setting up dialup on a computer that cannot access internet atm"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by jcheung1 on 2011-10-09
i am very new to this, so please bear with me.
OS version: ubuntu 10.10
GNOME version: 2.32.0

hardware:
[SIZE="1"]00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2) 
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2) 
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) 
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2) 
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3) 
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3) 
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3) 
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) 
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) 
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) 
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) 
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) 
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) 
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2) 
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3) 
01:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2) 
02:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2) 
02:01.0 PCI bridge: nVidia Corporation Device 05bf (rev a2) 
02:02.0 PCI bridge: nVidia Corporation Device 05bf (rev a2) 
02:03.0 PCI bridge: nVidia Corporation Device 05bf (rev a2) 
03:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2) 
03:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1) 
07:06.0 Communication controller: Agere Systems Lucent V.92 Data/Fax Modem 
07:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)[/SIZE]

i have tried doing this on my own, but i keep hitting roadblocks.
i keep seeing references to system > administration > network, but i do not have that option there...
when i do not see that reference, and i try to download something or another and install it by importing it on a USB flash drive, i get dependency issues.
the number i need to dial is 12123592000, server IP is 216.194.31.245
i'm nearing the end of my rope, any assistance would be much appreciated.

---

### Post by roger_1960 on 2011-10-09
Hi

I tried for months with this and finally bought a USRobotics 5637 external USB dial up modem.  I use it with gnome-ppp (dialer software from software center) and had to configure permissions as given below:

System settings
then
Users & groups
then
Advanced settings
then authenticate
User priviledges tab
Then tick "use modems" and "connect to internet using modem"

I really tried everything with the same Lucent type of built in winmodem, but its not worth the hassle for the sake of about £20 from Amazon.

---

### Post by jcheung1 on 2011-10-09
i'm sorry, you lost me :(
hard to access software center without an existing internet connection... i lost my broadband a few months ago.

please explain everything in a manner that a person with an IQ of 50 could understand?

---

### Post by roger_1960 on 2011-10-09
Hi again

You can download the gnomeppp.deb file from he following site:

[http://packages.ubuntu.com/hardy/i386/gnome-ppp/download](http://packages.ubuntu.com/hardy/i386/gnome-ppp/download)  (it is the same file for ubuntu 10.10)

You need to copy the file to your desktop (or any folder) and double click it.  It should self install.  I assume you must have internet access from somewhere otherwise you would not be posting here!

The modem I purchased works well, but whatever make/model you get must be a true external modem, with all the electronics in the external box, and NOT a winmodem (winmodems are designed to work with windows and although some can be made to work, many cannot)

The instructions for setting up permissions can be done without gnomeppp or a modem

System settings - menu item
then
Users & groups - within system settings
then
Advanced settings - a button in the users and groups window
then authenticate - enter your password
User priviledges tab - select this tab
Then tick "use modems" and "connect to internet using modem" - tick the boxes - if in doubt, tick them all!

Hope this helps - I'm out for a while now, I'll check any response in a few hours

Roger

---

### Post by jcheung1 on 2011-10-09
oh, i have to get a *bleep* external modem? just gets better and better....
you sure there's no way that my Agere Systems Lucent V.92 Data/Fax Modem chipset 11c1:0620 cannot be forced to work with ubuntu 10.10? (on second thought, will it work with any of the ubuntu versions?


P.S. i connected to this site telepathically :lolflag:
[color=white]not really[/color].

---

### Post by gandaran on 2011-10-09
> **jcheung1 said:**
> oh, i have to get a *bleep* external modem? just gets better and better....
you sure there's no way that my Agere Systems Lucent V.92 Data/Fax Modem chipset 11c1:0620 cannot be forced to work with ubuntu 10.10? (on second thought, will it work with any of the ubuntu versions?


P.S. i connected to this site telepathically :lolflag:
[color=white]not really[/color].
yes you can use the modem but you have to install drivers, ubuntu doesn't support any winmodem out of the box.
download the scanmodem tool run it then contact the developer for driver.
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by roger_1960 on 2011-10-09
Hi again

Yes, what gandaran is true, however I went down this path with a Lucent winmodem and eventually got nowhere. Its so much easier to use an external NON winmodem that I recommend thats what you do.

Roger

---

### Post by grahammechanical on 2011-10-09
I am not disputing what others have said about having difficulty with winmodems. The device, like Windows GDI printers, lacks many of the electronic components (cheaper that way) that Linix is use to communicating with in a modem. Windows does most of the work with these devices.

What I suggest is to open Synaptic Package Manager and search for pppconfig and see if it is installed. I think that it is installed as standard.

It is a text menu based utility that is run in the terminal and it will set up a modem connection. I used to use it before I got broadband.

In the terminal you type sudo pppconfig. I do not know if this will make any difference but it may solve the problem of downloading Gnome-PPP without an Internet connection.

> P.S. i connected to this site telepathically 

So, that's why I have an headache!

Regards.

---

### Post by roger_1960 on 2011-10-10
Hi

I know it goes against the grain to buy a modem but remember that it will work with almost any computer with very little setting up.

grahammechanical is right, pppconfig is in the standard installation (I'd forgotten about it).  You need to run it with root privileges - cut and paste the following in a terminal:

> sudo pppconfig

(You will still need to do the system settings set up I gave above)

Depending where you are in the world, ebay may be good for a modem, or often a local computer shop will have them.  Do make sure any modem you buy is not a winmodem (some external modems are!)

Roger

---

### Post by lkraemer on 2011-10-11
jcheung1,
Why don't you go to [www.linmodems.org](www.linmodems.org) and download their script, then run it
to determine what Marvin and the folks at linmodems.org need to assist you.

Send Marvin & those folks your information in PLAIN TEXT, so they can
advise you.

You can also search through their archives, looking for others that have used the same modem as yours, and follow their exploits.

Here is a link to to an old Guide.  
[http://ubuntuforums.org/showthread.php?t=1654588&highlight=sm56](http://ubuntuforums.org/showthread.php?t=1654588&highlight=sm56)
Posting #3

lk

---

