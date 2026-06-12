---
title: "Help setting up a network with XP/Vista"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by silent contender on 2008-08-19
I dual-boot Windows XP on my laptop.  The problem is in Ubuntu, I cannot connect to my LAN network of Windows computers, but I do have internet in Ubuntu.  When I switch to XP on my laptop, I have no problem connecting to the LAN or internet.

One thing I did notice is Wireshark does not work in Ubuntu, without using *sudo*, which is bad.

Please keep answers simple, because I know VERY little about networking (though I am willing to learn).

---

### Post by SZ07 on 2008-08-19
How did you try connect to your Windows network? For me, I just had to go to Places>>Network>>Windows Network and I was able to connect to my home network.

---

### Post by tuxulin on 2008-08-19
i thought linux and windows used different network protocols
i didnt know that ubuntu could connect directly to windows
out of the box.

DAM, if i knew this at the beginning then i would of never 
based my linux to xp network around **samba**

Tuxulin

---

### Post by chkneater on 2008-08-19
I have a similar problem connecting to a Windows network with Ubuntu 8.04.  It show their is a Windows network under places/network but it shows 0kb and clicking on it opens an empty folder.  I know that the network is available and can be accessed by other windows computers.  I don't dual boot tho.

---

### Post by jonandrews on 2008-08-20
I've put step-by step guides to XP / Ubuntu networking on this website:
[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

They should help you get sorted.

---

### Post by silent contender on 2008-08-21
I forget to mention that Ubuntu networks on D-Link routers without MUCH hitch.  However, the Linksys EZXS55W router doesn't work with Ubuntu, and occasionally Windows.  The Linksys router assigns IP addresses that differ in the last two numbers (i.e. 192.168.X.X)

---

### Post by chkneater on 2008-08-22
Thanx, that helps me at least, we use a Dlink router.  Any idea if it's just that I can't view Windows files or does it not work both ways? I see the Windows network icon in the Network folder and I've installed Samba and made some folders shareable.

---

### Post by silent contender on 2008-08-23
I also noticed today that my network card on my laptop is not recognized by ubuntu.  When I open Network Tools and try to configure my card (eth0) under Devices, I get

"The interface does not exist
Check that it is correctly typed and that it is correctly supported by your system."

Funny thing is I have a working internet connection.  My output from running ifconfig:

eth0      Link encap:Ethernet  HWaddr 08:00:46:cd:b8:c8  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fecd:b8c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68266771 (65.1 MB)  TX bytes:23373131 (22.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57980 (56.6 KB)  TX bytes:57980 (56.6 KB)

---

### Post by seagullplayer77 on 2008-08-24
Seems kind of odd that you can't get your Windows network. All I have to do to get into mine is go to Places > Network > Windows Network, and then put in a password (your Ubuntu login PW if you don't have a separate one for the network). Oddly enough, it's easier to access my Windows network resources (printers, files, etc.) with Ubuntu than it is with Windows. Have you been able to get your Windows network with other Windows machines before?

---

### Post by silent contender on 2008-08-24
The Windows computer did network at one time to another XP computer, but then the network somehow how broke.  I have another network in my house, and the Windows computers on that connect fine.  I cannot connect to that network either, but I get Internet and printers on that one.

I think I might be able to give or solve this problem, if someone could tell me how to configure/install my network card.  Networking tools doesn't recognize my card.

---

### Post by pizzavortex on 2008-08-24
Doesn't smb://[windowsipaddress] work in nautilus?

---

