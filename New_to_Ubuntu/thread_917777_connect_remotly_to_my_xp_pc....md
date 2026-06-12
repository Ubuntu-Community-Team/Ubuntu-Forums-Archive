---
title: "connect remotly to my xp pc..."
date: 2008-09-12
forum: New to Ubuntu
---

### Post by inter-m on 2008-09-12
im always using my ubuntu on my laptop at home but sometimes i need to use something my pc which happens to run xp... i want to access my pc from my laptop... and i heard about remote desktop connection... but i have no clue on where to start...

K.H

---

### Post by gvartser on 2008-09-12
1) Enable Remote desktop on your XP machine:
   [http://www.microsoft.com/windowsxp/using/mobility/getstarted/enableremote.mspx](http://www.microsoft.com/windowsxp/using/mobility/getstarted/enableremote.mspx)

2) Install "rdesktop" on you Ubuntu machine:
   ```
sudo apt-get install rdesktop
```
   OR
   use synaptic package manager: search for "rdesktop"

3) Connect to your XP machine by entering the IP address in the connection display.

4) Done.

/g

---

### Post by dhtseany on 2008-09-12
OR

Follow his link to enabling RDC and click on Applications -> Internet -> Terminal Server Client.

Fill in the needed info (Most likely you'll only need the name of the computer and set the protocol to RDC). Hit connect and you should be in business.

Peace
Sean

---

### Post by acidsolution on 2008-09-12
```
 rdesktop ip-address 
```

if you want full screen than 
```
 rdesktop -f ip-address 
```

to exit from fullscreen press 
CTRL+ALT+ENTER

---

### Post by JoulesG on 2008-09-12
... cool - yet another nail in Redmond's coffin!

Cheers

JoulesG
:lolflag:

---

### Post by JoulesG on 2008-09-12
of course it alsoi works for remote Windows servers ... 

JoulesG
:guitar:

---

### Post by tuskenraider on 2008-09-12
me personally i use gnome-rdp  i like it alot and its easier to use than command line or the terminal server client... but thats just me.

tusk

---

### Post by dhtseany on 2008-09-12
Glad to hear your problem is solved!

Make sure to mark it solved under thread tools and thank whoever helped you ;)


peace
Sean

---

### Post by halitech on 2008-09-12
you can also use Log Me In ([http://www.logmein.com](http://www.logmein.com)) to access the pc. It will allow you to access it from any computer with an internet connection.

---

### Post by inter-m on 2008-09-12
thanx for this info... i tried all of that but the thing is how would i know my ip add on both my machines... keeping in mind i used [http://whatismyip.com/](http://whatismyip.com/) to get my ip... and the strange thing it gave me the same ip on both my laptop and pc...

---

### Post by halitech on 2008-09-12
you can use dyndns to create a static hostname and use that to connect instead of the IP address.

are you using a router at home?

---

### Post by dhtseany on 2008-09-12
A brief explaination is that you have a public IP for your DSL or cable (Thats what whatismyip.com spit back at you). You also have internal or local IP addys. On Window$ click on Start -> Run then type "cmd".
```
C:\> ipconfig
MS Network Config blah blah blah

Local Area Connection 1:
Network Address.... **192.168.1.2**
Subnet Mask........ 255.255.255.0
Defaul Gateway..... 192.168.1.1

```

The network address will be your machine's IP address.

On UB open the terminal and type the following:
```
$: ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:cf:41:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:18:fd:46  
          **inet addr:10.15.20.100**  Bcast:10.15.20.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe18:fd46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10454 errors:15 dropped:15 overruns:0 frame:0
          TX packets:9453 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:404863955 (386.1 MB)  TX bytes:45357071 (43.2 MB)
          Interrupt:18 Base address:0x6000 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103800 (101.3 KB)  TX bytes:103800 (101.3 KB)

```

The bolded "inet addr:" if your local IP addy on the UB computer.

If you need more help just ask :)

Peace
Sean

---

### Post by Maheriano on 2008-09-12
This will help me out as well, thanks fellas!

---

### Post by inter-m on 2008-09-12
yes im using a router... and im not clear on the dyndns thing???

---

### Post by dhtseany on 2008-09-12
If you don't need to access your XP box outside your house then don't worry about it. Use the method I showed you and use the local / inside your house addresses to connect to one another. I think what halitech was trying to explain is how to set this up so you can connect to your XP box outside of your house (ie from the office or a place with free wifi, etc).

Peace
Sean

---

### Post by halitech on 2008-09-12
if you have a router then the external IP address would need to be forwarded to your computer and if its dynamic, it could change so if you have an account at [http://www.dyndns.com/](http://www.dyndns.com/) then you could have a name like interm.homelinux.com and you would use that instead of having to try and find your external IP address all the time

---

### Post by inter-m on 2008-09-12
thanx all for ur help... im happilly connected to my pc this moment all thanx to u guys... but i have a couple of inquiries before i mark it as solved... right now im connected from ubuntu to xp... but when i tried the opposite it didnt work... any ideas why???

how would i connect remotely from a computer outside my home network???

---

