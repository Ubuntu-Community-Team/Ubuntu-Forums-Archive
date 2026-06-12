---
title: "How do my Ubuntu find my wifi-printer?"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by haralito on 2011-12-06
I converted my netbook from Vista to Ubuntu 11.10 and I am impressed over the improvement. 

However, now I can't find my Samsung ML-2525W wifi printer.
It's probably easier to just connect an USBcable to it, but I really would like to print wifi.

Since I'm all new to Ubuntu (Linux) I would be very happy if somebody could help where to look.
Thanks in advance :)

-Haralito

---

### Post by bluexrider on 2011-12-06
you will need the IP address of your wifi printer

1. Click on administration and add printer.
 2.  Fill in the name of the printer.
 3.  Under location, I type in the ip address of the server.
 4.  You can fill in a description, but you don't have to.
 5.  Click continue.
 

should do it

---

### Post by kurt18947 on 2011-12-06
> **bluexrider said:**
> you will need the IP address of your wifi printer

1. **Click on administration and add printer.**
 2.  Fill in the name of the printer.
 3.  Under location, I type in the ip address of the server.
 4.  You can fill in a description, but you don't have to.
 5.  Click continue.
 

should do it

Administration on 11.10? Wouldn't pressing the 'super'(windows) key then type 'printers' and go from there work better?  I use Gnome shell 99% of the time but that's how I remember Unity working presuming the O.P. is using Unity.

---

### Post by bluexrider on 2011-12-06
> **kurt18947 said:**
> Administration on 11.10? Wouldn't pressing the 'super'(windows) key then type 'printers' and go from there work better?  I use Gnome shell 99% of the time but that's how I remember Unity working presuming the O.P. is using Unity.

its an easy fix if the OP wants to get it going no matter

---

### Post by haralito on 2011-12-07
Thanks for suggestion so far, but I still haven't figured out how to solve this problem.

To start, I think it's wise to give you the specs of my equipment:

1. Internet modem
2. Wireless router
3. Desktop - Windows XP connected through cable to the router
4. Netbook - Ubuntu 11.10 conncted wireless to the router
5. Samsung ML 2525W wifi printer - connected via USB to the desktop 

I've tried following:

Installed Unified Driver and Printer Setting Utility. Then I added a printer pressing "Super" and then I get 3 options:
1. LPT#1
2. Enter URI 
3. Network printer. I suppose it's Network printer i should pick. Choosing Network printer I get the option "Host" where I typed the IP address for the printer. Is this where I am doing wrong? You guys said i should type in my network IP. In that case would that be the address for my router? And where do I find the address of the network?  It couldnt find anything with the IP of my printer.

Any suggestions of what I do next?


> **kurt18947 said:**
> Administration on 11.10? Wouldn't pressing the 'super'(windows) key then type 'printers' and go from there work better?  I use Gnome shell 99% of the time but that's how I remember Unity working presuming the O.P. is using Unity.

---

### Post by kurt18947 on 2011-12-07
I have a somewhat similar situation.  I find it far easier to make a network connection between the printer & router without going through another PC and it's USB cable. Of course your printer may work with more than one connection.  For instance, one Brother printer can have a USB connection **and** one network connection, either wired or wireless.  An advantage to having the printer connected to the router rather than a PC is that the attached P.C. doesn't need to be on to use the printer.  I don't have  Samsung, I have 2 Brother MFDs networked.  I assume the Samsung is somewhat similar.  If the printer is located such that a cable can be run from your router to the printer, that makes things a little simpler and IMO more reliable.  If not,  WiFi should work fine.

The first thing I did was find or set an I.P address on the printer.  If you're able to run a cable you shouldn't have to worry about this, just let DHCP do its thing.  If not, you'll need to tell the printer your wireless encryption, SSID & password. On my Brother printers, this is done via a keypad & screen.  I also assign a static I.P. address to the printer.  TIP:  To help remember the I.P. address, I use part of the model #. i.e. MFC-440's I.P would be 192.168.1.40.  More on this in a minute.  If you did everything right, you should get some indication that a wireless network connection is established.

For the next step I use Unity in 11.10.  For whatever reason the printer setup in Unity provides more options than does Gnome-shell at least for me.  I do superkey -> search for printing, left-click the printer icon then left-click 'add'.  Click the arrow by 'Network Printer', wait a few seconds and your Samsung should be listed.  If your printer is in the Foomatic database and I think many Samsungs are, it should find a suitable driver and  pretty much install itself.  Otherwise it may list available drivers or ask for a .ppd.  I'm not familiar with Samsung's install so I can't help there.

This next part is a personal preference and only applies to wireless connections for me.  I've not had issues with wired network connections.  I've had connectivity problems in the past with the default dns-sd connections.  I've started using a manual configuration that seems quite reliable.  I right-click the printer icon in the Printing-localhost window and select 'properties'.  In the device URI I type ```
[http://socket://xxx.xxx.xxx.xxx:9100]("http://socket//xxx.xxx.xxx.xxx:9100")
``` where xxx=I.P. address. That's the reason I assign printers static I.P. addresses;  if the printer's I.P. address were to change this wouldn't work.  You can change the printer driver if you find a better one from the same location.

I hope this makes sense, isn't too long and works for you.

---

### Post by Mark Phelps on 2011-12-07
I've found that CUPS in 11.10 is generally quite good at finding networked printers.  With previous Ubuntu versions, I had to manually configure the network addresses, but with 11.10, that's not needed now.

To do this, open a browser and enter "localhost:631" (without the quotation marks).  That will open CUPS.  Then use the Add menu option -- and see if the printer is listed.

---

### Post by haralito on 2011-12-07
I will thank you all for the help. It turned out that CUPS in my OS edition 11.10 did the nice work :) At first it didn't find the printer, but I found the printer on through the manufacters list that came up. Because of that I managed to make a fully install. But there were no contact. I tried to make a print, but no reaction. Then I decided to turn the printer off and on. All of the sudden it happened. It worked!!! Since the print was in cue, it came out automatically when my printer came online.
So thanks to you all for nice help.
I will definetely stick to Ubuntu 11.10. 
Especially because of the generousity of help from other Linux/Ubuntu-users.

Sincerely,
Haralito

---

### Post by bluexrider on 2011-12-07
> **haralito said:**
> I will thank you all for the help. It turned out that CUPS in my OS edition 11.10 did the nice work :) At first it didn't find the printer, but I found the printer on through the manufacters list that came up. Because of that I managed to make a fully install. But there were no contact. I tried to make a print, but no reaction. Then I decided to turn the printer off and on. All of the sudden it happened. It worked!!! Since the print was in cue, it came out automatically when my printer came online.
So thanks to you all for nice help.
I will definetely stick to Ubuntu 11.10. 
Especially because of the generousity of help from other Linux/Ubuntu-users.

Sincerely,
Haralito

thats what we're here for

---

### Post by kurt18947 on 2011-12-07
> **Mark Phelps said:**
> I've found that CUPS in 11.10 is generally quite good at finding networked printers.  With previous Ubuntu versions, I had to manually configure the network addresses, but with 11.10, that's not needed now.

........


Thanks Mark. I'll try that next time I do an install.  It'd make life simpler.

---

