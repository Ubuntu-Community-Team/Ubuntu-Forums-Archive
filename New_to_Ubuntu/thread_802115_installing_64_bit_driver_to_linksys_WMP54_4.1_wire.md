---
title: "installing 64 bit driver to linksys WMP54 4.1 wireless adaptor"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Happy-Cheese on 2008-05-21
I have downloaded an windows driver for my 64 bit ubuntu...
Then i got that DriverLoader program so U can install windows drivers to your Linux thing... :)

Then i try to install the driver BUT then it says:

-----------------------------------------------------------------------<
It seems that your device is either not present or not supported by the installed driver(s). Either:

1. Plug-in your device and click [Refresh] to retry, OR
2. Upload a new driver using the [Upload Windows Driver] button below.

If your device still does not appear, please look at the Kernel Messages for possible clues and check that no conflicting kernel modules are loaded.
-----------------------------------------------------------------------<

And ya im really sure that i got that wireless netcard...

Im sitting here with a 20 meter long cable to get on the internet :/ I neeed help!

---

### Post by Happy-Cheese on 2008-05-21
Cmon someone must know!!!

---

### Post by shifty_powers on 2008-05-21
first of all look here

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

this will give you some interesting info on your card.

plus have you tried ndiswrapper?

---

### Post by Happy-Cheese on 2008-05-21
What is ndsirapper?

And what does all that stuf means?

Chipset

Driver
	
Supports network install?
	
Supported in installed system?	

Works "out of the box" 

:) sorry

---

### Post by shifty_powers on 2008-05-21
heh ok....

just a quick quetion. have you actually tried to detect a wireless network?

plus what is the output of

```
lspci
```

when typed into a terminal? (applications>accessories>terminal)

---

### Post by Happy-Cheese on 2008-05-21
the output is:
happy-cheese@Happy-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IB (ICH9) 4 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
02:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
05:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
06:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI


No actually i havent try to connect a network... a cant find out of that too :/

---

### Post by shifty_powers on 2008-05-21
heh well that card/driver *SHOULD* just work. it's the same driver that i use ;) (albeit for a different card)

ok.

go back to the terminal and type:

```
sudo iwlist scan
```

and post the output ;)

---

### Post by shifty_powers on 2008-05-21
oh and which version of ubuntu are you using btw? and is there a special reason you picked the 64-bit version?

---

### Post by Happy-Cheese on 2008-05-21
Output:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Im Using the newest version downloaded it yesterday :)

no theres not a good reason that i downloaded the 64 Bit only that i newer tried to really use the 64 bit i can run :P

---

### Post by shifty_powers on 2008-05-21
is that definitely the entire output?

hmm...

ok, well tbh, i personally would recommend downloading the 32-bit version and using that.

tbh, don't take this the wrong way, but you seem quite new to ubuntu, and i just think that your life is going to be easier with 32-bit, than 64 ;) Also, you will not notice any real difference in speed between the two, and i have a suspicion that 32-bit 8.04 will play nicely with your card....

---

### Post by Happy-Cheese on 2008-05-21
Now i remember... it was Ubuntu 8.04

---

### Post by Happy-Cheese on 2008-05-21
Okay ill try installing 32 bit and then return to this forum in 2-3 hours :P 

So Long

---

### Post by shifty_powers on 2008-05-21
heh dude, tyr using the live-cd first.

always a good idea ;)

it will let you know if the wireles is going to work...

---

### Post by Happy-Cheese on 2008-05-21
From my Windows...

I have tow partitions :)
im nearly finish downloading it and it takes no time to install :D
And then i got it on a CD for later use :O

---

### Post by shifty_powers on 2008-05-21
heh, but the point of the livcd is that it will boot up a full version of ubuntu, trying to identify and run all of the drivers for your hardware. That way it will give you some idea of whether your wireless will work without installing.

don't forget, you need to right click on the network manager icon in the sys tray in the top right and either enable wireless/pick the netwrk you want to join...

---

### Post by Happy-Cheese on 2008-05-21
Now im back with 32 bit :)

i have installed the driver and all seems to be in order then i click on my wireless network and enter the password, then there goes a long time and then it just stops.. and still no wireless connection or error mesasge :(

Hope U can help me again :P

---

### Post by Happy-Cheese on 2008-05-21
PLeease someone i really need help

---

### Post by shifty_powers on 2008-05-21
heh, my aplogies, even i have to step away from the computer occassionally.

right. first of all could you repeat the lspci and uso iwlist scan commands from earlier and post the output...

---

