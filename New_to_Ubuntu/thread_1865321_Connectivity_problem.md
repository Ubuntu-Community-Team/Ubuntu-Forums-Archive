---
title: "Connectivity problem"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by katsandcards on 2011-10-20
Hi. I am new to Linux and Ubuntu. I had an old HP 6642F desktop that wasn't being used and thought I'd try the Linux Operating system. I installed Ubuntu 11.1 and everything seems to have loaded properly. It is the only OS on the machine now. My problem is with getting onto the internet. I have cable internet service. I have a small  home network with 3 Windows computers (and a Xbox). I have a Leviton 4 port gateway and Leviton 8 port switch. All rooms are hardwired. I've looked at a million posts on different websites trying to figure out the problem. Can Linux and Windows go through the same router/gateway? When I run sudo ppoeconf It scans eth1 and I get a message "sorry I scanned one interface, but the Access Concentrator of your provider did not respond. please check cables etc."   I would appreciate any help in this matter.  :confused:

---

### Post by Grenage on 2011-10-20
Hello there,

Routers/gateways are OS-agnostic; they're only interested in TCP/IP/etc, so there should be no problem.  I assume that the machines get their IP address from the gateway, so is your Ubuntu install receiving one?  Type this in, and post the results:

```
ifconfig
```

I don't believe it now needs root rights, but if you get nothing back, just prefix the command with *sudo*.

---

### Post by 3rdalbum on 2011-10-20
You should just be able to plug the computer in, and then go to the Network Manager indicator at the top of your screen and choose "Wired Connection 1" (or similar) from the menu.

What happens when you try this? Please be as descriptive as possible.

You shouldn't need pppoe - your router will handle this, not the computer.

---

### Post by varunendra on 2011-10-21
If you need an ID-Password to get connected, you may easily configure this in Network Manager as this video shows: [http://www.youtube.com/watch?v=Dx-G-Sn6IhY](http://www.youtube.com/watch?v=Dx-G-Sn6IhY) [the network manager icon is changed to a conical shape in Natty onwards]

---

### Post by katsandcards on 2011-10-21
> **Grenage said:**
> Hello there,

Routers/gateways are OS-agnostic; they're only interested in TCP/IP/etc, so there should be no problem.  I assume that the machines get their IP address from the gateway, so is your Ubuntu install receiving one?  Type this in, and post the results:

```
ifconfig
```

I don't believe it now needs root rights, but if you get nothing back, just prefix the command with *sudo*.
Linux:-$ ifconfig ```

Link encap:Local Loopback 
inet addr127.0.0.1  Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING  MTU:16436 Metric:1 
RX packets 936 errors:0 dropped:0 overruns:0 frame:0  
TX packets:936 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0  txqueeuelen:0 
RX bytes:75624 (75.6 kb) TX bytes:75624 (75.6 kb)
```

---

### Post by katsandcards on 2011-10-21
> **3rdalbum said:**
> You should just be able to plug the computer in, and then go to the Network Manager indicator at the top of your screen and choose "Wired Connection 1" (or similar) from the menu.

What happens when you try this? Please be as descriptive as possible.

You shouldn't need pppoe - your router will handle this, not the computer.
When I click on the network manage, edit connections is my only option I chose the wired connections tab It shows Wired connection 1 I close manager and no connection can be made.

---

### Post by Iowan on 2011-10-21
**ifconfig -a** should show all interfaces - active or not. The info you posted looks like the loopback (lo) is the only interface - *probably* meaning no IP address for network card (eth?).

I haven't yet installed 11.10, but I presume the CLI stuff should work the same...

---

### Post by varunendra on 2011-10-22
> **Iowan said:**
> **ifconfig -a** should show all interfaces - active or not. The info you posted looks like the loopback (lo) is the only interface - *probably* meaning no IP address for network card (eth?).

I haven't yet installed 11.10, but I presume the CLI stuff should work the same...
I can confirm it is still the same :)

@*katsandcards*,
Please post a detailed description of how you connect to it in your windows machines. And the outputs of following:
```
ifconfig -a
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```
Did you try the method shown in the video I linked to?

---

### Post by katsandcards on 2011-10-23
(ifconfig -a)   eth1  Link encap:Ethernet HWaddr 00:1a:70:14:10:e4  BROADCAST MULTICAST MTU:1500 Metric:1 RX packets:0 errors:0 dropped:0  overruns:0 frame:0 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  collisions:0 txqueuelen:1000 RX bytes:0 (0.0B) TX bytes:0 (0.0 B)  Interrupt:9 Base  address:0x3000                                                                                    lo                Link encap:Local Loopback inet addr:127.0.0.1  Mask:255.0.0.0 inet6 addr: ::1/128 Scope:Host UP LOOPBACK RUNNING  MTU:16436 Metric:1 RX packets:112 errors:0 dropped:0 overruns:0 frame:0  TX packets:112 errors:0 dropped:0 overruns:0 carrier:0 collisions:0  txqueuelen:0 RX bytes:8880 (8.8KB) TX bytes:8880  (8.8KB).............................................................................................                                                                                                                                                                                                                                                                                                                    (cat /etc/network/interfaces)    auto lo iface lo inet  loopback.........................................................................                                                                                                                                                    (cat  /etc/NetworkManager/NetworkManager.conf)       [main]  plugins=ifupdown,keyfile  no-auto-default=00:06:4f:5f:04:22,    [ifupdown] managed=false .............................................................................             Yes, I watched the video, already tried and it didn't  work. As far as the windows machines, Cable to modem, modem to gateway, gateway to switch, switch, to all RJ45 jacks in the house. I simply plug ethernet cable from  computers into ethernet switch recepticle and it automatically connects.

---

### Post by Grenage on 2011-10-24
To quickly rule out hardware and router config (well, mostly), do you get an IP if you boot from a live/Install CD?

---

### Post by varunendra on 2011-10-24
katsandcards,
First off, please make it a habit to always wrap your outputs in 'code' tags as you did in post#5 for ifconfig. You can see the difference yourself ;)

Anyway, I'm doing it here myself for sake of readability:
```
**ifconfig -a**
eth1    Link encap:Ethernet HWaddr 00:1a:70:14:10:e4[INDENT] BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0  overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0B) TX bytes:0 (0.0 B)
Interrupt:9 Base  address:0x3000
[/INDENT]lo        Link encap:Local Loopback[INDENT] inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436 Metric:1
RX packets:112 errors:0 dropped:0 overruns:0 frame:0
TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
collisions:0  txqueuelen:0
RX bytes:8880 (8.8KB) TX bytes:8880 (8.8KB)[/INDENT]
``````
**cat /etc/network/interfaces**
auto lo
iface lo inet  loopback

**cat  /etc/NetworkManager/NetworkManager.conf**
[main]  plugins=ifupdown,keyfile

[COLOR=Red]**no-auto-default=00:06:4f:5f:04:22**[/COLOR]

[ifupdown]
managed=false
```
The line highlighted in red means your wired connection is set to **Not set to 'Connect Automatically**' in Network Manager. In this case, right-click on the Network-Manager icon on the upper panel and make sure 'Enable Networking' has a tick mark beside it in the drop down menu. Then you should be able to see a default connection name (most probably "Auto eth0") under 'Wired Connection' section of the same menu. Just click on it and you should get connected.

To make it connect automatically each time you start computer, do the following:
Right-click on the Network-Manager icon > Edit Connections > goto 'Wired' tab > double click (or select > edit) the default connection name in the list > check the "Connect automatically" checkbox > close

If this doesn't help, please open command prompt in one of your windows machines (click **run** in Start menu > type **cmd** > press Enter), and enter this command:
```
ipconfig /all > C:\ipconfig.txt
```This will create a file "ipconfig.txt" in your C: drive in windows. Just copy-paste its contents in your next post (and don't forget to wrap it in 'code' tags ;))

Lets hope clicking "Auto eth0" is all you need :)

---

### Post by katsandcards on 2011-10-25
My only option when clicking on the network manager is "edit connections" the other choices are not highlighted. When I chose edit connections, I then chose the wired tab. The only connection is described as wired connection 1.     Sorry for the ignorance, but I didn't know how to access the "code tags".   The Iowan was gracious and edited my previous post. I appreciate your help.                                                                                                                               > Windows IP Configuration
 
        Host Name . . . . . . . . . . . . : firstbuild2000
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
 
Ethernet adapter Local Area Connection:
 
        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : Realtek RTL8169/8110 Family Gigabit Ethernet NIC
        Physical Address. . . . . . . . . : 00-01-08-00-9D-A8
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.2
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 74.128.17.114
                                            74.128.19.102
        Lease Obtained. . . . . . . . . . : Monday, October 24, 2011 2:02:40 PM
        Lease Expires . . . . . . . . . . : Thursday, October 27, 2011 2:02:40 PM

---

### Post by varunendra on 2011-10-25
Does it look like this:

[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Natty-NM-Disabled.jpg[/IMG]

If so, click on "Enable Networking". If even this option is not highlighted, try this command in a terminal:
```
sudo /etc/init.d/networking restart
```
Then see if it is highlighted as the following screenshot:

[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Natty-NM-Enabled.jpg[/IMG]

If it is, clicking on "Wired connection 1" may get you connected because as per the windows output, DHCP is enabled on your network.

However, if just clicking on it does not get you connected (it sometimes happens due to dhcp errors), you may have to fill in the configuration details manually by 'editing' "Wired Connection 1", something like this screenshot shows:

[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Ubuntu-2010-08-14-02-40-43.png[/IMG]

Replace Address, Netmask, Gateway and DNS with following details (obtained in your windows output)
> IP Address. . . . . . . . . . . . : **192.168.0.2** *(Address)*
        Subnet Mask . . . . . . . . . . . : **255.255.255.0*** (Netmask)*
        Default Gateway . . . . . . . . . : **192.168.0.1** *(Gateway)*
DNS Servers . . . . . . . . . . . : **74.128.17.114**, **74.128.19.102**


And no problem with the code-tag unfamiliarity. Everyone has a starting point :). To wrap any output in code tags, just click on the **#** symbol at the top of the edit box in which you write your posts (just beside the 'quote' tag button you are currently using). This will automatically generate [noparse]```
..and..
```[/noparse] tags. Then just copy-paste the outputs between these tags using your mouse cursor. An example:

Code without tags will appear like this:
"code without tags"

After you add code tags like this:
[noparse]```
"code with tags"
```[/noparse]

it will look like this in the post:
```
"code with tags"
```

Oh, by the way, your attempt with the 'quote' tags is appreciable. Almost exactly there :)

---

### Post by katsandcards on 2011-10-26
```
sudo /etc/init.d/networking restart
```    That did the trick! Thanks so much, I really appreciate the help.

---

### Post by varunendra on 2011-10-26
> **katsandcards said:**
> That did the trick!
Love to hear that!! :)
And you're most welcome.

---

