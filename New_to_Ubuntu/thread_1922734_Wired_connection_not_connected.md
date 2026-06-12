---
title: "Wired connection not connected"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by Radhika Mandra on 2012-02-09
I was happily using Windows7 but later realized I need ubuntu to learn and work on things like python and django better...
So i used wubi to install ubuntu..
As i tried to connect to the broadband it says "wired connection not connected" 
My internet works absolutely well from windows7..
please help...i can't download and install any required packages without internet...

---

### Post by Fayaz427 on 2012-02-09
[https://help.ubuntu.com/10.04/internet/C/connecting-wired.html]("https://help.ubuntu.com/10.04/internet/C/connecting-wired.html")
i think this may help you....
and which version of ubuntu have you installed?

---

### Post by winh8r on 2012-02-09
Please post details of what version of Ubuntu you are using, what type of computer and router/modem you are using.

Also , open a terminal and type

ifconfig

and hit enter

then post the results here.

---

### Post by Radhika Mandra on 2012-02-09
I have installed ubuntu 11.10 using wubi on windows7..

In the network manager i did edit the details in the wired connection as per the ipaddr, subnet, gateway and DNS given by my broadband service provider.
Then suggested in the above post i did ifconfig and this is what i got...

eth0      Link encap:Ethernet  HWaddr 00:26:b9:1e:5c:b0  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:fe1e:5cb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12389 (12.3 KB)  TX bytes:32499 (32.4 KB)
          Interrupt:41 Base address:0x6000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:584 (584.0 B)  TX bytes:584 (584.0 B)


Now instead of "wired connection disconnected" it says "wired connection established" but still the browser cant open any page..

---

### Post by winh8r on 2012-02-09
Open your browser and select "File" on the menu tabs and make sure "Work Offline" is not selected.



If it still will not connect, open your browser and open a new tab.
in the address bar type about:config
hit enter
click i promise i will be careful

in the search box type ipv6
hit enter
the entry that appears should say:

network.dns.disableIPv6

select it 

right click on it and select "toggle"

it should now read 

network.dns.disableIPv6  user set  boolean  true


close this window.

close browser

reboot and try to connect again.

---

### Post by Radhika Mandra on 2012-02-13
did all the above things but still it doesn't work..

please help soon since i have a interview coming in a week and i need to practice at least the basics of python and django on ubuntu.. please help!!

---

