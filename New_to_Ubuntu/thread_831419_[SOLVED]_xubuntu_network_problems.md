---
title: "[SOLVED] xubuntu network problems"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by dave00001 on 2008-06-16
So, I just recently installed xubuntu hardy on an older computer (Pentium III, 1 GHz, 128Mb RAM) for a friend... problem is, I can't get the internet connection to work!

The install went flawlessly, and everything seems to be working fine, but when I try to connect to my wired connection via my cable modem it's a no-go, which means I can't sudo apt-get update my system!!

I have another machine running an xp/ubuntu hardy dual boot, and this connection works fine with this other computer, so I'm assuming it might be a problem with my settings??

I'm still kindof new to ubuntu, and any help you guys can give would be really useful!

EDIT - If it helps - my ethernet card is a D-Link DFE 530Tx..  I'm going to see if it's a driver issue....

---

### Post by NT4usB on 2008-06-17
A quick [Google]("http://www.google.com/search?num=50&hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=Wq0&q=site%3Aubuntuforums.org+D-Link+DFE+530Tx&btnG=Search") finds several hits on that card. I didn't read any but may be a problem child. Check it out.

---

### Post by dave00001 on 2008-06-17
I think there is a linux version of the driver available...  I'm guessing I can download the tar.gz file on a separate computer which actually has internet access, and transfer it over??  I'll let you know how it goes.

EDIT - these are the results of the "ifconfig" command - I'm not sure if my system is recognizing the card right or not??  I've had to retype it into here so please forgive me if it's not exactly the way it should be..

eth0    
Link encap:Ethernet HWaddr 00:50:ba:2d:da:0a
inet5 addr:fe80::250::baff:fe2d:da0a/64 Scope:Link
UP BRIADCAST MULTICAST MTU:1500 Metric:1
RX packets:5 errors:0 dropped:0 overruns:0 frame:0
TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1872 (1.8 KB)  TX bytes:4901 (4.7 KB)
Interrupt:5 Base address:0xa000


eth0:avahi
Link encap:Ethernet JWaddr 00:50:ba:2d:da:0a
inet addr:169:254:5:230  Bcast 169:254:255:255  Mask 255:255:0:0
UP BROADCAST RUNNING MULTICAST MTU:1500 metric:1
Interrupt:5 Base address:0xa000

lo
Link encap:Local loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:62 errors:0 dropped:0 overruns:0 frame:0
TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:3884 (3.7 KB)  TX bytes:0 (3.7 KB)

---

### Post by cariboo on 2008-06-17
There should be a lot more output then that for ifconfig:

To check that the module is loaded in a terminal type:

```
lsmod | grep 8139
```

if not try:

```
sudo modprobe 8139
```

Then restart networking:

```
sudo /etc/init.d/networking restart
```

Jim

---

### Post by dave00001 on 2008-06-17
Thanks for the reply, Jim.

I was in the midst of finishing my post - you can see the full results of the ifconfig above -sorry!!](*,)

As for your suggestion, I tried:

lsmod | grep 8139

and got no visible response from terminal.

sudo modprobe 8139

returned "FATAL: Module 8139 not found."

What does this mean?

Once again, thanks for your help ;)

---

### Post by dave00001 on 2008-06-18
Ok.. well I think I've tried just about everything a noob can for the past two days, including trying to find the drivers, and no luck..

To see if it was a driver issue, I pulled out the d-link and tried a relatively new Linksys LNE100TX ethernet card, hoping that it would do the trick... but alas, I have the same problem...  

So, I then tried to re-install xubuntu dapper through the alternate install CD to see where the problem was.  I get stuck at the network autoconfiguration step:

"Network autoconfiguration failed
Your network is probably not using the DHCP protocol.  Alternatively, the DHCP server may be slow or some network hardware is not working properly"

I can run two other computers which collectively run XP, ubuntu hardy and xubuntu hardy with the same ethernet connection, so I am really stumped as to why this older box will not autoconfigure.  I really only need the internet connection working on this older box to get me going, but it's getting pretty frustrating!

Any ideas??

---

### Post by NT4usB on 2008-06-18
Couple wags...
Does the board have onboard NIC (probably not) disable it.
Has the board ever worked on a network?
Move the card to a different PCI slot.
Are you getting any green blinks out of the LED on the card.
Poke around the BIOS, see if anything PCI can be set... set it to auto. Things like WOL, etc. if it's enabled, disable it or vice versa.
What does this print:```
lspci
```
If autocinfig fails to get a DHCP address, they sometimes assign a static IP. You have to go into network settings, nuke the static IP and reselect DHCP.
Maybe try a static IP?
May be a DNS issue. Can you ping a known good IP address or the Router IP?
NICs should just work, I dunno...

---

### Post by dave00001 on 2008-06-19
Thanks alot for the reply, NT4usB, but I finally messed around with it enough for it to work!

For those of you looking for the same fix, the problem turned out not to be a driver problem after all.. I went back to xubuntu dapper, which has a slightly different network configuration GUI, and I basically just had to go to system->networks, activate it, and turn it on.  Once that was done, a quick off/on with the cable modem (and the computer off) did the trick!

I appreciate all the help guys!

Cheers,

Dave

---

