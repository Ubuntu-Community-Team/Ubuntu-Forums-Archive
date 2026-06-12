---
title: "Unstable wireless connection"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by amelie on 2008-11-20
Hi there,

I've got my wireless network since a couple of months - I use a wireless USB adapter D-LINK. At the beginning a plug -out and -in was okay when the signal was lost, but yesterday it seems to have gone at all. Restart also does nothing... What could be the problem?
Thanks for the attention
amelie

---

### Post by SamNSane on 2008-11-20
I'm not familiar with any of the DLink USB adapters. It may help those who want to help if you post which version of the OS you are running, as well as the exact model number of that adapter.

I can tell you that USB wireless network adapters are pretty flakey, compared to other types. Part of the reason for that is that you've typically got power management trying to put various parts of the system to sleep to save power, and in this case it's doing it on two pieces of hardware in the chain -- the adapter itself and the USB port/hub.

It seems from your comment that, for a while at least, unplugging and replugging the adapter was getting you reconnected. That is one of the hallmarks for power management problems. The OS (or even the BIOS on some systems) sees low activity on the NIC and says, "Hmmm. You don't need that any more. Why don't I put it to sleep for you?"

Does the adapter have a link or an activity light on it? If so, were you seeing changes in the light behavior between the connected and disconnected states?

---

### Post by amelie on 2008-11-20
Hello, SamNSane,
I agree to you about the power management problems, I've even discussed it with another guy, but we weren't sure as well.
About the link activity - before, when I had no network and needed to plug out and in, there was only the Link light, but not the activity one as well. When i have network, the Link is permanently on, the activity one is blinking. Now i have them like that, everything seems okay, but there is no network, what do you think?
Thanks for being there for my problem
amelie

---

### Post by SamNSane on 2008-11-20
I'm a little confused. Do you mean that the link light is on, and the activity light is blinking, but you still do NOT have a network connection?

I hope someone more familiar with Ubuntu than I will come along to help you. I'm a beginner in this operating system myself. In the meantime, I'll try to be helpful by asking you for information that I think will be needed.

Please tell us the model of the USB network adapter. Also, tell us:

1. Was the adapter detected and supported immediately by the operating system upon installation, or did you have to do something special to get it to be operational?
2. Is the wireless access point / router under your private control, or are you trying to access a publicly available wireless network?
3. Is encryption used for the network? If so, what kind?
4. Is the SSID being broadcast?
5. Which Ubuntu version are you running?
6. What are you using for controlling networking? The network-manager applet? WICD?

It would also be a good idea to post the output from the following two commands issued in the terminal:

iwconfig
ifconfig

You should use the Code (#) tag and paste the results for each command from the terminal window in between the two parts of the tag.

If you post this information, it may help the other users here to help you. We will certainly need more information than we have right now.

Thanks.

---

### Post by amelie on 2008-11-20
=) > I'm a little confused. Do you mean that the link light is on, and the activity light is blinking, but you still do NOT have a network connection? You understood me correctly ;)

D-LINK AirPlusG+DWL-G122
1. I used ndiswrapper to read my drivers
2. wi-fi point from a home-installed router
3. WEP, shared key
4. no idea about that :)
5. ubuntu hardy heron 8.04
6. network manager


```

iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan1     IEEE 802.11g  ESSID:""   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=27 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B    
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

```

```

ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:bc:86:1d   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:220 Base address:0x6000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1246 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1246 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:67318 (65.7 KB)  TX bytes:67318 (65.7 KB) 
 
wlan1     Link encap:Ethernet  HWaddr 00:21:91:82:df:58   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wlan1:avahi Link encap:Ethernet  HWaddr 00:21:91:82:df:58   
          inet addr:169.254.7.254  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-21-91-82-DF-58-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

```

---

### Post by SamNSane on 2008-11-20
I'm finally at a location where I can answer again (been traveling around). But I'm afraid I'm not sure where to go from here. It appears to me as though your adapter is failing to receive a signal from your router. This could happen because:

1. Your router isn't broadcasting, at least on a frequency received by your adapter. (It's "channel" hasn't been changed recently, has it?)
2. Your adapter is malfunctioning or is misconfigured in some way.

The information provided shows that your wireless interface is configuring itself at 169.254.7.254. That 169.*.*.* address is an indication that your system is asking for an address to be allocated for it via DHCP, and that it is receiving no response.

The first thing to do is to check to be sure that the wireless router is turned on and behaving itself. Are there other systems present that are connecting successfully to this router -- wirelessly? If there are, that narrows the issue down (maybe, and I do stress maybe) to your network adapter. We might need to know about those other systems -- wireless channel being used especially. If there are no other systems that you can use to successfully connect to the router you could first just try rebooting the router -- usually done with most of them by shutting them down and restarting them. I have to do this once-in-a-while (say, once ever other month or so) because of issues with my ISP and their provided cable modem.

If that doesn't work, then we have to start getting down to the nitty-gritty, which I probably can't help you with very much in this operating system. I'm kind of new in this environment. But you should go ahead and try these things and report what happens so that other people viewing the thread (people who are more knowledgeable about Ubuntu / Linux) can pick up where I've had to leave off.

I'm still going to stay tuned, and I'll try to help if I think I'm able. But I'm not going to pretend to be familiar with the way to go ahead with handling driver / hardware issues in Ubuntu.

---

### Post by amelie on 2009-01-03
Hello, SamNSane! Happy New Year, first, then very big thanks to all you've written here, excuse me for the great delay :) 
Now I read everything carefully and here we are:
There are other computers that connect to the router wirelessly.
The channel of the router hasn't been changed recently.

---

### Post by Michael.Godawski on 2009-01-03
hi,

can you please post the output of these terminal commands:

```
sudo lshw -C network
cat /etc/network/interfaces
```

---

### Post by amelie on 2009-01-03
```
amelie@amelie-desktop:~$ sudo lshw -c network cat /etc/interfaces

sudo: unable to resolve host amelie-desktop

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

```

Thank you very much for the interest.

---

### Post by Michael.Godawski on 2009-01-03
wowow...:D

I have posted two different commands. Run them one after the other.
Make sure you type a capital C in the first command.

---

### Post by amelie on 2009-01-03
Excuse me, I had to understand this on my own, but i was in a hurry and gave instructions to another person to do this for me, I was away from the PC :)
here is the true info now:
```

**sudo lshw -C network**

 *-network             
       description: Wireless interface 
       physical id: 1 
       logical name: wlan1 
       serial: 00:21:91:82:df:58 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 

```

```

**cat /etc/network/interfaces **
auto lo 
iface lo inet loopback 
 
iface eth0 inet dhcp 
 
iface wlan1 inet dhcp 
wpa-driver wext 
wpa-key-mgmt WPA-PSK 
wpa-proto WPA 
wpa-ssid TP-LINK 

auto wlan1 
[/B]

```

---

### Post by amelie on 2009-01-07
the most interesting thing about it is that the act lamp of the adapter is blinking...

---

