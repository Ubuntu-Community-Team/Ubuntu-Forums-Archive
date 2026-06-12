---
title: "Printing from Ubuntu to Orange Livebox"
date: 2007-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by dmfield on 2007-09-01
[I]A quick note:

[/I]> baza41 has [already posted ]("http://ubuntuforums.org/showthread.php?t=363781")one way of doing what i'm about to cover using the CUPS Web interface, The instructions are to do the same thing, using the Ubuntu Printer GUI Interface.  The live box is a device supplied by Orange when you sign u in the UK (and possibly elsewhere) for their broadband package. When i first got the box, i thought it was a bit of tat, something for the iPOD generation however, the more i use it, the more  I like it. The wireless does work with the device (covered on other posts if you are stuck) however this feature is a great one Wireless Printing. You can spend up to 60GBP+ to get a wireless print server, however the Livebox does it. And its quick and easy with Ubuntu. (I'm using 7.04) from the GUI follo these instructions.
[B]
Setup the Livebox[/B]

> Plug your USB Printer into the USB Port on the Live box> Log into the Web Interface for the Livebox (Usually [http://192.168.1.1](http://192.168.1.1)) > Enter the  "Access configuration pages" and enter your login ID and password> The first page you are taken to is the My Services page, if the Liveprinter option is **not **enabled click on Change, then on the next screen click on Enable*If the Live printer option **IS** enabled, then you don't need to enable it.*

To check and see if the device has been recognized, on the Menu Click on

> Configuration -> USB Host portThe printer should be listed under USB Peripherals, i got:[INDENT]> **Deskjet F300 series (HP)**
Vid: 1008
Pid: 21777
USB Version:  2.00
Revision:  1.00
Serial number: CN----------CK[/INDENT]If you have got this far, your ready to setup Ubuntu

**Setup Ubuntu**

In the Ubuntu Menu 

> System -> Administration -> Printing> Double Click on New PrinterLet the Reading Printer database do its stuff

_***Step 1 of 3: Printer Configuration ***_

> Printer Type = Network Printer> 
Choose TCP/Socket, HP Jetdirect, Raw Connection in the drop down menu > Host = 192.168.1.1(This is the IP Address of your Livebox, if you have a different IP for your Livebox (If you had to type something different in to get the Livebox Web Admin interface, type it in here, the default setting is 192.168.1.1)

> Port = 9100Click on Forward

_***Step 2 of 3: Pinter Driver***_

Choose the Manufacturer and Model of your Printer, for example, i chose HP as the Make and Deskjet F300, [INDENT][I]if your not sure, but have had the printer setup in Ubuntu before, then you would be best to check your previous printer settings

[/I][/INDENT]Click on forward

[U][I][B]Step 3 of 3: Printer Information

[/B][/I][/U]This information is how your printer will be show when you click print in applications, so enter a valid name I used F300 Live Printer

Once you have finished click on apply

**Set as Default**

If you want to make this your default printer, then In the printer window, which should still be open, simply:

> Right Click on the newly added printer> Select Make Default**Testing**

If you want to test that this works, then In the printers Window, which should now show your printer 

(as default if you followed the above instructions, with a green tick on it) 

> Right Click on the Printer Icon> Click on PropertiesWait for the properties box to appear (less than 10 seconds usually) 

> Click on Print Test PageIf everything went swimmingly, then you should hear th printer start to crank up, and print the Ubuntu Test page...

---

### Post by johnjones on 2007-10-19
is this possible using MacOS X (CUPS) or Windows (using IPP) ?

I have a orange livebox and a linux box does as my print server but it has to be on... and if it works from all 3 of my OS's that would be stunning !

also I belive that the orange livebox runs linux but I have no way of hacking into it at the moment....

thanks I really dont want to mess up my network until I would know this works and I know you must have a copy of the XP soemwhere since its on your profile...

awaiting your answer !

John

---

### Post by lenswipe on 2008-03-01
> **johnjones said:**
> is this possible using MacOS X (CUPS) or Windows (using IPP) ?

I have a orange livebox and a linux box does as my print server but it has to be on... and if it works from all 3 of my OS's that would be stunning !

also I belive that the orange livebox runs linux but I have no way of hacking into it at the moment....

thanks I really dont want to mess up my network until I would know this works and I know you must have a copy of the XP soemwhere since its on your profile...

awaiting your answer !

John


This does not mess up your network!!

It just adds a printer to it meaning you can print through your orange livebox. However i have an orange livebox 7920 but i dont get the thing about Live Printing....


Anyone got any ideas??


It has a USB port on it but not the live printing option!!!  :lolflag:

---

### Post by dmfield on 2008-03-01
How did you work out the model number of the livebox?

---

### Post by lenswipe on 2008-06-05
> **dmfield said:**
> How did you work out the model number of the livebox?

its in the SSID of my wireless and its also in the configuation pages under system information.

---

### Post by davcham9 on 2008-08-01
Hi

Thank you works great for me, ubuntu didn't have my printer driver (Brother HL2030) but using the HL2060 worked fine even quicker to send prinjobs then vista (no surprises there then)

---

### Post by mehtdosa11 on 2008-08-01
oh my god it works!!

thank you sooo much!! i was trying to get this to work in my old windows days thru tcp/ip.

according to the orange web-site, even they haven't got it working yet !!

many thanks again

steve

---

