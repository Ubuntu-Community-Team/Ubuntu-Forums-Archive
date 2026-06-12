---
title: "Trouble Connecting and/or Using"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by dugorek on 2013-01-16
Okay, I'm fairly new to this stuff, but my wife has a Compaq Mini that uses the Ubuntu 10.04 LTS operating system.  It is connect via wifi to a Linksys E900 router.  It says it is connected, but Firefox 15.0.1 (Mozilla Firefox for ubuntu canonical - 1.0) can't access the net, saying server not found.  I have it set to "Auto-detect proxy settings for this network", though I've tried the no proxy setting as well.  The network proxy preferences are set to direct internet connection (under system > preferences > network proxy) and the network setting for the connection as in Ad-hoc mode, using a WEP 128-bit passphrase for security.  I thought I made a stupid mistake in the above settings (and still might have), but I have another wrinkle.  I've tried using Update Manager, and tell it to check for updates manually.  This never caused a problem before, but it "could not download all repository indexes".  It says there are network problems (though it says the network connection is active 100%).  It has many listed mistakes that use this format (the first of the errors):

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

Can someone tell me what the heck I'm doing (wrong)?  I'm staying on this page, updating often, just so I can get this taken care of and get my wife off my back  :)  Thank you for your time...

---

### Post by mapes12 on 2013-01-16
1. Has your Compaq connected OK in the past?
2. Have you tried rebooting the router?

---

### Post by dugorek on 2013-01-16
1. While there have been occasional problems in the past, generally it has worked fine.  However, this is a new router.  The router is working for all other computers in the house.
2. Rebooting the router and everything else individually was one of the first things I did and didn't help.

---

### Post by dugorek on 2013-01-16
Bump? 

If it matters, it was connecting to the previous linksys wifi router with no issues, so I'm really thinking it isn't the router...

---

### Post by dugorek on 2013-01-17
Is there any more info I can provide that might help aim me towards a solution?

---

### Post by Warren Hill on 2013-01-17
There are a few possibilities

1.  The DNS server isn't working correctly

To test this in your web browser try this as an address
212.58.241.131

This should take you to the bbc home page.  If it does then you can use the DNS server at 8.8.8.8.  I can give you the command to do this

2.  You are not connected to the network you think you are to test

```
ifconfig; route -n; ping 8.8.8.8
```

Post results back here and we can advise further

---

### Post by Zill on 2013-01-17
> **dugorek said:**
> Okay, I'm fairly new to this stuff, but my wife has a Compaq Mini that uses the Ubuntu 10.04 LTS operating system.  It is connect via wifi to a Linksys E900 router...
Wifi always brings its own "can of worms" into the equation so, as a temporary measure, I would exclude this.  Just link the computer to the router with an ethernet cable and see if you can then browse the web.

If this does work then it means that the router internet connection is configured correctly and that the problem is with either the router *or* the computer wifi configuration.

---

### Post by dugorek on 2013-01-17
Warren: To 1 above, I still had no connection through Firefox or special result with the ip addy you gave.  Then I put the code you provided on the Terminal and got the following:

eth0       Link encap:Ethernet  HWaddr 03:ee:e6:d4:8e:90
             inet addr:10.42.43.1  Bcast:19.42.43.255  Mask:255.255.255.0
             inet6 addr: fe80::eee:e6ff:fed:8e90/64 Scope:Link
             UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:21633
             TX packets:54 errors:6 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX: bytes:0 (0.0 B)  TX bytes:9112 (9.1 KB)
             Interrupt:16 Base address:0xc000

lo           Link encap:Local Loopback
             inet addr:127.0.0.1  Mask:255.0.0.0
             inet6 addr: ::1.128 Scope:Host
             UP LOOPBACK RUNNING  MTU:16436  Metric:1
             RX packets:136 errors:0 dropped:0 overruns:0 frame:0
             TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:0
             RX bytes:9728 (9.7 KB)  TX bytes:9728 (9.7 KB)

Kernel IP routing table
Destination        Gateway             Genmask             Flags Metric Ref     Use  Iface
19.42.43.0         0.0.0.0               255.255.255.0      U      2        0           0  eth0
169.254.0.0       0.0.0.0               255.255.0.0          U      1000   0           0  eth0
Connect: Network is unreachable

[Note: This is while the wifi connection thing says the wireless network connection is active 100%]



Zill: Oddly enough, when I tried a corded connection, my connection icon menu wouldn't acknowledge it and I still got no connection for firefox or update manager.  Now I'm really confused.  HELP!?!

---

### Post by Warren Hill on 2013-01-18
What's the output of 
```
cat /etc/network/interfaces
```

---

### Post by Zill on 2013-01-18
dugorek: This doesn't seem right to me:
> **dugorek said:**
> 
             inet addr:10.42.43.1  Bcast:19.42.43.255  Mask:255.255.255.0
What is the (local) IP address of your router?

---

### Post by dugorek on 2013-01-18
Warren: Here is the results of your 2nd request:
auto lo
iface lo inet loopback

Zill: The IP addy for the router is 192.168.1.1 - I agree that this doesn't seem right in the results, but I have absolutely NO idea what to do about it.

---

### Post by dugorek on 2013-01-18
Additional, mostly to Zill:
I was able to go to that addy on my computer that is also on wifi.  It got me access to the router's admin console.  HOWEVER, when I tried it on my wife's compaq (the one that has ubuntu), I got nothing.  All this tells me that it isn't connected.  If this is true, why does the icon on the taskbar next to the volume say I'm connected 100%.  This is the part that is really throwing me...

---

### Post by Zill on 2013-01-19
> **dugorek said:**
> ...If this is true, why does the icon on the taskbar next to the volume say I'm connected 100%.  This is the part that is really throwing me...
AIUI, this applet indicates wifi connection strength, not wired connections.  I would first concentrate on getting a wired connection working properly and *then* move on to the wifi configuration.

Assuming you are using the "network-manager" GUI applet, this provides a "managed" connection that is independent of the contents of /etc/network/interfaces.

Firstly, you need to ensure that your new router actually has your chosen address 192.168.1.1.  Test for this from a "working" machine with the following command:
```
ping 192.168.1.1 -c5
```
If you get an error (such as "Destination Net Unreachable") then the router address needs to be changed via the router config screen.  You may find it best to do a "hard reset" of the router to set everything back to defaults and then re-enter your ISP broadband details.

Secondly, use the router config screen to check that the router DHCP server is "on" so that it will deliver IP addresses to connected clients.

Thirdly, plug the ethernet cable in to link the (suspect) computer to the router.  Right-click on the network-manager icon and ensure that "Enable Networking" is checked.  Click on "Edit Connections" and select the "Wired" tab.  "Auto eth0" should be selected.  Close this screen.

Right-click on the network-manager icon and select "Connection Information".  The tab entitled "Auto eth0" should show the following:
IP Address:  (your PC IP address obtained via DHCP)
Broadcast Address:  192.168.1.255
Subnet Mask:  255.255.255.0
Default Route:  192.168.1.1
Primary DNS:  192.168.1.1

See if you can browse the web with the wired connection.  Please advise if this works or advise any discrepancies from the above.

---

### Post by mapes12 on 2013-01-19
Do you have any other machines connected to the router (wired or wifi, doesn't matter) that are connecting to the internet OK? If yes, then your DHCP and DNS services seem to be working correctly on the router. That being the case then something is screwed up with your Ubu box network settings. It could be that **network-manager** has somehow become corrupted. Uninstalling it (completely) and then re-installing it should reset it.

---

### Post by dugorek on 2013-01-20
Okay, for some reason, this time the ethernet connection worked, so I'm a step further than I was.  Zill, looking at the expected connection information, it all matches up, EXCEPT for the primary DNS, which according to the info the system gives me is 207.191.192.130 - It is clear this is the problem.  Can anyone tell me how to change it?

---

### Post by Zill on 2013-01-21
dugorek:  Assuming we are *just* talking about the Network Manager wired ethernet connection for now (wifi can be done later!) it seems that the "Default Route" is 192.168.1.1 and the "Primary DNS" is 207.191.192.130.

As the "Primary DNS" should be the same address as the router, it is possible that your Network Manager connection is corrupted.  I would try deleting the (Wired) "Auto eth0" connection.  Then reboot the computer and (hopefully!) a new "Auto eth0" will have appeared and "Connection Information" should now show the correct DNS IP (192.168.1.1).  You should now be able to browse the web.

As an additional check I suggest you open the config screen of the router (enter 192.168.1.1 in to your web browser) and then check the router DNS settings.  You *should* have one or two IP addresses supplied by your ISP for their DNS servers.  If you wish you could use different DNS servers such as Google's (8.8.8.8 and 8.8.4.4).

---

### Post by rameshandeepak on 2013-01-21
if there are a number of systems using the wifi there might be a possibility of ip conflict

---

