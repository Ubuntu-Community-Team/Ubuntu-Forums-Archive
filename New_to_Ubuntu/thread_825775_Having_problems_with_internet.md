---
title: "Having problems with internet"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by This is Linux on 2008-06-11
I am currently having two problems. 1. Whenever I unplug or plug in the ethernet cable, linux crashes. In windows, it just displays a windows that a cable has been removed. Can I not do this in linux? 2. I cannot connect to my wireless network. I believe my wireless card is on and working based on the output of my terminal from the command iwconfig(posted below), but I cannot seem to to find my wireless network. Help?
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by powerpleb on 2008-06-11
Does your wireless network have a hidden ESSID?

It looks to me like the wireless card can see the network but all information about it is hidden.

---

### Post by This is Linux on 2008-06-11
I don't believe so, as this laptop was able to detect it when it was windows.

---

### Post by powerpleb on 2008-06-11
try this
```
sudo iwlist scan
```

---

### Post by This is Linux on 2008-06-11
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
Does this mean that no wireless networks are in the area? Thats weird, because when I hold my DS 3 feet away, it detects 7 networks.

---

### Post by geezerone on 2008-06-11
Sounds like two different problems.

You should be able to unplug/plug the ethernet cable without any crashes, but what messages or info could you provide about the crashes.

The wireless problem is a different kettle of fish. Have you hidden the SSID of your network on your Access Point/Router? Has it ever worked and what device/chipset are you using as well as distribution of Ubuntu?

You may have to install the wireless device otherwise.

---

### Post by This is Linux on 2008-06-11
1. When I unplug the ethernet, the whole system just locks up and I have to do a hard shut down and restart. But it has crashed like 3 times this morning (3 times in about 2-3 hours, and I have only disconnected the ethernet once, so I was probably wrong about the source of the crashes, sorry)

2. I do not believe that I have hidden it. I can't seem to find the visibility setting on the router configuration program, but my DS did just detect it so I figure it is not hidden. 

3. I installed linux (any kind) for the first time on this laptop yesterday, and the wireless hasn't worked since then. But, when I go to the hardware drivers section, it says that the Broadcom b43 wireless driver is enabled and in use.

---

### Post by ukripper on 2008-06-11
Can you post output of the following:

```
lshw -C network
```

---

### Post by This is Linux on 2008-06-11
*-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:28:78:14
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.0.195 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:47:3b:54
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
Thats the output.

---

### Post by decoherence on 2008-06-11
Sorry to keep throwing commands at you, but can you try

```
sudo ifconfig wlan0
```

as well as 

```
nm-tool
```

are you using WEP or WPA on the network?

---

### Post by powerpleb on 2008-06-11
I think I had the same problem.

In my laptop when I installed Ubuntu Hardy it used some drivers that didn't work with my wireless interface. It said it was working, but it wasn't. Is your wireless interface Atheros? If so this *may* be the solution.

I had to use ndiswrapper to enable it to use Windows drivers.

If you can get it on the internet I suggest you use Synaptic to install ndisgtk.

Go into System > Hardware Drivers and disable the Broadcom drivers.

Then get the windows drivers and load up ndisgtk (you can do this with sudo ndisgtk in the terminal) and use it to choose the drivers.

You may have to reboot but then your wireless should work.

---

### Post by This is Linux on 2008-06-11
sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:14:a5:47:3b:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
(Note: The ethernet is plugged into this computer, so it might be throwing off the results)
nm-tool
NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/wlan0
  Type:              802.11 Wireless
  Driver:            b43
  Active:            no
  HW Address:        00:14:A5:47:3B:54

  Capabilities:
    Supported:       yes

  Wireless Settings
    Scanning:        yes
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Networks (* = Current Network)


- Device: eth0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/eth0
  Type:              Wired
  Driver:            sky2
  Active:            yes
  HW Address:        00:03:25:28:78:14

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings
    Hardware Link:   yes

  IP Settings:
    IP Address:      192.168.0.195
    Subnet Mask:     255.255.255.0
    Broadcast:       192.168.0.255
    Gateway:         192.168.0.1
    Primary DNS:     192.168.0.1
    Secondary DNS:   0.0.0.0

---

### Post by This is Linux on 2008-06-11
Powerpleb, sorry but I have no idea what atheros is, but if you give me some command to find out, I can type that in and give you the result.

---

### Post by geezerone on 2008-06-11
> **This is Linux said:**
> 2. I do not believe that I have hidden it. I can't seem to find the visibility setting on the router configuration program, but my DS did just detect it so I figure it is not hidden. 

What router are you using, perhaps we can help you find it? 

I have Windows and Nintendo equipment that works with hidden SSID but the linux machine doesn't (and I am on different chipset)?

> **This is Linux said:**
>  3. I installed linux (any kind) for the first time on this laptop yesterday, and the wireless hasn't worked since then. But, when I go to the hardware drivers section, it says that the Broadcom b43 wireless driver is enabled and in use.

I was able to see some networks nearby but not my own so that doesn't guarantee that it is fully operational. Try the ndiswrapper way first and if no joy try the fwcutter route.

Edit: Found [http://ubuntuforums.org/showthread.php?t=824262&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=824262&highlight=BCM4318) which may help?

---

### Post by This is Linux on 2008-06-11
1. I am using a d-link DIR 655.
2. I will try the ndiswrapper method now.

---

### Post by geezerone on 2008-06-11
To check if SSID is on or off go to *Wireless* setting of the router, and examine the *Visibility status* of your network. You want to make it visible for now anyway. I would also set the 802.11 mode to *mixed 802.11b and 802.11g* for now too and keep channel at 6.

The manual for it can be found under *product manual *[here]("http://www.dlink.com/products/?pid=530").

---

### Post by This is Linux on 2008-06-11
I am trying to find the windows drivers and the directions for the ndiswrapper method but I am completely lost, could someone post links or something. Also, I don't know if it is important but I am running a gateway mx7515 with a broadcom 4318 card. Finally, it seemed that it stopped crashing for a while, but now my computer is continually crashing, could it be my failed attempts to install the drivers are causing this?
Edit: My router is visible and is running in mixed ng, g, and b mode.

---

### Post by powerpleb on 2008-06-11
These posts will help you:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by This is Linux on 2008-06-11
That last link ([http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)) did the trick. Thank you guys very much. My laptop now connects to my network perfectly. Just to make sure, I rebooted my computer to ensure that it would automatically reconnect, which it did. Oddly, the first reboot it hung and I had to turn it off with about 1/4th of the orange bar left to disappear, but on my second reboot, everything went smoothly, so I assume it was just a hiccup. Finally, I would just like to thank you guys again for helping me.

---

### Post by powerpleb on 2008-06-11
> **This is Linux said:**
> That last link ([http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)) did the trick. Thank you guys very much. My laptop now connects to my network perfectly. Just to make sure, I rebooted my computer to ensure that it would automatically reconnect, which it did. Oddly, the first reboot it hung and I had to turn it off with about 1/4th of the orange bar left to disappear, but on my second reboot, everything went smoothly, so I assume it was just a hiccup. Finally, I would just like to thank you guys again for helping me.

No problem.

Now that you've successfully got wireless working on Linux the rest will seem like a walk in the park.

---

