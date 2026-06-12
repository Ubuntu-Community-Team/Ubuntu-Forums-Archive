---
title: "no network adapter"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by hlekat on 2008-06-08
i have just installed 8.04 for the second time. the reason i made the reinstallation is the network adapter. i cannot access to the internet. i am trying to configure it manual but also nothing happens.

in network settings > location i think it should show my network adpater but it does not shows anything.

i also try to replace the lo device that is writen in the recourses file with eth0 eth1 eth2 but nothing.

in the hardware tesd it recognizes the network adapter: \attansic technology l2 rev a0.

in network tools > network devices eth0 and eth1 are not available although i can select them i cannot cofigure them : interface does not exist.

---

### Post by hlekat on 2008-06-08
i have also run sudo pppoenconf

i got the following message : 

Sorry , i scaned 1 interace, but the access concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be anoter running pppoe process whick controls the modem.

---

### Post by Unix_Slayer on 2008-06-08
> **hlekat said:**
> i have also run sudo pppoenconf

i got the following message : 

Sorry , i scaned 1 interace, but the access concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be anoter running pppoe process whick controls the modem.

Is this a wired, or wireless connection? Because eth0 would be the wired. I am trying to picture what your problem is.

---

### Post by hlekat on 2008-06-08
yes it is a wired connection.

in the same computer i have also intalled vista and i have no problem with the cables - internet.

---

### Post by Unix_Slayer on 2008-06-08
> **hlekat said:**
> yes it is a wired connection.

in the same computer i have also intalled vista and i have no problem with the cables - internet.

```
Fast Ethernet
	
L2
	PCI-Express Base 1.0a
10/100 Ethernet Controller with Integrated Transceiver 	
	PCI Express Base 1.0a compliant
	100/ 10 Mbps IEEE 802.3 compliant
	IEEE 802.3u Auto-Negotiation
	TWSI and SPI mode
	Single power supply 3.3V with on-chip Linear regulator
	 
Power
	
AT9173
	Bus Termination Regulator 	
	Support Both DDR I (1.25VTT) and DDR II (0.9VTT) Requirements
	SOP-8/PSOP-8 Packages
	High Accuracy Output Voltage at Full-Load
	Minimum External Components
```

So this would be your wired adapter.

---

### Post by hlekat on 2008-06-09
i don't know if it's my adapter. the netowork adapter is on board. 
any ideas how to fix it ?

---

### Post by hyper_ch on 2008-06-09
does it work in windows?

---

### Post by hlekat on 2008-06-09
yes it does.

---

### Post by Unix_Slayer on 2008-06-09
> **hlekat said:**
> yes it does.


If you can, go into windows and see what device it is. From the info you gave, I have no clue what kind of card it is.

---

### Post by hlekat on 2008-06-09
the adapter is integrated with the motherboard  

[http://www.asus.com/products.aspx?modelmenu=1&model=1771&l1=3&l2=11&l3=498&l4=0](http://www.asus.com/products.aspx?modelmenu=1&model=1771&l1=3&l2=11&l3=498&l4=0)

from windows : atheros l2 fast ethernet

---

### Post by Unix_Slayer on 2008-06-09
> **hlekat said:**
> the adapter is integrated with the motherboard  

[http://www.asus.com/products.aspx?modelmenu=1&model=1771&l1=3&l2=11&l3=498&l4=0](http://www.asus.com/products.aspx?modelmenu=1&model=1771&l1=3&l2=11&l3=498&l4=0)

from windows : atheros l2 fast ethernet


I'm looking at the board specifications. P5G-MX

This link. ===> [http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5G-MX]("http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5G-MX")

Go to Lan. At the bottom of the page of drivers for the Lan is the linux driver.

---

### Post by Unix_Slayer on 2008-06-09
You might have to use a specific lan manager. You might try to install wicd. I've had no luck with wicd, but most people do.

---

### Post by hlekat on 2008-06-10
because i am not familiar with driver installation in linux i will first try wicd.

---

