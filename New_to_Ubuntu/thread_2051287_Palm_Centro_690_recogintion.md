---
title: "Palm Centro 690 recogintion"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by Scott B ME on 2012-09-01
I just loaded Ubuntu 12.04 on to my desktop and the only way I can get internet is through my Palm cell tehered to the computer. How do I get this thing to connect?

---

### Post by gordintoronto on 2012-09-01
Please provide a lot more facts. How do you want to connect? Give us the brand and model of any devices, including your computer? The terminal command: lspci
might produce some useful facts.

---

### Post by Scott B ME on 2012-09-01
It is a Palm Centro 690 that I am trying to use to use as a modem to connect to the internet. I am using the teather and not a bluetooth.

---

### Post by Scott B ME on 2012-09-02
> **Scott B ME said:**
> It is a Palm Centro 690 that I am trying to use to use as a modem to connect to the internet. I am using the teather and not a bluetooth.
 
More information:
Computer is a Dell Dimension 4300
Phone is a Palm Centro 690 
I ran 2 commands:
lsusb:
Bus 001 Device 004: ID 0830:0061 Palm, Inc. Lifedrive/ Treo 650/850 / Centro
 
usb-devices:
T: Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=   4 Spd=12 MxCh=0
D: Ver 1.10 Cls=00(>ifc) Sub=00 Prot=00 Mxps=16 #Cfgs=   1
P: Vendor=0830 ProdID=0061 Rev=02.00
S: Manfacturer=Palm, Inc.
S: Product=Palm Handheld
S: SerialNumber=50325639303446394D30
C: #Ifs= 1 Cfg#= 1 Atr=c0 Mxpwr=500mA
I: IF#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=visor
 
From this it appears that Ubuntu does recognise My Palm... So now what is missing for getting it to connect. :D

---

### Post by Scott B ME on 2012-09-02
Info from lspci:
00:1f.2 USB controller Intel 82801BA/BAM controller #1
00:1f.4 USB controller Intel 82801BA/BAM controller #1
 
I also show a communications controller for a 56K Conexant modem and an ethernet controller for a compatable 10/100 Ethernet. 
 
If there are any other commands I should run please let me know. This is my first time using Linux

---

### Post by gordintoronto on 2012-09-02
This is for a different Palm phone, but it might point you in the right direction:
[http://palmpre-hacks.com/palm-pre-hacks/how-to-tether-your-palm-pre-as-a-usb-modem/](http://palmpre-hacks.com/palm-pre-hacks/how-to-tether-your-palm-pre-as-a-usb-modem/)

I also found this suggestion:
"Configure the Centro. Press the Applications button until all applications are displayed. Select Preferences. In the Communication field, tap Connection and select Standard Modem. Finally, press Done. This sets up the Centro to be used as a wireless Internet source for a computer."

It was on this page:
[http://www.ehow.com/how_6247217_use-centro-wireless-internet-source.html](http://www.ehow.com/how_6247217_use-centro-wireless-internet-source.html)

---

### Post by Scott B ME on 2012-09-03
> **gordintoronto said:**
> This is for a different Palm phone, but it might point you in the right direction:
[http://palmpre-hacks.com/palm-pre-hacks/how-to-tether-your-palm-pre-as-a-usb-modem/](http://palmpre-hacks.com/palm-pre-hacks/how-to-tether-your-palm-pre-as-a-usb-modem/)
 
I also found this suggestion:
"Configure the Centro. Press the Applications button until all applications are displayed. Select Preferences. In the Communication field, tap Connection and select Standard Modem. Finally, press Done. This sets up the Centro to be used as a wireless Internet source for a computer."
 
It was on this page:
[http://www.ehow.com/how_6247217_use-centro-wireless-internet-source.html](http://www.ehow.com/how_6247217_use-centro-wireless-internet-source.html)
 
Thanks but that did not work. However, it did point me to download jpilot for linux. It says I shoud be able to connect my smartphone with this. However, I did downlaod this to a USB drive but I cannot figure out how to load this. I used the Ubuntu software center typed in jpilot. I see the file with a penguin next to the name but it does not give me the box on the right side to allow me to load it.... How do i get this accomplished?

---

### Post by gordintoronto on 2012-09-03
What you downloaded from the web site was probably source code. If at all possible, use the Software Center.

When I searched for jpilot, it appeared. When I clicked on it, the "install" button appeared.

---

