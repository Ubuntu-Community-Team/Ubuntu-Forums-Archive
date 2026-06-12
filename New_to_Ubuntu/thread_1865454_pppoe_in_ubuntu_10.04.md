---
title: "pppoe in ubuntu 10.04"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by angelgog on 2011-10-20
hi there ...
my friend has installed ubuntu 10.04 & cannot connect to the internet
he has broadband connection (pppoe) , in windows it is easy but when he shifted to ubuntu we cannot connect?
can any body help us please?

---

### Post by Karlchen on 2011-10-20
Hello, angelgog.

The easiest way of configuring a broadband connection, cable-bound or WLAN, should be by using System=> Settings => Network Connections.
What you need to configure there depends on hwo the computer is connected to the internet:
+ Is it using a WLAN connection to a router and the router establishes the connection to the ISP? (Wireless Network) 
+ It is using a cable bound connection to a router and the router establishes the connection to the ISP? (Wired Network)
+ It is using a cable bound connection to a "stupid" DSL modem and the computer has got to establish the conneciton to the ISP (DSL Connection)

Kind regards,
Karl

---

### Post by angelgog on 2011-10-20
thanx , i tried to configure it , followed the instruction in the manual of ubuntu but no result
i used the terminal (pppoeconf) & installed the user name & password & followed the step & no results
& add to it the network shortcut on the upper pannel on the rt side dissappeared
i am lost & despert ...
i dont know what to do 
 
in windows i have broadband connection ... click on it ... enter username & password ... get connected
 
please if you can help me & give me the detailed steps of connecting to broadband pppoe & if there is more than a way i will be very grateful 
 
thanx again for your help

---

### Post by Karlchen on 2011-10-20
Hello, angelgog.

I am not sure that I can give you a step by step instruction without knowing the details of your environment - which I do not really expect you to post publically.

Anyway, to start with:

You should decide whether you want to use **Network Manager** (you remember System => Settings => Network Connections) _or_ **pppoeconf**.
If you use the **pppoeconf Network Manager** will not touch (remove, modify) the entries which **pppoeconf **created. So it is either or.

When I configured my DSL conection at home on Karmic Koala, I opted for **pppoeconf**, after having tried **Network Manager** without success.

The computer was connected to the DSL modem by a network cable. All I knew about the DSL connection was the login name and the password which the ISP had given me.

Launched **sudo pppoeconf**. Accepted everything which **pppoeconf **suggested and only entered name and password. The connection started working fine and has been doing so ever after.

If this procedure does not work in your case, it may be worth determining first whether your network card is recognized and can be used.
You may e.g. inspect /var/log/messages or /var/log/syslog and search for entries related to your network card. 

Kind regards,
Karl

---

### Post by Karlchen on 2011-10-20
Hello, angelgog.

You have not told us how the machine in question connects to its ISP,
+ via WLAN to a router, and the router connects to the ISP
+ via cable to a router,  and the router connects to the ISP
+ via cable to a dumb DSL modem, so the computer needs to do the DSL login to the ISP

Therefore I will start explaining how to configure what may be the most common way of connecting a computer to the internet, in particular for notebooks:
The notebook has got a WLAN connection to a DSL router.
This router is connected to the DSL line. The router holds the logon name and the password with which you connect to your ISP.
The WLAN has been configured to require authentication and to use WPA2.

Here is what you do in Lucid Lynx:

[LIST=1]
[*]System => Settings => Network Connections
[*]Tab "Wireless Network" (2nd tab from the left) => Add
[*]Connection name: [name of your choice]
[*]Tick [X] Connect automatically
[*]Tab "Wireless Network"
[*]SSID: [name of your WLAN], e.g. [My_Secure_WLAN]
[*]Mode: Infrastructure
[*]BSSID: [leave empty]
[*]MAC address: [leave empty or fill in the MAC address of your WLAN adapter]
[*]MTU: [automatic]
[*]Tab "Security"
[*]Security: [WPA & WPA2 Personal]
[*]Password: [Password accepted by your router for incoming WLAN connections]
(strongly hope you have configured WPA2 Personal on your router)
[*]Tab "IP4 Settings"
[*][Automatic (DHCP)]
[*]Tab "IP6 Settings"
[*]Method: [Ignore] unless you know your router and your ISP can use IPV6
[*]Click the button [Apply]
[/LIST]
Provided all settings are correct Network Manager should now establish a connection to your router and soon you should see a little popup telling you that the connection to your wireless network named [Name_of_your_WLAN] has been established.

If this is the case, do not forget to enable your software firewall by running **sudo ufw enable** in a terminal window.

HTH,
Karl

---

### Post by dineshs on 2011-10-21
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

