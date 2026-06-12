---
title: "not able to connect with my linksys wireless wrh52g router"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by Rockstarever on 2012-12-17
hello guises there, 
i am having a lenovo laptop booted with ubuntu 12.04 and have a router cisco linksys wireless G home router whr54g with the access terminal at 192.168.1.1 
the problem is i am not able to connect to it even after manually entering the settings i.e. 


eth0      Link encap:Ethernet  HWaddr 00:1b:38:99:fe:05  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe99:fe05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57 errors:150 dropped:0 overruns:0 frame:0
          TX packets:1143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5222 (5.2 KB)  TX bytes:112149 (112.1 KB)
          Interrupt:21 Base address:0x3000


when i configure this in windows it was working and i was able to open the user access terminal in browser at 192.168.1.1 and able to enter the password and login but i am not able to access that terminal in ubuntu please help me with it i am very needy here. one more thing i am not going to use it to connect it to internet but want to share my internet access with it as i am connecting with my wireless usb dogle. have i done any thing wrong ? also this problem is faced by many ubuntu users face this same problem so may this also help them.

---

### Post by Mark Phelps on 2012-12-17
Sorry ... I'm having difficult understanding what is going wrong ...

Your PC  IP address appears to be on the same subnet (192.168.1.xxx) as the router, so you should be able to open a BROWSER (Not a terminal) and enter 192.168.1.1 in the address area -- and have that open a web page that will allow you to access the router.

IF that prompts for a userid and password, you will have to provide that to gain access to the router.

As to sharing internet access FROM the USB dongle with the router, I have no idea how you can do that -- unless what you really mean is gaining access to the router USING the USB dongle.

---

### Post by s1baker on 2012-12-17
if you haven't reset your router, you show be able in ubuntu bring up your browser and enter 192.168.1.1 and enter your password to get into your router settings. ( your password to get into your router to do administration, not the long password that is in your router that the router and the dongle use to talk encrypted to each other )


That said, have you also edited your network connection in Ubuntu and set the password to match your password on your router? ( the long password or password that the router and dongle use to talk to each other, not the password that you need to enter after going to 192.168.1.1 to do administration on your router )

---

### Post by s1baker on 2012-12-17
also~ make sure that the type of encryption that is set in your router ( probably WPA2 ) is also set in your ubuntu network connection.
ie.. in ubuntu, go to network connections. select wireless, highlight your connection and select edit, select wireless security and make sure it is set to "WPA & WPA2 PERSONAL". Also set your password here that matches you password on your router.

---

### Post by Rockstarever on 2012-12-18
i have already reset router once so i really dont know whats wrong is it problem in ubuntu or the router does not supports the linux. but the main fact is, router is still working on windows machine. so should i close this topic?

---

### Post by steeldriver on 2012-12-18
The only possible way I can think that "the router does not support Linux" to the extent that you can't access the router's web interface from a browser even though it has allowed you to connect and given you an IP address is that the router is asking for login credentials via a popup window and your browser is configured to block popups...?

---

### Post by Rockstarever on 2012-12-18
yes you are right my browser is set to pop up block. my thanks i think it just solved my problem. good logic buddy. thanks.

---

### Post by steeldriver on 2012-12-18
ok glad we were able to puzzle it out ;)

---

### Post by Rockstarever on 2012-12-18
got to put out an new habit not to freak out at any case what ever happens. because there is always a way to solve it out. ;) thanks again. :D

---

