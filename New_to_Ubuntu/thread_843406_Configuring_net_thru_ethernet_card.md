---
title: "Configuring net thru ethernet card"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by NikS on 2008-06-28
Hi,
I am using a broadband connection through a share modem OR router (m not sure about, if its called this).
I have LAN/eth card installed, n is detected by ubuntu.
but m not being able to configure it to get net acces.

I have the IP address, subnet mask, default gateway also DNS addresses: 1 preferred n other alternate, My username n password.

I can use the connection through winXP but I want to use net on ubuntu as well!!

Plz Help!!

Thanks All!!

---

### Post by prshah on 2008-06-28
> **NikS said:**
> 

I can use the connection through winXP but I want to use net on ubuntu as well!!


From windows, open a command prompt (Start-Run)```
cmd
```, press enter, then give the command```
ipconfig /all
``` and post the output here. This will give us essential information on your network, and allow us to guide you better.

---

### Post by NikS on 2008-06-28
Thanks prshah,
Here's the output:

Windows IP Configuration

        Host Name . . . . . . . . . . . . : neopc
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : RTL8139D PCI Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-A1-B0-01-18-91
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.100.56
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :
        DNS Servers . . . . . . . . . . . : 203.187.215.35
                                            203.187.192.12

PPP adapter utele:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 219.91.250.102
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 219.91.250.102
        DNS Servers . . . . . . . . . . . : 203.187.215.35
                                            203.187.192.15
        NetBIOS over Tcpip. . . . . . . . : Disabled

---

### Post by superprash2003 on 2008-06-28
also post output of ping google.com from the ubuntu terminal

---

### Post by NikS on 2008-06-28
Ok,
Now for that I'l have to restart my PC into Ubuntu n back to win..
Wait..
I'l be back..

---

### Post by NikS on 2008-06-28
Here's the output fromm the ubuntu terminal:


niks@Zion:~$ ping google.com
ping: unknown host google.com

---

### Post by NikS on 2008-06-28
Someone!!!!
PLZ Help!!!!

---

### Post by defrex on 2008-06-28
click on the network icon in the panel in ubuntu, and select "manual configuration"

click "unlock" and enter your password

select the "wired connection" and click properties

disable roaming mode and select static ip.

You should then be able to enter all your info and get it configured.

---

### Post by NikS on 2008-06-28
I alredy trued it, exactly as u said!!!

But, no lead!!
I fed it all the information i had, but still its askin me for MODEM!!! says it couldent find it!!!
Know y??

---

### Post by cariboo on 2008-06-28
Can you post the output of ifconfig and route -n

Jim

---

### Post by prshah on 2008-06-28
> **NikS said:**
> 
Windows IP Configuration
Ethernet adapter Local Area Connection:
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.100.56
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
[color=red]        Default Gateway . . . . . . . . . :[/color]
        DNS Servers . . . . . . . . . . . : 203.187.215.35
                                            203.187.192.12
[color=blue]PPP adapter utele:[/color]



You are connecting through "bridged" mode on your router. 

Open the terminal and type ```
sudo pppoeconf
``` and follow instructions to setup a dial-up connection in bridged mode.

Post back in case of difficulties with relevant output.

---

### Post by NikS on 2008-06-28
ok, what i just tried is:
I dont see the computers connected in the upper right corner of my screen showing connection, thre's an ! mark.
when clicked, it shows "No network devices have been found" as 1st option below which:Manual configuration is shown.
I fed all info i knew into manual configuration.
Now i opened Network Tools: Devices, selected 'Ethernet Interface (eth0)' from the list (Other was Loopback interface (lo)).
When i press configure:It shows:
Interface doesnot exist, check that it is correctly typed and that it is correctly supported by your system!!!


Any Ideas????

---

### Post by NikS on 2008-06-28
Oook,

Now I'l go back n try these commands:
pppoeconf n ifconfig

Thanks..

---

### Post by NikS on 2008-06-29
Here I am!!!

Thanks prshah for that sudo pppoeconf!!!
It worked!!
I could download the UPDATES!!
That means I could connect to net, Right??

But still NOT able to use FIREFOX!!!
It says that either theres no connection or the firefox is in OFFLNE MODE!!!
Now where do I change the mode from?????

Even the computers in the upper right corner dont show connections!!!
(I could download updates!!!, What does that mean????)

Plz Help!!!

---

### Post by sharks on 2008-06-29
type in terminal: sudo pppoeconf 
and configure

---

### Post by NikS on 2008-06-29
Thanks a LOT EVERY1!!!!

M on Ubuntu!!! Online!!!!
My firefox is working!!! (Sorry for asking that stupid question about firefox..)

But hey, the icons still say : No network device has found!!!!!!!


I did configure through sudo pppoeconf, thats how i got the net active!! but the icons!!!1
Hey, Does it matter??
I mean, does this signify something thats gonna cause problem while using net, cause i can, at the moment use net!!!!


M on Ubuntu!!!
M so HAPPY!!!
THANKS, THANKS A LOT!!!!!

:guitar: :lolflag: :guitar: :lolflag: :guitar: :lolflag: 

I think m gonna go crazy!!!

Well, do reply about those connection icons!!

---

### Post by prshah on 2008-06-29
> **NikS said:**
> 
Thanks for sudo pppoeconf!!!
It worked!!

But still NOT able to use FIREFOX!
It says that either theres no connection or the firefox is in OFFLNE MODE! Now where do I change the mode from?????

(I could download updates)


Looks like a DNS server problem. Post the output of this command ```
cat /etc/resolv.conf
```

It should show your DNS server addresses:> DNS Servers . . . . . . . . . . . : 203.187.215.35
203.187.192.12

If it **doesn't** show your dns servers, give the command```

sudo gedit /etc/dhcp3/dhclient.conf
``` Then look for a line starting with > #prepend domain-name-servers (The hash [#] may or may not be there); edit it so that it shows
```

prepend domain-name-servers 203.187.215.35,203.187.192.12;
```

save the file, quit; then give the command ```
sudo /etc/init.d/networking restart
```

==

On the other hand, if your DNS servers are _already_ mentioned in /etc/resolv.conf, then open firefox, click File, and make sure the "Work Offline" option is unchecked/unticked.



> **sharks said:**
> type in terminal: sudo pppoeconf 
and configure

He's been there, done that.

---

### Post by NikS on 2008-06-29
Thanks prshah,

heres the output:
```

niks@Zion:~$ cat /etc/resolv.conf
nameserver 203.187.215.35
nameserver 203.187.192.15
niks@Zion:~$ 

```

Well, it showed the DNS servers, n i can surf as well  now, but the icons still say theres no connection!!!!!!!!!
Y so??

---

### Post by NikS on 2008-06-30
Ok, Now I have reinstalled ubuntu,
I clicked on the connection icons (showin ! mark)
selected manual configration, disabled wireless, entered static ip, gateway addresses, DNS server addresses  etc.
Then i selected Point to Point connection, selected pppoe, entered username, password, selected modem as eth0, enabled EVERYTHING.

now again i can surf, download.
BUT STILL the icons say NO NETWORK CONNECTION!!!!

Why is it so??

---

