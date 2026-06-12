---
title: "HSPA USB Modem(SmartBro) problem"
date: 2010-08-25
forum: Philippine Team
---

### Post by itagomo on 2010-08-25
HSPA USB Modem(SmartBro)

Gamit ko SmartBro USB Modem(HSPA).
Naka establish nako ng connection dati, tapos na-update ko pa un Update Manager.
First and only (until now) established connection ko pa lang yun.
Dati kasi ayaw magdetect as modem un USBModem, kaya gumamit ako ng usb_modeswitch.
Ininstall ko yun and entered the code to switch usb to modem, tapos nirestart ko ata at naka connect nako.
Pero dahil umabot ako ng madaling araw, natulog muna si pogi (ako).
Kinahapunan of the next day, ayaw mag connect. Try lang ako ng try, pero ayaw.
Bumalik ako sa WinXP. Pedeng pede.
Pero ayaw talaga maka establish ng connection sa Ubuntu 10.04.
Huhu.
Gagawa sana ako dito sa forum ng 'tutorial on how to detect USBModem as Modem in Ubuntu 10.04" for people who has problems connecting USBModems, pero di nako makaconnect eh.
Enge Help sa'nyo. Pls.

---

### Post by aljoriz on 2010-08-30
Hope your smartbro dongle is not WM660 .. There are reports that model does not work well with ubuntu 10.4, I am not sure about 10.4.1

---

### Post by Arnold Martin on 2010-09-01
> **itagomo said:**
> HSPA USB Modem(SmartBro)

Gamit ko SmartBro USB Modem(HSPA).
Naka establish nako ng connection dati, tapos na-update ko pa un Update Manager.
First and only (until now) established connection ko pa lang yun.
Dati kasi ayaw magdetect as modem un USBModem, kaya gumamit ako ng usb_modeswitch.
Ininstall ko yun and entered the code to switch usb to modem, tapos nirestart ko ata at naka connect nako.
Pero dahil umabot ako ng madaling araw, natulog muna si pogi (ako).
Kinahapunan of the next day, ayaw mag connect. Try lang ako ng try, pero ayaw.
Bumalik ako sa WinXP. Pedeng pede.
Pero ayaw talaga maka establish ng connection sa Ubuntu 10.04.
Huhu.
Gagawa sana ako dito sa forum ng 'tutorial on how to detect USBModem as Modem in Ubuntu 10.04" for people who has problems connecting USBModems, pero di nako makaconnect eh.
Enge Help sa'nyo. Pls.

Install wvdial then run it as root, ex. sudo bash, your password then type wvdial hsdpa in the terminal as root. Before that, put this into your wvdial.conf;

[Dialer Defaults] 
Phone = *99# 
Username = your login name 
Password = your login password 
Stupid Mode = 1 
Dial Command = ATDT 
 
[Dialer hsdpa] 
Modem = /dev/ttyUSB2 
Baud = 115200 
Init2 = ATZ 
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ISDN = 0 
Modem Type = Analog Modem

You might want to change the /dev/ttyUSB2 to /dev/ttyUSB0 or something. That's it! And you might also want to try SuperOS. It is cool.

---

### Post by itagomo on 2010-09-04
ah teka, tanong ko, pano ba malaman kun ttyUSB0 or something yun modem?
saka kakabasa ko lang sa superOS sa wiki, bago lang yun noh..

eto yun lumabas sa Terminal after entering 'wvdial hsdpa':

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

help pa ulit. tnx

---

### Post by Arnold Martin on 2010-09-09
You just simply guess if your modem is /dev/ttyUSB0, /dev/ttyUSB1 and so on, one funny trick before you type wvdial hsdpa as root in the terminal is that the LED light should be green, so you have to switch it to a '3G only' on the network settings of a microsoft windows system if your modem is ZTE MF627 like mine.

---

### Post by benlita on 2010-09-09
baka wala ka ng load?

---

### Post by itagomo on 2012-05-06
ang luma ng thread na to .. pero sagot dito ay usbmode switch .. search nio nalang ..

---

