---
title: "wont connect to internet wireless"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by zuttoh on 2008-10-26
yeah so now my problem is that it wont connect to internet.. it tries to but it just wont ;/
when i click the icon on top right i see the place where it should connect wich is named Default but it just wont ;/

atm using windows via safe mode.. 

wireless connection :)

just hit me with some ideas

---

### Post by Nxion on 2008-10-26
When did this all start to occur? Was it after an update? Or has this been an ongoing issue?

---

### Post by zuttoh on 2008-10-26
> **Nxion said:**
> When did this all start to occur? Was it after an update? Or has this been an ongoing issue?

just installed ubuntu.. never been able to connect internet yet ;/

---

### Post by Peter09 on 2008-10-26
What flavour of Ubuntu are you running? Why are you in recovery mode?

---

### Post by Peter09 on 2008-10-26
Can you connect using a wired connection, that will then let you download any updates that might help.

---

### Post by zakirs on 2008-10-26
just a dumb question .. did u switch on your wireless :P

---

### Post by zuttoh on 2008-10-26
> **zakirs said:**
> just a dumb question .. did u switch on your wireless :P

yes i did :)

and no i cant connect with wire's ;/
but i can connect via windows safe mode so i think i can d/l the updates on this and save em on pc boot to ubuntu and install em :) but i have no idea what i need

---

### Post by Peter09 on 2008-10-26
Can you post the output of the next two commands - you need to run them in a terminal  which you can get from the menus Applications->Accesories->Terminal

```
ifconfig
```
and
```
lshw -C network
```

---

### Post by zuttoh on 2008-10-26
ill try takes while

---

### Post by Peter09 on 2008-10-26
Just looked at your original Post. Are you attempting to connect to an encrypted network (WEP etc) and if so have you entered your encryption key?

You do this by clicking on the network you want to connect to.

---

### Post by zuttoh on 2008-10-26
> **Peter09 said:**
> Just looked at your original Post. Are you attempting to connect to an encrypted network (WEP etc) and if so have you entered your encryption key?

You do this by clicking on the network you want to connect to.

O.o didnt see anything about that.. and when i tried few months back connect with my laptop it worked w/o any problems my network doesnt have pw or anything..

---

### Post by Peter09 on 2008-10-26
OK,
right click on the network icon (a set of vertical bars top left). You should see a list of available wireless networks. Select the one you want by ticking its radio button next to it.

You should be able to connect. 

I seem to recollect a bug somewhere which makes connecting to open wireless networks a problem, this may have been resolved.

---

### Post by zuttoh on 2008-10-26
thats exactly what i am doing [clicking it, selecting the place where i want to connect] but it just wont connect..

```
omistaja@Elisa:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:92:94:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58000 (56.6 KB)  TX bytes:58000 (56.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:40:05:29:31:55  
          inet6 addr: fe80::240:5ff:fe29:3155/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:966 (966.0 B)  TX bytes:258 (258.0 B)
          Interrupt:21 Base address:0xe800 



omistaja@Elisa:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

omistaja@Elisa:~$ 


```

---

### Post by Peter09 on 2008-10-26
OK the lshw command failed because it needed a capital C in -C. Not to worry as I can see that your wireless card is running ok. 

At the moment I cannot see why you are not connecting to your network. Will have to think some more about it. As a test are you able to put encryption on your network, or would that be a problem.

---

### Post by zuttoh on 2008-10-26
well.. i have no idea howto put it ;E
edit: and thanks allready for the help as a btw!

---

### Post by zuttoh on 2008-10-26
omistaja@Elisa:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:18:f3:92:94:40
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: wlan0
       version: 00
       serial: 00:40:05:29:31:55
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+
omistaja@Elisa:~$

---

### Post by prismpirate on 2008-10-26
> **Peter09 said:**
> Just looked at your original Post. Are you attempting to connect to an encrypted network (WEP etc) and if so have you entered your encryption key?

You do this by clicking on the network you want to connect to.
He can't connect using wired networks as well.

And he isn't using recovery mode in ubuntu, its safe mode in Windows.

Can you connect normally in windows though? I mean without safe mode?

---

### Post by Peter09 on 2008-10-26
Hi,
I think this one is yours

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94918](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94918)

may be worth doing an upgrade to the new Intrepid Release Candidate which is available for download. This bug may be fixed in that.

---

### Post by zuttoh on 2008-10-26
> **prismpirate said:**
> He can't connect using wired networks as well.

And he isn't using recovery mode in ubuntu, its safe mode in Windows.

Can you connect normally in windows though? I mean without safe mode?

i think so but my windows is raped by virusses.. this is only way i can be in internet atm ;/

looking up the link


edit: When i used my laptop [wich is broken atm.. that was few whiles back.. like 3months] i didnt have any problems connecting to net.. could it be some drivers or something?

---

### Post by zuttoh on 2008-10-26
info of my wireless:

my box is smc2404wbr, EU part no 750.9748  and inside my pc is: [http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_FIN&cid=5&scid=31&pid=1672]("smc2404wbr, EU part no 750.9748  and inside my pc is:http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_FIN&cid=5&scid=31&pid=1672")

---

### Post by zuttoh on 2008-10-27
none?

---

### Post by Peter09 on 2008-10-27
Hi,
sorry been away for a few days. My understanding is that the bug is present in  Hardy and I could not see a work around. However, as I said before, if you can download the release candidate for Intrepid you may find that it is resolved in there.

---

### Post by reg4c on 2008-10-27
Perhaps stupid suggestion but what the heck...

Try these:

```
sudo ifconfig wlan0
sudo iwlist wlan0 scan
```

Cheers

---

