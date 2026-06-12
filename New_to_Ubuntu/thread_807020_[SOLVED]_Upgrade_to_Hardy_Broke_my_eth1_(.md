---
title: "[SOLVED] Upgrade to Hardy Broke my eth1 :("
date: 2008-05-25
forum: New to Ubuntu
---

### Post by BassKozz on 2008-05-25
I just upgraded using the "Update Manager" to Hardy Heron (8.04) from Fiesty (7.10), and now my eth1 card is down?
When I go in to the network tools and try and configure it I get the following error message:
> **The interface does not exist**
Check that it is correctly typed and that it is correctly supported by your system.
I've tried moving the ethernet cable ot eth0 also and that doesn't work either :(
Also tried ```
sudo /etc/init.d/networking restart
```
Doesn't help either :(

How can I fix?
Thanks in advance,
-BassKozz

---

### Post by quelx on 2008-05-25
what does ```
ifconfig
``` show you when run from a terminal window? Paste the result in CODE tags for easy reading.

While your at it post your ```
cat /etc/network/interfaces
``` also.

---

### Post by BassKozz on 2008-05-25
> **quelx said:**
> what does ```
ifconfig
``` show you when run from a terminal window? Paste the result in CODE tags for easy reading.

I wish I could paste the results of that into here, but I can't because networking is down (I am on another terminal typing this), so I can't SSH into it to run the command, and when I run the command locally there is no way for me to copy the information from the terminal into a working terminal (w/ networking)...

**EDIT**:I manually typed in this information:
```

br0  Link encap: Ethernet HWaddr {MAC of eth1 HERE}
     inet addr: 192.168.**.*** B cast:192.168.**.255 Mask: 255.255.255.0
     inet6 addr: fe80::250:8bff:****:****/64 Scope:Link
     UP BROADCAST MULTICAST MTU: 1500 Metric: 1
     RX packets:304 errors:0 dropped:0 overruns:0 frame:0
     TX packets:201 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:34213 (33.4KB) TX bytes:18925 (18.4KB)
     Interrupt:22 Base address:0x4000

eth0 {I didn't copy/type this in - irrelevant}

eth1 Link encap: Ethernet HWaddr {MAC HERE}
     inet addr: 192.168.**.*** B cast:192.168.**.255 Mask: 255.255.255.0
     inet6 addr: fe80::250:8bff:****:****/64 Scope:Link
     UP BROADCAST MULTICAST MTU: 1500 Metric: 1
     RX packets:859 errors:0 dropped:0 overruns:0 frame:0
     TX packets:507 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:92078 (89.9KB) TX bytes:68438 (66.8KB)
     Interrupt:22 Base address:0x4000

lo   Link encap: Local Loopback
     inet addr: 127.0.0.1 Mask: 255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOPBACK RUNNING MTU:16436 Metric: 1
     RX packets:1986 errors:0 dropped:0 overruns:0 frame:0
     TX packets:1986 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:106276 (103.7KB) TX bytes:106276 (103.7KB)

vbox0 Link encap: Ethernet HWaddr: {MAC Address}
     inet6 addr: fe80::2ff:****:****:****/64 Scope:Link
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:195 overruns:0 carrier:0
     collisions:0 txqueuelen:500
     RX bytes:0 (0KB) TX bytes:0 (0KB)
```
**_EDIT2_**:
*-I blocked out certain info for security reasons
{}-notes I made
I didn't enter in the eth0 port info because it is irrelevant, because I am only using port eth1 connected to my router via cat5 cable.

---

### Post by BassKozz on 2008-05-25
> **quelx said:**
> While your at it post your ```
cat /etc/network/interfaces
``` also.
```
auto lo
iface lo inet loopback
auto br0
iface br0 inet dhcp
     bridge_ports eth1
```

---

### Post by quelx on 2008-05-25
Try changing **eth1** to **eth0** in the **/etc/network/interfaces**

```
sudo nano -w /etc/network/interfaces
```

**CTRL-X** to save and exit, then

```
sudo /etc/init.d/networking restart
```

Do you mean to have a bridge created?  I think a second port is supposed to be indicated, maybe **eth1** should read **eth0 eth1**

---

### Post by BassKozz on 2008-05-25
> **quelx said:**
> Try changing **eth1** to **eth0** in the **/etc/network/interfaces**

```
sudo nano -w /etc/network/interfaces
```

**CTRL-X** to save and exit, then

```
sudo /etc/init.d/networking restart
```

Do you mean to have a bridge created?  I think a second port is supposed to be indicated, maybe **eth1** should read **eth0 eth1**

No I am not using eth0 (no cat5 connected), so I didn't copy that information from 'ifconfig' results because it is irrelevant... I have my Ethernet cat5 cable connected to only the eth1 port.

---

### Post by quelx on 2008-05-25
Ok, well your bridge isn't bridging anything, your virtual box adapter needs to be adapted and for some reason eth1 is still picking up an address.  For troubleshooting purposes make your **/etc/network/interfaces** look like this

```
auto lo
iface lo inet loopback
auto br0
#iface br0 inet dhcp
#     bridge_ports eth1
iface eth1 inet dhcp

```

and restart networking

---

### Post by BassKozz on 2008-05-25
> **quelx said:**
> Ok, well your bridge isn't bridging anything, your virtual box adapter needs to be adapted and for some reason eth1 is still picking up an address.  For troubleshooting purposes make your **/etc/network/interfaces** look like this

```
auto lo
iface lo inet loopback
auto br0
#iface br0 inet dhcp
#     bridge_ports eth1
iface eth1 inet dhcp

```

and restart networking

That did the trick, network is back up...
After reset I got the following:
```
sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...
Ignoring unknown interface br0=br0.

```

Now what, can I just leave it as is:
```
auto lo
iface lo inet loopback
auto br0
#iface br0 inet dhcp
#     bridge_ports eth1
iface eth1 inet dhcp

```???

---

### Post by quelx on 2008-05-25
If you don't need the bridge (were you using virtualbox or something?) then you can comment out the **auto br0** also by placing a **#** before that line (I don't like to delete stuff from config files, too often I've found I come back to them and wonder what I did months ago and I've removed all the old lines).

---

### Post by BassKozz on 2008-05-25
Well I just restarted my machine, and after restart the network was down AGAIN using:
```
auto lo
iface lo inet loopback
auto br0
#iface br0 inet dhcp
#    bridge_ports eth1
iface eth1 inet dhcp
```
So I went back in and changed "/etc/network/interfaces" back to:
```
auto lo
iface lo inet loopback
auto br0
iface br0 inet dhcp
    bridge_ports eth1
#iface eth1 inet dhcp
```
and its working now?
Weird:confused:

---

### Post by quelx on 2008-05-25
There must be some other script controlling the bridge interface, if it's working after reboots, I guess just roll with it.  Keep that other line around so you have something to go back to.

---

### Post by BassKozz on 2008-05-25
> **quelx said:**
> There must be some other script controlling the bridge interface, if it's working after reboots, I guess just roll with it.  Keep that other line around so you have something to go back to.

I just rebooted again, and the same thing happened, but this time I reverted from:
```
auto lo
iface lo inet loopback
auto br0
iface br0 inet dhcp
    bridge_ports eth1
#iface eth1 inet dhcp
```
to:
```
auto lo
iface lo inet loopback
auto br0
#iface br0 inet dhcp
#    bridge_ports eth1
iface eth1 inet dhcp
```
And now the network is back up again...
What's going on with this?

---

### Post by BassKozz on 2008-05-25
Every time I reboot I need to switch this around and do a "sudo /etc/init.d/networking restart" to get my network back :confused:

---

### Post by quelx on 2008-05-25
What did you setup the bridge for in the first place?

I can only guess VirtualBox

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

What created the bridge in the first place?  Do you still need it?  There is a init script that is monkeying with your networking on boot.  If you can track down that script you can edit it or get rid of it all together.  Are there any unsusual scripts in **/etc/init.d/** (take a look at the creation times)?

---

### Post by BassKozz on 2008-05-25
> **quelx said:**
> What did you setup the bridge for in the first place?

I can only guess VirtualBox

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

What created the bridge in the first place?  Do you still need it?  There is a init script that is monkeying with your networking on boot.  If you can track down that script you can edit it or get rid of it all together.  Are there any unsusual scripts in **/etc/init.d/** (take a look at the creation times)?
I just uninstalled (COMPLETELY REMOVED) VirtualBox from synaptic, because I am now using VMware anyways. And I am still getting the same results...
I poked around **/etc/init.d/** but at first glance I couldn't find the culprit, is there a search command I can preform on the **/etc/init.d/** directory to find anything pertaining to "networking", that might help me find the script that is causing these problems?

I find it very odd that everytime I reboot I have to switch/revert the ***/etc/network/interfaces*** settings back and forth.:confused:

---

### Post by quelx on 2008-05-25
If you didn't make any other changes for your VirtualBox installation try ```
sudo dpkg --purge virtualbox
``` or virtualbox-ose depending on which one you installed.

---

### Post by BassKozz on 2008-05-25
> **quelx said:**
> If you didn't make any other changes for your VirtualBox installation try ```
sudo dpkg --purge virtualbox
``` or virtualbox-ose depending on which one you installed.
```
$ sudo dpkg --purge virtualbox
dpkg - warning: ignoring request to remove virtualbox which isn't installed.
```
I already "completely removed" it.

---

### Post by BassKozz on 2008-05-25
;bump;
anyone have any incite on this?

---

### Post by fwre01 on 2008-05-26
> **B/-\ssKozz said:**
> I just uninstalled (COMPLETELY REMOVED) VirtualBox from synaptic, because I am now using VMware anyways. And I am still getting the same results...
I poked around **/etc/init.d/** but at first glance I couldn't find the culprit, is there a search command I can preform on the **/etc/init.d/** directory to find anything pertaining to "networking", that might help me find the script that is causing these problems?

I find it very odd that everytime I reboot I have to switch/revert the ***/etc/network/interfaces*** settings back and forth.:confused:

you could use "grep -r interface /etc/init.d/" to find any files containing the word interface. Are you still using the bridge interface? or did you remove it when you de-installed virtual box?

---

### Post by BassKozz on 2008-05-26
> **fwre01 said:**
> you could use "grep -r interface /etc/init.d/" to find any files containing the word interface.
```
~$ grep -r interface /etc/init.d/
/etc/init.d/networking:# Short-Description: Raise network interfaces.
/etc/init.d/networking:	log_action_begin_msg "Configuring network interfaces"
/etc/init.d/networking:	    log_warning_msg "not deconfiguring network interfaces: network shares still mounted."
/etc/init.d/networking:	log_action_begin_msg "Deconfiguring network interfaces"
/etc/init.d/networking:	log_action_begin_msg "Reconfiguring network interfaces"
/etc/init.d/dhcdbd:# Description:       dhcdbd provides a D-DBus interface to dhclient,
/etc/init.d/wpa-ifupdown:# Description:		Run ifdown on interfaces authenticated via
/etc/init.d/wpa-ifupdown:#			network interface authenticated via a wpa_supplicant
/etc/init.d/wpa-ifupdown:		log_daemon_msg "Stopping wpa_action roaming interfaces"
/etc/init.d/wpa-ifupdown:		log_daemon_msg "Stopping wpa_supplicant interfaces"
/etc/init.d/hal:        # should keep this in place until hal offers a native interface for
/etc/init.d/waitnfs.sh:#                    interfaces are brought up; this script waits for
```
I don't think theres anything there that could be causing this...

> **fwre01 said:**
> Are you still using the bridge interface? or did you remove it when you de-installed virtual box?

Well, I am not sure... because I am using VMware I don't know if VMware needs that bridge or not?
Which lines should I try removing from ***/etc/network/interfaces***:
```
auto lo
iface lo inet loopback
auto br0
#iface br0 inet dhcp
#    bridge_ports eth1
iface eth1 inet dhcp
```

---

### Post by fwre01 on 2008-05-26
I would suggest changing it to look more like this

> auto lo
iface lo inet loopback

# auto br0
# iface br0 inet dhcp
# bridge_ports eth1

auto eth1
iface eth1 inet dhcp

i dont know if VMware uses the bridge interface, but most of it was already commented out in your interfaces file anyway. change your interfaces file (take a backup) and restart networking "sudo /etc/init.d/networking restart" and see if your eth1 grabs a DHCP lease. and see if VMware still networking still works

check to see if you are still using the bridge, (you should able to see it from "ifconfig" or "brctl show" will show all the interfaces that the br0 is bridging)

i appologise......iv kinda lost track of what the problem was in the first place. You cudnt see one of your nics? do u want to use both your nics?

---

### Post by BassKozz on 2008-05-26
> **fwre01 said:**
> I would suggest changing it to look more like this
```
auto lo
iface lo inet loopback

# auto br0
# iface br0 inet dhcp
# bridge_ports eth1

auto eth1
iface eth1 inet dhcp 
```

i dont know if VMware uses the bridge interface, but most of it was already commented out in your interfaces file anyway. change your interfaces file (take a backup) and restart networking "sudo /etc/init.d/networking restart" and see if your eth1 grabs a DHCP lease. and see if VMware still networking still works
Nope that didn't work, I tried using this and my connection was down after **sudo /etc/init.d/networking restart** :(
> **fwre01 said:**
> 
check to see if you are still using the bridge, (you should able to see it from "ifconfig" or "brctl show" will show all the interfaces that the br0 is bridging)
**_ifconfig:_**
```

br0       Link encap:Ethernet  HWaddr {MAC Address}
          inet addr:192.168.**.***  Bcast:192.168.**.255  Mask:255.255.255.0
          inet6 addr: fe80::250:****:****:****/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13175006 (12.5 MB)  TX bytes:16721617 (15.9 MB)

eth0      Link encap:Ethernet  HWaddr {MAC Address}
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr {MAC Address}
          inet6 addr: fe80::250:****:****:****/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16170757 (15.4 MB)  TX bytes:17819164 (16.9 MB)
          Interrupt:22 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:122817 (119.9 KB)  TX bytes:122817 (119.9 KB)

vmnet1    Link encap:Ethernet  HWaddr {MAC Address}
          inet addr:192.168.***.*  Bcast:192.168.***.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr {MAC Address}
          inet addr:192.168.***.*  Bcast:192.168.***.255  Mask:255.255.255.0
          inet6 addr: fe80::250:****:****:*/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
Interesting "vbox" is gone (now that I've completely removed VirtualBox, and "vmnet" seems to be my VMware virtual machines (I currently have 2 of them running)...

**_brctl show:_**```
bridge name	bridge id		STP enabled	interfaces
br0		8000.00508db55ea0	no		eth1
```
> **fwre01 said:**
> 
i appologise......iv kinda lost track of what the problem was in the first place. You cudnt see one of your nics? do u want to use both your nics?
No I am **_ONLY_** using *eth1* nothing is connected to *eth0*... I have my cat5 connected to eth1 only.

---

### Post by fwre01 on 2008-05-26
i think the interface went down becasue we kinda pulled the br0 config out from underneath it by commenting it out. to properly remove a bridge interface ur supposed to use ```
 delbr br0 
``` but its probably best to remove eth1 from the bridge first with ```
 delif br0 eth1 
```

i dont think theres any need to have this now your running VMware, its prob just causing more problems. ....even tho your output from ifconfig would suggest theres nothing wrong with the bridge interface

---

### Post by BassKozz on 2008-05-26
IT's FIXED...

I used fwre01's settings ```
auto lo
iface lo inet loopback

# auto br0
# iface br0 inet dhcp
# bridge_ports eth1

auto eth1
iface eth1 inet dhcp
```
and I rebooted my machine (it wasn't working before because I didn't reboot), and it's all fixed and working :D
Both my ubuntu system and my VMware virtual machines are all working in harmony...
Thanks fwre01 =D>

---

