---
title: "How to dial in to internet under ubuntu"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by dgg9879 on 2008-09-28
I just installed ubuntu today. Complete newbie. I just want to surf the net this way to avoid problems with spyware etc. But my dial up into the internet icon is on my windows desktop. I can't work out how to dial into the internet while in ubuntu operating system.

---

### Post by didiercool on 2008-09-28
Go to System, then Administration, and click on Network (not network tools).  From there, click on 'Modem connection,' highlighting it, and then properties on the side.  That will bring up the settings options for you dialup.  Just fill that in and enable it.  That should get you started!

~peace

---

### Post by jimmy the saint on 2008-09-28
That assumes you have a modem that will work with linux.  Most modems these days are winmodems which mean that they rely on windows to do most of the work.  It is possible to set up some of them in linux, but given the level of pain that smashing your head against the wall is likely to produce, just buying a serial modem is easier.

---

### Post by starcannon on 2008-09-28
Something like this one:
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=300257464712&ssPageName=MERC_VI_RCRX_Pr4_PcY_BIN_Stores_IT&refitem=290221281867&itemcount=4&refwidgetloc=active_view_item&usedrule1=CrossSell_LogicX&refwidgettype=cross_promot_widget&_trksid=p284.m184&_trkparms=algo%3DCRX%26its%3DS%252BI%252BSS%26itu%3DISS%252BUCI%252BSI%26otn%3D4](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=300257464712&ssPageName=MERC_VI_RCRX_Pr4_PcY_BIN_Stores_IT&refitem=290221281867&itemcount=4&refwidgetloc=active_view_item&usedrule1=CrossSell_LogicX&refwidgettype=cross_promot_widget&_trksid=p284.m184&_trkparms=algo%3DCRX%26its%3DS%252BI%252BSS%26itu%3DISS%252BUCI%252BSI%26otn%3D4)

There are others, that one will work, but any "hardware modem" should be fine, I like the old Zoltrix Rainbow 56k external modems alot, I keep one around for rare broadband outages.

---

### Post by jimmy the saint on 2008-09-28
Thanks starcannon.  I "hardware modem" was at the tip of my tongue (or fingers) but just wouldn't come out!  This is an important distinction.  I initially thought that all serial modems were hardware modems so I picked up a diamond something or other.  That was a mistake!  Apparently it is one of the only serial winmodems.

---

### Post by dgg9879 on 2008-09-28
I have DLink 200 modem. At least that's what it says. It's an old one. Will it work with Linux? It is ADSL. I need ADSL modem.

---

### Post by superprash2003 on 2008-09-28
hope this helps [http://prash-babu.blogspot.com/2008/06/how-to-configure-bridged-mode-in-linux.html](http://prash-babu.blogspot.com/2008/06/how-to-configure-bridged-mode-in-linux.html)

---

### Post by oilchangeguy on 2008-09-28
> **dgg9879 said:**
> I have DLink 200 modem. At least that's what it says. It's an old one. Will it work with Linux? It is ADSL. I need ADSL modem.

if you've got dsl, you do not have dial up. you should be able to get online just by clicking the firefox icon.

---

### Post by starcannon on 2008-09-29
Looks like its a USB DSL Modem, complete set of manuals, windows drivers, and firmwares available here: [http://www.dlink.com.au/tech/](http://www.dlink.com.au/tech/)

I have never used one of these units, and from looking at it am guessing it has no ethernet port, so USB is apparently the only way to connect it to your computer.

I have read a few success stories on that modem, but it does look like it may be rather involved. I would try setting up ppoe first though, just in case the modem works fine with Ubuntu and simply needs to pass along the username and password.

Assuming your connecting using PPPOE:
From a terminal {Applications>Accessories>Terminal} enter:
```
pppoeconf
```
You will need your user name and password from your ISP, 
Answer Yes to all the questions in the wizard, put in your ISP username and password in the fields when asked, and if your modem is a "just works you'll be up and running. If not I'll post some links to help get you started on getting that modem to work.

GL

---

### Post by J_dillinger on 2008-10-03
I was wandering if someone might help me with a similar question.  I have a dell laptop and have the drivers installed, but I am receiving intermittent connectivity.  When the modem is connected I can see my IP Address with ifconfig and ping the ISP, but I can not ping other web sites or open websites with fire fox.  I am thinking that I either have a problem with DNS or a firewall I have not found yet is prohibiting the connection.  The internet connection works fine with wireless of connecting with my NIC.  Could anyone help out with this final hurdle so I can finally connect with my modem. 

The DNS address I have entered was the one I copied out of the ipconfig from windows xp connecting to the same ISP.

---

### Post by J_dillinger on 2008-10-03
Here is the output from wvdial and ifconfig

206.190.171.99 - google IP Address

E:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT*70, 218 0079
--> Waiting for carrier.
ATDT*70, 218 0079
CONNECT 57600 
--> Carrier detected.  Waiting for prompt.
Level 3 Comm nas20.phx1 UQKT2
Username:/login:/Login:
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: ***Login Name***
Password: 
--> Looks like a password prompt.
--> Sending: (password)
    Entering PPP Session.
    IP address is 4.240.57.22
    MTU is 1524.
--> Looks like a welcome message.
--> Starting pppd at Fri Oct  3 17:01:51 2008
--> Pid of pppd: 6812
--> Using interface ppp0
--> pppd: ï¿½_ï¿½ï¿½Ð¨[06][08]ï¿½ï¿½[06][08]
--> pppd: ï¿½_ï¿½ï¿½Ð¨[06][08]ï¿½ï¿½[06][08]
--> pppd: ï¿½_ï¿½ï¿½Ð¨[06][08]ï¿½ï¿½[06][08]
--> pppd: ï¿½_ï¿½ï¿½Ð¨[06][08]ï¿½ï¿½[06][08]
--> pppd: ï¿½_ï¿½ï¿½Ð¨[06][08]ï¿½ï¿½[06][08]
--> local  IP address 4.240.57.22
--> pppd: ï¿½_ï¿½ï¿½Ð¨[06][08]ï¿½ï¿½[06][08]
--> remote IP address 63.215.26.148
--> pppd: ï¿½_ï¿½ï¿½Ð¨[06][08]ï¿½ï¿½[06][08]
--> primary   DNS address 207.69.188.187
--> pppd: ï¿½_ï¿½ï¿½Ð¨[06][08]ï¿½ï¿½[06][08]
--> secondary DNS address 207.69.188.186
--> pppd: ï¿½_ï¿½ï¿½Ð¨[06][08]ï¿½ï¿½[06][08]




ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:17:dd:ae  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94684 (92.4 KB)  TX bytes:94684 (92.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:4.240.57.22  P-t-P:63.215.26.148  
Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2034 (1.9 KB)  TX bytes:87 (87.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:77:67:40  
          inet addr:192.168.1.100  Bcast:192.168.1.255  
Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe77:6740/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50266 (49.0 KB)  TX bytes:27797 (27.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 
00-13-02-77-67-40-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by AClark on 2008-10-03
Quote:
[ When the modem is connected I can see my IP Address with ifconfig and ping the ISP, but I can not ping other web sites or open websites with fire fox.] 

@J_dillinger

Quoting from:
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)
"If you connect successfully but your Internet applications do not function (eg. web pages do not load in Firefox), you might need to add replacedefaultroute as a new line in the pppd option file."

I had the exact same symptoms - I could ping the ISP but nothing else and Opera/Firefox acted like I was not connected.

I added replacedefaultroute as the last line in my /etc/ppp/options file and now my applications are connected and function normally.

---

