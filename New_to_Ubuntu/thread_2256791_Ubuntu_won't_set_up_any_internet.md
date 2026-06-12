---
title: "Ubuntu won't set up any internet"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by nick70 on 2014-12-14
Okay, long story short, I've been trying to install drivers, some of them for wifi cards/adapters and some for other things. But, the CDs that have the drivers for my wifi cards/adapters don't have Linux drivers. So I was using Wine to try to get them working (wrong idea, done with that), but I couldn't get Wine setup without downloading things on my other computer and transferring them over; and even that wasn't working. 

That wasn't very short, but whatever. So, my computer is upstairs, which is about as far away from my router as possible; which is why I use a wifi card/adapter. I also don't feel like winding a 60 foot ethernet cable down the stairs just to get internet. So, I resolved to bring my computer downstairs, use a short ethernet cable to setup the drivers for my wifi then move back upstairs. 

But, when I plugged in my computer to ethernet, it didn't do anything. No automounting, no "do you want to join/setup this network", no nothing. Even when I clicked on "Wired Connection", it doesn't connect.

I realize that I haven't given you much information to go off of, but I'm wondering why this happens and how I can fix it. Is it that I need to install motherboard drivers before I can use the Ethernet port correctly? I am running on an **AMD FX-8320 **and a **GIGABYTE 990-FXA-UD3**, if that helps anyone. And I don't think that the disk that came with the motherboard came with Linux drivers. Keep in mind that I am a pretty new person to Linux; I have some experience with command line but that's about it.

Thanks for anyone's help,

-Nick

---

### Post by Frogs Hair on 2014-12-14
Hello , nick70

Please open the terminal in Ubuntu and run the following command and copy and paste the output here. ```
lspci
``` The command will provide information about your wireless card which will be a starting point. below is an example from my computer.  

```
24:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
```


You can write down the network controller info which should be near the bottom of the terminal output since you have no internet on Ubuntu.

---

### Post by ian-weisser on 2014-12-14
[edit]Frogs Hair beat me to it. Well done.

---

### Post by nick70 on 2014-12-14
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02) 
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B) 
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H) 
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx1 port A) 
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40) 
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller 
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller 
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller 
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller 
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42) 
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40) 
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40) 
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40) 
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40) 
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller 
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) 
00:15.3 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3) 
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller 
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller 
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0 
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1 
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2 
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3 
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4 
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5 
01:00.0 VGA compatible controller: NVIDIA Corporation GK106 [GeForce GTX 660] (rev a1) 
01:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1) 
02:00.0 USB controller: VIA Technologies, Inc. Device 3483 (rev 01) 
03:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11) 
04:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) 
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06) 
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter (rev 01)
```


So, I'm using a netis WiFi card with a Realtek chipset (obviously). Also, I would prefer to use my WiFi adapter, which is a USB NETGEAR A6200 because it has a faster connection and is a bit more reliable, at least on Windows.


Again, neither of these (the card or the adapter) came with Linux drivers. Well, the card did, but I can't seem to figure out how to make them work (they're just sort of in a folder buried deep in the CD under a bunch of different version names; no executable).

---

### Post by nick70 on 2014-12-16
I hope I'm not violating any rules by bumping this. Just to make sure, here's my ifconfig, even though it probably doesn't help:

```
eth0      Link encap:Ethernet  HWaddr 74:d4:35:04:7b:e8             UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 


lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:65536  Metric:1 
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:12225 (12.2 KB)  TX bytes:12225 (12.2 KB) 
```

---

### Post by QIII on 2014-12-16
You are most certainly not breaking any rules!  You don't need to wait two days.  You don't even have to wait 24 hours like we used to ask.  Of course if you bump every hour we'll send you packing.  :)

You're good.

---

### Post by spiffymoo on 2014-12-16
if You can find an Ethernet connection to get online. Ubuntu should automatically find the drivers. well it always has for me anyways

---

### Post by ian-weisser on 2014-12-17
Wireless RTL8192CE drivers should be included with the default install of Ubuntu.
That wireless hardware should work out-of-the-box.
No fiddling with drivers should be needed.

Are you saying that wireless doesn't work at all?
Or are you saying that wireless works, but poorly?

(If the latter, see [http://askubuntu.com/questions/414974/realtek-rtl8192ce-wireless-slow-intermittent-access](http://askubuntu.com/questions/414974/realtek-rtl8192ce-wireless-slow-intermittent-access) for several solutions)

---

### Post by nick70 on 2014-12-17
Ok, so when I first installed Ubuntu (quite a while ago, not the current installation but same computer) when I tried to connect to my wifi network, it just thought for a bit and then asked me for the pass key again. It would do this indefinitely. The same thing happened with the current installation; except now, I must have screwed up the card or something because now no wifi networks show up under the Wireless menus. So no, wireless doesn't work at all.

---

### Post by oldfred on 2014-12-17
A lot of newer Gigabyte boards seem to need IOMMU settings.

Make sure you have the newest UEFI/BIOS from Gigabyte.

       turns out the IOMMU needs to be enabled (or disabled?) in the BIOS. This problems seems to be exclusive to Gigabyte boards.

Some also need settings in boot parameters. Test if any work or help, then if they do, then we can make them permanent. 

First just change setting in UEFI/BIOS or IOMMU.
Then try  this one: which seems to be [COLOR=#008000][I]iommu=soft, 
[/I][/COLOR]You add it just like nomodeset.        
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
> usb, 2.0 usb 3.0 and networking all work now in Ubuntu, and disabling  iommu in bios helps prevent windows freezes that was occurring if you  are running a dual boot environment. 


And some different settings.
      
 Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[http://ubuntuforums.org/showthread.php?t=2254677](http://ubuntuforums.org/showthread.php?t=2254677)

---

### Post by nick70 on 2014-12-17
I went into my BIOS and enabled IOMMU. I booted into Linux, and the WiFi networks showed up, and I was able to connect successfully to my wifi! However, when I open up a browser or the Ubuntu software center, it just says "Connecting". Is the signal not coming through? It connected successfully on the first try, no rejecting the code or anything.

---

### Post by nick70 on 2014-12-17
I also followed the instructions given by Wild Man on this post:

[http://ubuntuforums.org/showthread.php?t=198507](http://ubuntuforums.org/showthread.php?t=198507)

But that did nothing. Except, when I ran gksudo, it said the package wasn't installed yet, so I used sudo instead. I don't think that would have made a difference, but I don't know...

Also, the first command given created a new, blank file, so I just put the line of code into it, not above eth0 or whatever it says.

---

### Post by Paula_Livingstone on 2014-12-18
Hi Nick,

Assuming youre now connecting to your WiFi network? Could you post the output when you run ifconfig now please as well as that from "ip route show".

---

### Post by oldfred on 2014-12-18
Your link is to a thread from 2006?
If you had a command to edit a file with gedit you must use gksudo. 
gksudo for graphical programs
sudo for terminal programs
And if a blank file came up you were creating a new file, either a typo or file did not exist.

---

### Post by nick70 on 2014-12-18
ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 74:d4:35:04:7b:e8             UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 


lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:65536  Metric:1 
          RX packets:122 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:7526 (7.5 KB)  TX bytes:7526 (7.5 KB) 


wlan0     Link encap:Ethernet  HWaddr 04:8d:38:07:e0:45   
          inet addr:192.168.0.21  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::68d:38ff:fe07:e045/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:40 errors:0 dropped:2 overruns:0 frame:0 
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:3696 (3.6 KB)  TX bytes:10237 (10.2 KB)
```

and ip route show:

```
default via 192.168.0.1 dev wlan0  proto static 
192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.21  metric 9 
```

---

### Post by naga2raja on 2014-12-22
If you are unable to find any wireless networks list and you feel that your wireless card is working properly, then try stoping the network manager and connecting to the wireless network via command prompt.

To Stop N/W Manager:
> sudo service network-manager stop

To connect to wireless network Manually via terminal, Please follow the post [http://askubuntu.com/questions/16584/how-to-connect-and-disconnect-to-a-network-manually-in-terminal?lq=1](http://askubuntu.com/questions/16584/how-to-connect-and-disconnect-to-a-network-manually-in-terminal?lq=1)

---

### Post by ian-weisser on 2014-12-22
> **nick70 said:**
> 
wlan0     Link encap:Ethernet  HWaddr 04:8d:38:07:e0:45   
          **inet addr:192.168.0.21**  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::68d:38ff:fe07:e045/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          **RX packets:40** errors:0 dropped:2 overruns:0 frame:0 
          **TX packets:66** errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          **RX bytes:3696 (3.6 KB)  TX bytes:10237 (10.2 KB)**

default via 192.168.0.1 dev wlan0  proto static 
192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.21  metric 9 

Your ifconfig and route look like your system is properly connected to your wireless gateway.
The gateway DHCP server has apparently issued you an IP address (or did you put that in manually?), and exchanged plenty of packets without error.
When you took your snapshot, did you *seem* connected?

If not, the next things to look at are any configuration changes you made (hope you recall those), and plain old distance between the machines. Some building materials are very good at blocking wireless signal.

---

### Post by nick70 on 2014-12-22
> **ian-weisser said:**
> When you took your snapshot, did you seem connected?.


That's the thing. Ubuntu connects to the wifi network just fine and says that it's connected, but when I try to use a network application, i.e Firefox or Ubuntu software center, it won't connect to anything. This snapshot might illustrate my point better:

[ATTACH=CONFIG]258736[/ATTACH]

The wifi shows connected, but Firefox won't load pages.

Also, I would be concerned about distance and material because my computer is about as far away as you can get from my router, but Windows connects to the wifi just fine.

---

### Post by ian-weisser on 2014-12-22
Do you still have your install USB stick?
If so, boot from it, and try to use the internet in the trial environment.
If it works, then the problem is some settinng on your current install.

While experimenting, did you happen to change any kernel settings?
Network Manager settings?
Install WiCD?
Install any kind of proxy?
Change firewall settings?
Install some kind of firewall application? 

Any of those (and more) might have cause the problem you are having.

In a terminal, can you ping out? What's the result if you try:
```
ping -c 1 8.8.8.8
```

---

### Post by nick70 on 2014-12-22
I do have my CD, yes.

I went into both the CD and normal install. CD also connects to wifi fine. However, neither will ping correctly.

```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 

--- 8.8.8.8 ping statistics --- 
1 packets transmitted, 0 received, 100% packet loss, time 0ms 
```

This happens on both CD and install, which I'm assuming suggests that it isn't a problem with my install or something I did to configure it. Likewise, I don't remember doing anything to change the internet settings.

---

### Post by ian-weisser on 2014-12-23
> **nick70 said:**
> This happens on both CD and install

If the network problem occurs with the original install media --which you cannot change the settings upon--, then the problem seems not your Ubuntu settings.

Since the wireless hardware handshakes and connects, then the problem seems not a driver issue.

Perhaps it's time to look at your router:
Is everything else on your LAN connecting out to the internet just fine?
Do you have any custom firewall rules or other settings on your router?
Are you using the router's normal DHCP service?

---

### Post by nick70 on 2014-12-23
Everything that is connected to this wifi connects just fine. This includes multiple iPhones and Macs, as well as my Windows OS, my laptop's Windows and my sister's laptop's Windows. Also, when I use Ubuntu on my laptop, it connects fine. This probably just makes things even more complicated.

I don't believe I have changed any settings on the router. However, since I am not very well versed with network settings, I'd be happy to post screenshots of my router's firewall page and other pages, if you think they would help.

I'm sorry for making this such a hard question.

---

### Post by ian-weisser on 2014-12-23
It's not a hard question...but I'm admittedly out of ideas.

Your system seems to be doing something that I cannot reproduce.

If other machines on your network had problems getting internet access, I would suspect the router.
If your machine could connect to the network when booted from the LiveInstall media, then I would suspect a changed setting since install.
But I have never seen a case where the LiveInstall environment could connect to an open, wireless network...but not push data over it.

I will gracefully yield to other members of the community.

---

### Post by MrSteve on 2014-12-23
maybe worth looking at the network management settings for that connection and check to see if a DNS server address is listed
if no DNS address is listed use the gateway address of your router and place that address in the DNS server box ...

---

