---
title: "Ethernet port wifi port"
date: 2017-05-06
forum: New to Ubuntu
---

### Post by plymouth532 on 2017-05-06
Another newbie,
 I have an HP laptop and ubuntu 17.04 os. I have one device that uses an ethernet cable. I bought a bridge but when I connect bridge ethernet cable to the laptop, laptop set to wifi, and open browser and type in bridge address I get no internet connection to bridge. Is there a way to use both the wifi port and the ethernet port at the sam time? I keep getting the run around from sprint, bridge, and device manufacture. 

Thanks for any help I can get,
Ed

---

### Post by lammert-nijhof on 2017-05-07
You can use both ethernet and wifi at the same time, no problem I do it often. Start being more specific. What is the kind of device that uses the ethernet cable, what is the type and brand. What type of bridge did you buy, again type and brand. If your bridge is a real bridge and not a router or switch, the address it has, will be a mac address and not a tcp/ip address. You can't use mac addresses in a browser, so what do you type in? Where does your 'device' request a TCP-IP address or does it has a fixed TCP/IP address and what is it?

In the mean time try connecting your device to the wifi router with the ethernet cable and your laptop will connect through wifi to the same router. Both laptop and "device" will get a TCP/IP address from the wifi router. Find out what that 'device' TCP/IP address is and type that TCP/IP address in the browser. Forget for the moment about the bridge, it is probably useless. A TCP/IP address will look like e.g. 10.0.0.12 or 192.168.0.105 and the first three numbers of laptop and 'device' should be the same and only the fourth number should be different. A Mac or hardware address will look like 12:b0:23:f8:6c:77

---

### Post by christianc123 on 2017-05-26
[COLOR=#111111][FONT=Ubuntu][FONT=arial]If you're using NetworkManager, it should just work. That said, you will need to set specific settings for your wired connection.[/FONT][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][FONT=arial]Select your wired connection in the Connection Editor window for Network Manager (right click on the applet icon, then select Edit Connections). But bridge is a layer two device,its work with Mac address.Bridging occurs at the data link layer of the OSI model, which means the bridge cannot read IP addresses, but only the outermost hardware address of the packet. In our case the bridge can read the ethernet data which gives the hardware address of the destination address, not the IP address.[/FONT]

.[IMG]https://i.stack.imgur.com/L7j9v.png[/IMG]
[/FONT][/COLOR][FONT=arial][IMG]https://i.stack.imgur.com/ctcTX.png[/IMG][COLOR=#111111]


[/COLOR][/FONT][COLOR=#111111][FONT=Ubuntu][FONT=arial]You can then force the wired connection to not claim the default gateway (since NM would usually prefer wired over wireless), by checking the "Use this connection only for the resources on its network" checkbox.[/FONT][/FONT][/COLOR]
[FONT=arial]
[/FONT]
[COLOR=#111111][FONT=Ubuntu][FONT=arial]regards
Christian
Network Admin
[https://www.clouddesktoponline.com/](https://www.clouddesktoponline.com/)[/FONT]


[/FONT][/COLOR]

---

### Post by SeijiSensei on 2017-05-27
Do not connect both ports to the same router.  If the wifi device is connected to a gateway router that sees the Internet, then the Ethernet device should have a "static" IP address in an entirely separate IP subnet.  So if the wifi has address 192.168.0.2, use something like 192.168.1.2 for the Ethernet side.  

If you want to connect from wired devices to the Internet, you need to use "masquerading" as described in this document: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing).  My PS3 and TV use this type of arrangement.  They are connected via Ethernet to a computer running Kubuntu that is itself connected to the Internet via wifi.  

You don't need any type of bridging with this arrangement.  It all runs using standard TCP/IP routing.

---

