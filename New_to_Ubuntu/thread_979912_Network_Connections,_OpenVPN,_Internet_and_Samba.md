---
title: "Network Connections, OpenVPN, Internet and Samba"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by carltonnotthedoorman on 2008-11-12
Hello All,

I've decided to make the jump in to the world of Linux and it looked like Ubuntu was the best place to start. I'm about 4 weeks in and have it set up as the only operating system on a machine I'd like to use as a file server, media server and web server among other things. I'd been moving along pretty well until recently.

I had all of my network connections working correctly, was able to access the internet, set up a few samba shares and was able to access them through the network. Then, a few weeks ago, I decided to make a stab at OpenVPN, as one of the reasons I wanted to do all this was to set up a way to access my media files securely from wherever I was. I don't think it's important as far as this conversation goes, but the machine I want to access it with is a MacBook Pro that is dual booting Mac OS X and Ubuntu. The flavor of ubuntu I am using on both machines is 8.10 (intrepid ibex) server version on the server and desktop on my Mac. 

Getting OpenVPN installed and running was fairly easy, as was getting the Mac to connect to it. Where I had trouble was getting the Mac to connect to the Samba shares I had set up on the server. This problem has taken me a few weeks to solve. On Monday I had a great moment of luck, as I changed a couple of settings in the smb.conf file to allow connections via the OpenVPN subnet as well as the local subnet (this was done before, but according the OpenVPN HOWTO, I was supposed to add the local host IP 127.0.0.1 and I had neglected to do that previously). So, I added the local host IP, and voila, I was able to connect to my samba shares through my VPN connection. Now, after a few days away from the whole thing, I'm back on the server and I've found that the server has no internet connection and I am unable to connect to the samba shares via the local network (which I was able to do previously). So, I am able to connect to the server via OpenVPN, but that appears to be the only thing the server will connect to.

Help?

Thanks

---

### Post by carltonnotthedoorman on 2008-11-12
OK, I went in and removed the reference to 127.0.0.1 in smb.conf, and I still have no internet or local samba connections, but I still have my OpenVPN connection, so I guess that had nothing to do with anything. 

Anticipating the question, here is the return from ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:11:25:5f:a6:15  
          inet addr:10.0.1.200  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe5f:a615/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46467 (46.4 KB)  TX bytes:38672 (38.6 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4100 (4.1 KB)  TX bytes:4100 (4.1 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 

```

---

### Post by carltonnotthedoorman on 2008-11-12
Well, sorry to waste anyone's time, but I figured out the problem myself. In one of these forums somewhere trying to get my OpenVPN connections to work, I added the following two lines to the bottom of my server.conf file for OpenVPN...

```
route 10.0.1.0 255.255.255.0
route 10.8.0.0 255.255.255.255
```

This apparently allowed my OpenVPN connection, but disallowed all local connections. I commented out the top line, restarted OpenVPN and all is well.

Though no one responded to my thread I appreciate any aticipated responses.

---

