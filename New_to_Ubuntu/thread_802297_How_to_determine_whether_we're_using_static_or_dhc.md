---
title: "How to determine whether we're using static or dhcp"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-21
Hello, actually I would like to setup static ip for my machine. but when I type this code 
$ sudo nano /etc/network/interfaces
i get this quote 
auto lo
iface lo inet loopback

i dont know whether my sys using static(i have setup static ip for Utorrent in XP before i use Ubuntu).wonder if the setting remain unchanged) or dhcp. Another issue is, how do i get my current setting for; 

=> Host IP address
=> Netmask: 
=> Network ID: 
=> Broadcast IP:
=> Gateway/Router IP: 
=> DNS Server:

just for precaution in case i mess up later on

i would like follow this instruction to setup static ip;
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by pricetech on 2008-05-21
If that's the entire content of your interfaces file, your NIC isn't set up.
List your hardware so folks can see what you  have to work with.
Consider installing an extra NIC.  (might be easier and quicker than trying to make an incompatible NIC work)  Use an older NIC if you can put your hands on one, such as 3Com 3c905 or Realtek 8139 chipset.

Once you have a working NIC, then setting up your network should be a piece of cake, doable through the GUI based tools.

Good Luck.

---

### Post by wariskampar on 2008-05-21
maybe i dont get it but why should i install another nic. i browse internet with my machine now if that can prove that my current nic is ok. Btw, here is the NIC in my sys(get from lshw) 
 *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:06:07.0
                logical name: eth0
                version: 10

what else should i do?

---

### Post by pdtpatrick on 2008-05-21
can you provide more information please? 

ifconfig and display what message you are getting so we can proceed from there. When you set static.. what other settings did you put in? Maybe you missed other settings?

---

### Post by wariskampar on 2008-05-21
Hello, i'm sorry but you're right. when i go to Admin>Network Tools, found that my eth0 not exist (The interfaces does not exit!). All this while i'm actually using loopback interface(lo). How this could happen and what should I do to enable my eth0

---

### Post by wariskampar on 2008-05-21
Hello, i'm sorry but you're right. when i go to Admin>Network Tools, found that my eth0 not exist (The interfaces does not exit!). All this while i'm actually using loopback interface(lo). How this could happen and what should I do to enable my eth0

---

### Post by wariskampar on 2008-05-21
First of all, sorry for double post. My son keeps bordering me:). Now I just manually select Wired Connection in Network Setting. For the time being i just use DHCP to test whether my eth0 funtioning or not. Below is my ifconfig 

aznan@aznan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:d2:f0:44  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fed2:f044/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1677935 errors:9 dropped:15 overruns:9 frame:0
          TX packets:1723737 errors:0 dropped:0 overruns:2 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:993596257 (947.5 MB)  TX bytes:679676462 (648.1 MB)
          Interrupt:21 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:15:00:01:b5:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 Memory:b0106000-b0106fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3911 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:349121 (340.9 KB)  TX bytes:349121 (340.9 KB)

What should I next?

---

### Post by stchman on 2008-05-21
> **wariskampar said:**
> Hello, actually I would like to setup static ip for my machine. but when I type this code 
$ sudo nano /etc/network/interfaces
i get this quote 
auto lo
iface lo inet loopback

i dont know whether my sys using static(i have setup static ip for Utorrent in XP before i use Ubuntu).wonder if the setting remain unchanged) or dhcp. Another issue is, how do i get my current setting for; 

=> Host IP address
=> Netmask: 
=> Network ID: 
=> Broadcast IP:
=> Gateway/Router IP: 
=> DNS Server:

just for precaution in case i mess up later on

i would like follow this instruction to setup static ip;
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

Just go to System--->Network

When that comes up go to the adapter and select Properties.

After that drop down the menu that says Static IP.

After that fill in the blanks.

IP - Pick one outside your router's DHCP
Subnet Mask - usually 255.255.255.0
Gateway - IP of your router usually 192.168.1.1

After that Network Manager will reconfigure your interface and you will be given a static IP behind your router.

I do not believe that you can have static IP with wireless connection running encryption.  Although your router will always assign the same IP to the same MAC address.

---

### Post by pricetech on 2008-05-21
Looks like your ETH0 is working just fine.  Your ETH1 I'm guessing is a wireless since it appears to be a laptop.

Let's concentrate on ETH0 and leave ETH1 out of the discussion for now.

System -> Administration -> Network should open your network applet.

Click the Unlock button and enter your password when prompted.

Click on ETH0 and click properties.  It may be hard to tell which is which before you click on the properties button, but the title bar of the screen that comes up will show which NIC you're working with.

Uncheck Use Roaming Mode and that will allow you to select Static IP Address next to Configuration.

From there you can put in the IP configuration you need:
For IP address, use an address that's not given out by your router, or whatever is handing out IP addresses via DHCP.
For Subnet Mask, use the same 255.255.255.0 that it's currently using.
For Gateway use the IP address of your router, probably either 192.168.1.1 or 192.168.1.254
Click on the DNS tab and you should see some DNS servers listed.  Jot those down in case you have to reenter them, though they should remain listed.

Hope this helps.

P.S. You might have to stop and restart the interface after you make the changes by unchecking the box next to the interface and then rechecking it.

---

### Post by wariskampar on 2008-05-21
Thanks guy. I think the instructions are pretty easy to follow. If I setup static ip now, does it remain as it is when i reboot or i need to re-setup

---

### Post by pdtpatrick on 2008-05-21
So i guess your question was answered? You're using DHCP and you were able to activate your card.. 

you can also set static ip via the terminal, that would be an assignment to work on if you wanted to :)

---

### Post by wariskampar on 2008-05-21
Yeah! I think i can manage that. Matter of fact, i already find the appropriate website to assist me on. Thanks to all:)

---

