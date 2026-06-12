---
title: "vlc and totem lag"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by spearo on 2008-08-06
ok this i have come across similar threads but nun of their solutions have fixed my problem. When watching avi's either through totem or vlc is it slightly laggy. its not terrible...but it seems a little gerky and gets irritating after a while.

i have a dual 1.4 ghz cpu, i have tried all the various encoding methods vlc offers that i have read off other threads in search of finding a solution to my problem.I have compiz turned off. 

I am failing to see what the problem is. Does anyone have a similar problem???

any help would be greatly appreciated.

kind regards
liam

---

### Post by Blutack on 2008-08-06
Are you using Compiz (fancy fading menus and stuff)?

---

### Post by spearo on 2008-08-06
nope...no compiz...or beryl.

---

### Post by Blutack on 2008-08-06
Hmm, do you know what graphics card do you have?
I had a similar issue with some SIS motherboard thing.

---

### Post by spearo on 2008-08-06
hmmm, not sure on the exact model of the graphics card. I know its an ATI. when i type in lspci it gives me info like this:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE


im not sure if that will be much help?? the laptop is a dell Inspiron 1501.

---

### Post by Blutack on 2008-08-06
Do you know if you have installed the Restricted Drivers?
Go System --> Administration --> Hardware Drivers and see if your card is there and ticked.

---

### Post by spearo on 2008-08-06
yes there is ATI accelerated graphics driver there and its been ticked. :S

---

### Post by rashwan on 2009-07-21
i have exactly the same issue i believe its due to compiz
unless you dont use it
i tried to killall compiz automatically the dock disappeared as well as the window borders
then tried to play the lagging movie it worked pretty well
any suggests ?

---

