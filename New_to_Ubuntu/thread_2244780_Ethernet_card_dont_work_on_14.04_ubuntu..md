---
title: "Ethernet card dont work on 14.04 ubuntu."
date: 2014-09-18
forum: New to Ubuntu
---

### Post by Vagelism_Meintasis on 2014-09-18
Hello to all, just installed ubuntu and windows 7 on an intel NUC. I got  latest bios update and on windows everything runs fine with the NIC  card.
The problem comes to ubuntu when the card try to connect and never  connects. When I put manually the IP configuration, seems connected but  dont have INTERNET connectivity.
Any solution?
Thank you!

---

### Post by Michael_McKenney on 2014-09-18
Does the adapter show up on the device list?  Did you try hard setting the IP, Mask and gateway on the adapter.  I found my onboard NIC of my Intel DG33TL board did not work and I purchased a $20 Gbps NIC that had no issues.

---

### Post by Vagelism_Meintasis on 2014-09-18
I dont know how to see it on the device list. But should be since I can hard set the ip , mask etc...when I do it it says it is connected , but I still dont have internet...

---

### Post by SeijiSensei on 2014-09-18
To see the available interfaces on the machine type "ifconfig" at a prompt.

My guess is that you don't have a default gateway specified.  Run the command "route -n".  Does it have an entry for "default" or "0.0.0.0"?  Does it point to your router as its gateway?

If not, you need to include a "gateway ip.of.your.router" directive in the eth0 stanza in /etc/network/interfaces.

---

### Post by Vagelism_Meintasis on 2014-09-19
No is not that. I define default gateway and still not working. It has the symbol of connected but still can not ping not even the router that is the dafault gateway.

---

### Post by Michael_McKenney on 2014-09-19
ctrl+alt+t open terminal
lspci will list all your controllers  

See if your on board nic shows up.  You could get an inexpensive Gbps NIC and try it.  That was my solution.

---

### Post by Vagelism_Meintasis on 2014-09-19
Sounds great...but why to buy something extra whren there is a NIC on the pc? Besides on windows works just fine.

---

### Post by The Cog on 2014-09-19
Can you please post the output of these two commands - it should help us work out what's happening:
```
ifconfig
route -n
```

---

### Post by Vagelism_Meintasis on 2014-09-19
> **Michael_McKenney said:**
> ctrl+alt+t open terminal
lspci will list all your controllers  

See if your on board nic shows up.  You could get an inexpensive Gbps NIC and try it.  That was my solution.

Yes the NIC appears there.

---

### Post by Vagelism_Meintasis on 2014-09-19
> **The Cog said:**
> Can you please post the output of these two commands - it should help us work out what's happening:
```
ifconfig
route -n
```

```
ipmaniac@ipmaniac-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr c0:3f:d5:64:73:62  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c23f:d5ff:fe64:7362/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:624 (624.0 B)  TX bytes:10414 (10.4 KB)
          Interrupt:20 Memory:f7c00000-f7c20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6000 (6.0 KB)  TX bytes:6000 (6.0 KB)


ipmaniac@ipmaniac-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
ipmaniac@ipmaniac-desktop:~$ 




```

---

### Post by Michael_McKenney on 2014-09-19
A $20 card saved me hours of work trying to fix it.  I also have better file transfer performance on the PCI NIC over the onboard one.  

Is your router 192.168.1.1? I change my router gateway address to another address instead of default.  

Those errors could be mismatched speed or duplexing.  Half duplex setting on a switch will cause those errors.  On our corporate network the switch ports are hardset to 100 or 1000.  If the connecting nic is not also set to same speed, it can error out.   Did you try another cable?  A CAT 5 cable will not do 1 Gbps.   You need 5e or 6.

---

### Post by Vagelism_Meintasis on 2014-09-19
I hardset the NIC to 100 Mbps. Still nothing.

---

### Post by Michael_McKenney on 2014-09-19
You said it works in Windows.  Reboot to Windows and check your settings, IP address, mask and gateway.  If it works, the cable is good and we know the nic works in Windows.   What are those settings for speed, duplex of the controller, IP Address, Mask and Gateway.

---

### Post by The Cog on 2014-09-19
That's odd. Your ifconfig and route both look good. There are fewer receive packets than I would expect after you have sent that many, but it's not proof of any problem.
Perhaps you could try these few commands please:
```
ping -c 3 192.168.1.1
arp -n
```
Maybe you could run **sudo tcpdump -n** (a packet capture) in another window while you are doing that, to capture what's happening on the wire. And wait until a packet or two are received from another device before stopping it - capturing the odd packet from other devices might give a useful clue.

---

### Post by Michael_McKenney on 2014-09-19
I had the same problem and went and bought a cheap nic and fixed it.  lspci did not show all the components on the board.  So I figured the nic did not completely load correctly.  The Intel DG33TL had issues.  My Tyan Thunder K8WE board found everything.  It was designed for enterprise Linux.

---

