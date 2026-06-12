---
title: "ubuntu 12.04 wired internet connection is intermittent"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by Velenjak on 2013-01-12
I dual boot windows 7 and ubuntu 12.04. ubuntu 12.04 partition had no problems at all for about a month until yesterday. The internet is very "patchy" - it turns on, and then loses connection after about 30 seconds. This is a ubuntu specific issue, not my internet connection. I am able to stay online fine on my windows partition. Please help, thank you.

---

### Post by Velenjak on 2013-01-12
Please help

---

### Post by squakie on 2013-01-12
Please allow 24 hours before posting again unless you are adding something.

It might be that you received an update and it may have cleared something to do with your wireless driver.

Please do the following:

[LIST]
[*]open a terminal window
[*]type lspic > ~/abs-network.txt
[*]type lsusb >> ~/abs-network.txt
[*]type iwconfig >> ~/abs-network.txt
[*]type ifconfig >> ~/abs-network.txt
[/LIST]
Please note a single ">" on the first line, but all the rest are double  - ">>".  This creates a file in your home folder called abs-network.txt that will contain some information for us to try to help you.


Post a reply back here and use the paperclip to attach the file ~/abs-network.txt with the reply.

---

### Post by Frogs Hair on 2013-01-12
You stated wired connection so I don't no if an update affecting a wireless driver would come into play at least it hasn't for me. Select the network icon and view connection information. Is it IPV4 or 6 ? Most services still use 4 but some depending on location could be 6.  

You may want to look at the link and do more research. [http://askubuntu.com/questions/87003/intermittent-internet-connectivity](http://askubuntu.com/questions/87003/intermittent-internet-connectivity)

---

### Post by squakie on 2013-01-12
Yeah, sometimes an update comes through and results in somethings being updated that you wouldn't think would.  Perhaps the OP can check to see what updates went in.  In the mean time we can wait for the information requested.

EDIT:  I also hadn't noticed until now that the OP doesn't actually mention wireless, but instead the wired connection.  What I was thinking probably doesn't apply here - sorry! ;)

---

### Post by Velenjak on 2013-01-13
> **Frogs Hair said:**
> You stated wired connection so I don't no if an update affecting a wireless driver would come into play at least it hasn't for me. Select the network icon and view connection information. Is it IPV4 or 6 ? Most services still use 4 but some depending on location could be 6.  

You may want to look at the link and do more research. [http://askubuntu.com/questions/87003/intermittent-internet-connectivity](http://askubuntu.com/questions/87003/intermittent-internet-connectivity)

IPv4 is set to Automatic (DHCP) and IPv6 is set to Automatic - I don't quite understand the other suggestions. 

I am currently using a wired connection to a school network, if that changes any diagnosis...

ifconfig reads:

eth0      Link encap:Ethernet  HWaddr 8c:89:a5:e5:e6:90  
          inet addr:129.65.234.131  Bcast:129.65.234.255  Mask:255.255.255.0
          inet6 addr: fe80::8e89:a5ff:fee5:e690/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33913335 (33.9 MB)  TX bytes:1453034 (1.4 MB)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104041 (104.0 KB)  TX bytes:104041 (104.0 KB)

---

### Post by Frogs Hair on 2013-01-13
> I am currently using a wired connection to a school network, if that changes any diagnosis...

I have seen posts reporting problems with this in the past but have no experience with this problem. Wired connections on Ubuntu have been golden for me since started using it . I would search the forum and Google because I remember reading that some school networks are not Linux friendly. You could contact the administrator to eliminate or confirm that possibility.

---

