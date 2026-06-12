---
title: "Internet connect by supplicant in VirtualBox Guest -&gt; sharing internet w/ Ubuntu Host"
date: 2008-09-13
forum: Outdated Tutorials &amp; Tips
---

### Post by bpanahij on 2008-09-13
Hello Ubuntu Users,

I am currently living in the Peoples Republic of China and I am an internet user. I also enjoy tinkering and I wanted to try out Ubuntu again on my latest PC. Well, there was a problem, which I solved, and I would like to share my solution. 

The problem is that my ISP does not provide a linux client for their supplicant protocol. I attempted to use wpa_supplicant, but the ISP uses some kind of proprietary encryption. I tried using Wine to run the supplicant application (a Windows .exe), but that failed due to the inability of wine to properly use the WinPCap application dlls, and a problem with Wine binding to the wrong nic card (I have two installed). The only answer was to install a VM running Windows XP, and to connect from within that. I followed some tutorials on this forum, and I got that working: the Windows XP VM connected to the internet by use of the "EDU Supplicant" (I work for a University here, and the internet is provided by CERNET, a Chinese government owned ISP.). There was one las problem: How do I get internet to my host from my guest VM's connection. 

I found a solution that works very well, and I'd like to give something back to the Ubuntu community. I did some experimenting, for a few hours, and finally I tried one last thing, but I fell asleep while Ubuntu was rebooting. When I woke up, I thought I'd keep trying, so I made sure I sat down, logged into Ubuntu, and what I did just before I fell asleep worked!!!! So here it is for you.

**First, here are my systems specs:**

AMD Athlon 64 5000+ BlackEdition (hehe)
Ubuntu Feisty 7.04 64-Bit-AMD [Edit: Running Hardy 8.04 and still works great]
Two Nic cards (Realtek)
VirtualBox with a stripped down Windows XP virtual machine running

**Here are the connection details**:

Proprietary .exe called "EDU Supplicant", by CERNET
The supplicant sends my MAC address to restrict me to one computer

**So heres how it works:**

I added a bridge, and set my eth0 (where school network is connected) to promiscuos (read on), and added the eth0 to the bridge. Then I used VirtualBox to add a TAP interface and add the TAP (vbox0) it to the bridge.

First set up the network/interfaces file...

Here is the /etc/network/interfaces file:[EDIT New and improved]

> auto lo eth0 eth1 br0 br1
iface lo inet loopback

iface eth1 inet manual
	up ifconfig $IFACE 0.0.0.0 up
       	up ip link set $IFACE promisc on
       	down ip link set $IFACE promisc off
       	down ifconfig $IFACE down

iface eth0 inet static
	address 192.168.0.3
	netmask 255.255.255.0
	gateway 192.168.0.1	

iface br0 inet dhcp
	bridge_ports eth1

iface br1 inet dhcp
	bridge_ports eth0


Now restart networking, type:
> 
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start


Wait for the network to completely restart. You can open another terminal and type ifconfig to check the interfaces. Once you see all of the interfaces in the output of ifconfig, then the interfaces are up.

Now run these commands:

> 
sudo VBoxAddIF vbox0 <username> br0
sudo VBoxAddIF vbox1 <username> br1


Make sure to set the permissions of /dev/net/tun to 066, so that VirtualBox can access the bridges.

> sudo chmod 0666 /dev/net/tun

You can now set up your Virtual Machine in VirtualBox.

**Here is how it works.**
eth0 is set to listen to all lan traffic (promisc), and is then added to br0 (bridge0). Then vbox0 is added to that bridge: when you reboot Ubuntu. 

Next, vbox1 is set to listen to all lan traffic (promisc), and eth1 is set to a static IP on the same subnet as br0, and the Virtual Nic (in XP client). Both vbox1 and eth1 are added to a new bridge: br1.

Now, set up you virtual machine: you must add two nic cards under the network tab. They should be set to "Host interface", any random MAC address, and set the device id to vbox0 and vbox1 respectively for each virtual nic card.

Lastly, boot your virtual machine, install the network card drivers, and set the first one up the way you would set it up if you were just running XP directly on your hardware (not virtualized). For me that means:

static IP address, specified Gateway and DNS addresses: provided by my ISP: CERN (China Education R[*] Network).

To get your supplicant .exe program into the virtual machine just open a file browser, type "burn:///" into the address bar, and hit enter. You can drop any files you want to access in your virtual machine here. Then hit the button on the file browser that says burn, or "write to disk". Create an iso file from the menu that pops up, and mount the iso from within your virtual machine.

Install the supplicant.

Now install your supplicant executable in the windows environment. Check to see that the NIC card is actively sending and receiving packets. You can do this by checking the status of the network in XP. VirtualBox also shows network activity at the bottom right of the VM window. You should see (send and receive) activity even when you have not authenticated with the supplicant. My supplicant is a program called "EDU Supplicant" by CERNET.

Run the Supplicant and set the settings. On mine, I must set an authentication server (within the supplicant program) and select which NIC to use (it seems to prefer NIC2 by default. I want NIC one: vbox0], Then I type in my user name and password in the supplicant exe.

Now try logging in to your ISP. AT this point it should work. If not make sure the Supplicant has you correct login information, and that the virtual nic (within the WinXp virtual client) is set up the way your ISP has instructed. You may need to reboot Ubuntu, to allow networking to properly boot up.

If the connection works, and you have internet in your VM WinXP client, then thank the Gods (watching to much Gallactica!). Now, in the WinXP virtual client right click the vbox0 nic (the one connected to the network and authenticated by supplicant to the network) and select "Properties". Now, click the advanced tab and select "Allow other computer users to connect through this computers internet connection." Then click "Settings" and select the types of services to share (HTTP, FTP, etc...). You only really need to share HTTP, but you can share more if you will it.

Now go to your Ubuntu host and start up Firefox..... you should have internet in the host. Woohooo.


**Troubleshooting**

If you don't have internet at this point, open a terminal and type:

> ifconfig

You should see something like this:

> 
brian@brian-desktop:~$ ifconfig 
br0       Link encap:Ethernet  HWaddr 00:1d:7d:ac:11:6c  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:feac:116c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:412078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36138394 (34.4 MB)  TX bytes:608632 (594.3 KB)

br1       Link encap:Ethernet  HWaddr 00:e0:4c:6a:25:c7  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe6a:25c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:313135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:427873377 (408.0 MB)  TX bytes:22201551 (21.1 MB)

eth0      Link encap:Ethernet  HWaddr 00:e0:4c:6a:25:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1d:7d:ac:11:6c  
          inet6 addr: fe80::21d:7dff:feac:116c/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:3454276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2075389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2989303245 (2.7 GB)  TX bytes:406451615 (387.6 MB)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:386585 (377.5 KB)  TX bytes:386585 (377.5 KB)

vbox0     Link encap:Ethernet  HWaddr 00:ff:a1:d7:d2:03  
          inet6 addr: fe80::2ff:a1ff:fed7:d203/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:291156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:726278 errors:0 dropped:278 overruns:2 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:22456429 (21.4 MB)  TX bytes:476525878 (454.4 MB)

vbox1     Link encap:Ethernet  HWaddr 00:ff:a0:44:ca:da  
          inet6 addr: fe80::2ff:a0ff:fe44:cada/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:313135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289248 errors:0 dropped:13 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:432260325 (412.2 MB)  TX bytes:22195129 (21.1 MB)


If this is not like what you see, then reboot Ubuntu, and try again. Just check the ifconfig after you reboot, and if it looks like this it should work.

You want to see br0, br1, eth0, eth, vbox0, and vbox1

If there is an br0:avahi or br1:avahi, it may interrupt or slow your connection down. I suggest turning of the Multicasting DNS service discovery, because in this setup you won't need it, and it creates the avahi daemons you may see sometimes. Turn the service off by going to the System->Administration->Services, then unlock Service Settings (if in Hardy or later), and uncheck "Multicast DNS service discovery".

There should always be some activity on eth0 and br0. Once you have booted and connected the Supplicant in the Virtual WinXP, all connections should have activity (send and receeive incrementing).

Check the network icon at the bottom of the VirtualBox VM Windows window, make sure there are both green and orange lights blinking. If not, then reboot the Windows VM, and then reboot the Ubuntu Host machine.This networking setup may slow down the boot time. If you want to fix this, then check this out:
[http://blog.dotkam.com/2008/08/06/speed-up-ubuntu-boot-time-by-starting-networking-on-the-background/](http://blog.dotkam.com/2008/08/06/speed-up-ubuntu-boot-time-by-starting-networking-on-the-background/)
It works for me, and I like the cool scripting.

Good luck, and happy hunting.

bpanahij

---

### Post by Bit Hacker on 2010-06-05
Awesome post, just what I've been looking for. I'm trying to use CLEAR Motorola WiMax USB in Ubuntu as there is no support for linux as yet. I've installed windowsxp as guest in ubuntu and the version I'm using is 3.2.2. USB is connecting fine in 
WindowsXP but I can't use internet in Ubuntu. Can you please tell me how to do it. Here is the configuration that could help you guys. Thanks in advance.

I'm using Two Network Adapters.


```
Network
Adapter 1:
PCnet-FAST III (NAT)
Adapter 2:
PCnet-FAST III (Host-only adapter, 'vboxnet0')
```


**ipconfig [on Guest windowsXP]**

```
Windows IP Configuration
Ethernet adapter Local Area Connection:  PCnet-FAST III (NAT)

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 10.0.2.15
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.0.2.2

Ethernet adapter Local Area Connection 3: PCnet-FAST III (Host-only adapter, 'vboxnet0')

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.56.101
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection 2: 

        Connection-specific DNS Suffix  . : CLEAR Motorola USB
        IP Address. . . . . . . . . . . . : 10.168.242.33
        Subnet Mask . . . . . . . . . . . : 255.255.192.0
        Default Gateway . . . . . . . . . : 10.168.192.2
```


**IFCONFIG [on Host Ubuntu]**

```
Code: Select all   Expand viewCollapse view
(Ethernet) eth0      Link encap:Ethernet  HWaddr 00:14:22:b9:9d:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1    (Wireless) Link encap:Ethernet  HWaddr 00:13:ce:f0:9b:0d  
          inet6 addr: fe80::213:ceff:fef0:9b0d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:84 (84.0 B)
          Interrupt:17 Base address:0xe000 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:171952 (171.9 KB)  TX bytes:171952 (171.9 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          inet addr:192.168.56.1  Bcast:192.168.56.255  Mask:255.255.255.0
          inet6 addr: fe80::800:27ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:21174 (21.1 KB)
```

---

