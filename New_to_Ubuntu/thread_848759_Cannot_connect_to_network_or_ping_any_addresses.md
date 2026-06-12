---
title: "Cannot connect to network or ping any addresses"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by MrVader101 on 2008-07-03
Hi All

I am brand new to ubuntu have been using it for a little while at home and liked it so much i thought i might stick in on my work computer as well.

I Have just installed the latest version of ubuntu on my work computer 8.04. Only problem is i can not connect to the network. either with a static ip or DHCP i can not get any connectivity. 

I have the sis900 pci ethernet card installed.

any help would be appreciated cheers

---

### Post by iaculallad on 2008-07-03
Post the output of the following terminal commands:

```
cat /etc/hosts
```

and 

```
ifconfig
```

and

```
lspci
```

---

### Post by MrVader101 on 2008-07-03
Wow thanks for the quick reply iaculallad

Now word of warning i have been mucking aroud trying to get the net work going. I dont think that i have done anything to bad though hopefully.

firstly the hosts file 

# The following lines are desirable for IPv6 capable hosts 
::1 ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts 

Here is the ifconfig file

eth0      Link encap:Ethernet  HWaddr 00:11:09:f8:ec:ee  
          inet6 addr: fe80::211:9ff:fef8:ecee/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:77 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:10 Base address:0xd800 

eth0:avahi Link encap:Ethernet  HWaddr 00:11:09:f8:ec:ee  
          inet addr:169.254.11.98  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:10 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2408 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2408 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:120552 (117.7 KB)  TX bytes:120552 (117.7 KB) 

And lastly lscpi 

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11) 
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) 
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25) 
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller 
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] 
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) 
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0) 
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) 
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) 
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller 
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90) 
00:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac) 
00:09.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac) 
00:09.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04) 
00:0e.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05) 
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by iaculallad on 2008-07-03
> **MrVader101 said:**
> 

# The following lines are desirable for IPv6 capable hosts 
::1 ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts 


Is this the whole complete list of what **cat /etc/hosts** displays?

There should be something like the lines of texts below:

> 127.0.0.1 localhost
127.0.1.1 your_computer_name_here


---

### Post by MrVader101 on 2008-07-03
Yeah that's the whole thing.

---

### Post by iaculallad on 2008-07-03
> **MrVader101 said:**
> Yeah that's the whole thing.

Include the texts below as your FIRST line of text on your /etc/hosts file:

```
127.0.0.1 localhost
127.0.1.1 your_computer_name_here
```

Change the value of your_computer_name_here to match your settings. Its the value when you open your terminal:

ian@gutsy-gibbon:~$

In my case, its: **gutsy-gibbon**

EDIT: Then try to restart your network daemon, using your terminal:

```
sudo /etc/init.d/networking restart
```

---

### Post by MrVader101 on 2008-07-03
...if i open the hosts file with gedit /etc/hosts

i get the 2 lines
127.0.0.1 localhost
127.0.1.1 [my computer]

---

### Post by iaculallad on 2008-07-03
> **MrVader101 said:**
> ...if i open the hosts file with gedit /etc/hosts

i get the 2 lines
127.0.0.1 localhost
127.0.1.1 [my computer]

Could you post your terminal prompt:

i.e: **ian@gutsy-gibbon:~$ **

---

### Post by MrVader101 on 2008-07-03
Yeah so the host file currently reads 

127.0.0.1 localhost
127.0.1.1 greg-laptop
 
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 

When i open it for editing 
is that how it should look?

---

### Post by MrVader101 on 2008-07-03
sure thing its

greg@greg-laptop:~$

---

### Post by Dr Small on 2008-07-03
Also, running:
```
hostname
```

Will do the same thing. But basically, you host file should say:
```

127.0.0.1 *your_host_name*
```

---

### Post by iaculallad on 2008-07-03
> **MrVader101 said:**
> sure thing its

greg@greg-laptop:~$

Well, there's no problem with your hosts configuration file. Had you tried placing static IP on your eth0 interface?

System->Administration->Network, on your "Connection" tab, select "Wired Connection" and click on "Properties". Uncheck "Enable Roaming Mode" and select it to use "Static IP Address". Supply your valid IP configuration from there and on the "DNS" tab, supply your DNS server.

---

### Post by MrVader101 on 2008-07-03
Yeah just giving the static ip a go now.....and i am still unable to ping my server or connect to internet etc.

---

### Post by MrVader101 on 2008-07-03
when i go to the network tools i.e. system.administration.network tools

if i click on the eth0 interface and click configure i get the message interface does not exist....is that normal?

---

### Post by Dr Small on 2008-07-03
What is your interface? Are you using Ethernet or Wireless? I assume you are on wireless. If that is the case, then you should be setting ath0 instead.

---

### Post by MrVader101 on 2008-07-03
No i am currently trying to get the wired network up and running. i assume once that is going the wireless will be a similar process for connecting to the network

---

