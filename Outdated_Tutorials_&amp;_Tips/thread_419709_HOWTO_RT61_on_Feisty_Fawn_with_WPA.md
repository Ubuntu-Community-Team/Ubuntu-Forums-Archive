---
title: "HOWTO: RT61 on Feisty Fawn with WPA"
date: 2007-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by amniarix on 2007-04-23
These are my experiences getting a RT61-based wireless LAN (WLAN) card to work on Ubuntu Feisty Fawn (7.10) using WPA authentication. My chipset is:

ubuntu@ubuntu:~$ lspci | grep Ra
05:00.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

Part 1 first gets the interface working by manual tweaking, done running from the live CD in these examples to ensure a pristine environment. Explanations are given for each step so that if/when it Doesn't Work for You, the experience isn't a complete write-off. Part 2 then automates the configuration on startup.

** Why not Network Manager?**

Ubuntu 7.04's NetworkManager (found under System -> Administration -> Network, or from the gnome applet) is not able to configure WPA with the rt61 driver (see the [list of NetworkManager's supported drivers]("http://live.gnome.org/NetworkManagerHardware")), so I could not use it. Some guides I've seen recommend uninstalling it ('sudo dpkg -P network-manager network-manager-gnome'), but I found that to be unnecessary.

** Differences from Edgy**

Back with Ubuntu 6.10, I successfully followed the [HOWTO: RT61 on Egdy Eft with WPA]("http://www.ubuntuforums.org/showthread.php?t=296822") guide. With 7.04 most of this is obsolete. The ralinktech.com driver (RT61_Linux_STA_Drv1.0.4.0.tar.gz) does not even compile on my 2.6.20 kernel:

```
 jturner@psyche:~/RT61_Linux_STA_Drv1.1.0.0/Module$ make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/jturner/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M] /home/jturner/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/jturner/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_probe’:
/home/jturner/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/jturner/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_open’:
/home/jturner/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/jturner/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/jturner/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2
jturner@psyche:~/RT61_Linux_STA_Drv1.1.0.0/Module$ 
```

And neither do you need it, because Feisty includes the mostly-working fork(?) of it from serialmonkey.com:

```
 ubuntu@ubuntu:~$ lsmod | grep rt61
rt61 245128 1

ubuntu@ubuntu:~$ modinfo rt61
filename: /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko
license: GPL
description: Ralink RT61 802.11abg WLAN Driver 1.1.0 CVS CVS
author: http://rt2x00.serialmonkey.com
srcversion: 180F8980D3385B365E8F654
alias: pci:v00001814d00000401sv*sd*bc*sc*i*
alias: pci:v00001814d00000302sv*sd*bc*sc*i*
alias: pci:v00001814d00000301sv*sd*bc*sc*i*
depends:
vermagic: 2.6.20-15-generic SMP mod_unload 586
parm: debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)
parm: ifname:Network device name (default ra%d) (charp)
ubuntu@ubuntu:~$ 
```

The old Edgy howto, and rt2x00.serialmonkey.com distribution's instructions both say to copy some bin files to /etc/Wireless/RT61STA/, and configure a rt61sta.dat file in there with wireless connection details. This worked for me in Edgy with my hand-compiled rt61 driver, but hasn't worked for me in Feisty (perhaps this was just user error). So below I haven't used them, and the configuration previously done in rt61sta.dat I now do in /etc/network/interfaces 'pre-up' sections.


[SIZE=4]** 1) Manual Configuration**[/SIZE]

After booting the live CD, or after a clean install, you will see Ubuntu has an interface for the network card already configured:

```
 ubuntu@ubuntu:~$ ifconfig ra0
ra0 Link encap:Ethernet HWaddr 00:08:A1:A3:C2:B0
inet6 addr: fe80::208:a1ff:fea3:c2b0/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2248 errors:0 dropped:0 overruns:0 frame:0
TX packets:9630 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:235262 (229.7 KiB) TX bytes:0 (0.0 b)
Interrupt:16

ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"" Nickname:""
Mode:Managed Frequency:2.412 GHz Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=0/100 Signal level:-121 dBm Noise level:-111 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

However, as ra0 is unconfigured (ESSID:"", etc), the network connection isn't working. We need to configure it manually. Interface configuration is done with 'ifconfig'. Wireless interfaces need additional configuration with 'iwconfig' and 'iwpriv'.


[SIZE=3]** 1.1) Disable the ra0 interface**[/SIZE]

First thing to note is that if the interface is enabled (listed in 'ifconfig' output), your iwconfig/iwpriv changes won't take effect:

```
 ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"" Nickname:""
Mode:Managed Frequency:2.412 GHz Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=0/100 Signal level:-121 dBm Noise level:-111 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ubuntu@ubuntu:~$ sudo iwconfig ra0 essid WHALENET
ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"" Nickname:""
Mode:Managed Frequency:2.412 GHz Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=0/100 Signal level:-121 dBm Noise level:-111 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ubuntu@ubuntu:~$ 
```(note no change to ESSID)

So first bring down the ra0 interface:

```
 ubuntu@ubuntu:~$ sudo ifconfig ra0 down
ubuntu@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:16:177:AC:C1
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:17 Base address:0x6000

eth0:avah Link encap:Ethernet HWaddr 00:16:177:AC:C1
inet addr:169.254.9.63 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:17 Base address:0x6000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:20 errors:0 dropped:0 overruns:0 frame:0
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1432 (1.3 KiB) TX bytes:1432 (1.3 KiB)

ubuntu@ubuntu:~$ 
```Notice that the ra0 interface is gone.

[SIZE=3][B]
1.2) Configure ra0 with iwconfig and iwpriv.[/B][/SIZE]

Now we want to configure the ra0 interface so it connects to the wireless network. I am using WPA with a shared key (WPA PSK), connecting to a network called WHALENET. Your essid and WPAPSK will be different (possibly other settings too, but start with those).

```
 ubuntu@ubuntu:~$ sudo iwconfig ra0 essid WHALENET
ubuntu@ubuntu:~$ sudo iwpriv ra0 set AuthMode=WPAPSK
ubuntu@ubuntu:~$ sudo iwpriv ra0 set WPAPSK="My secret WPA key"
ubuntu@ubuntu:~$ sudo iwpriv ra0 set EncrypType=TKIP
ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"WHALENET" Nickname:""
Mode:Managed Frequency:2.462 GHz Access Point: 00:0F:B5:1D:C2:CE
Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=85/100 Signal level:-50 dBm Noise level:-79 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ubuntu@ubuntu:~$ 
```

Make sure that ESSID has taken the value you set it to. If the interface is working, the 'Link Quality' should be something other than 0/100.

Not working? Then check if the wireless network is even visible with 'iwlist scan':
```
 ubuntu@ubuntu:~$ sudo iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

ra0 Scan completed :
Cell 01 - Address: 00:0F:B5:1D:C2:CE
ESSID:"WHALENET"
Mode:Managed
Channel:11
Encryption keyn
Quality:84/100 Signal level:-53 dBm Noise level:-256 dBm

ubuntu@ubuntu:~$ 
```

You may find that other iwpriv parameters need tweaking.  As a reference, you could download the rt61 driver source from serialmonkey.com. Valid parameters are listed in the Module/rt61sta.dat file. I'd recommend running 'sudo ifconfig ra0 down' before 'iwpriv', just in case the interface's up'ness prevents its reconfiguration.

[SIZE=3][B]
1.3) Configure ra0's IP details[/B][/SIZE]

Now configure the ra0 interface's IP. I am using a static IP here (192.168.0.102, randomly picked from the my valid 192.168.0.x range):

```
 ubuntu@ubuntu:~$ sudo ifconfig ra0 192.168.0.102 netmask 255.255.255.0 up
ubuntu@ubuntu:~$ ifconfig ra0
ra0 Link encap:Ethernet HWaddr 00:08:A1:A3:C2:B0
inet addr:192.168.0.102 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::208:a1ff:fea3:c2b0/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5179 errors:0 dropped:0 overruns:0 frame:0
TX packets:12548 errors:0 dropped:0 overruns:0 carrier:0
collisions:1 txqueuelen:1000
RX bytes:554229 (541.2 KiB) TX bytes:3850 (3.7 KiB)
Interrupt:16

ubuntu@ubuntu:~$ 
```

[SIZE=3][B]
1.4) Configure routes[/B][/SIZE]

At this point, my default route is still eth0 (my unused wired network card):

```
 ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.0.0 * 255.255.255.0 U 0 0 0 ra0
link-local * 255.255.0.0 U 0 0 0 eth0
default * 0.0.0.0 U 1000 0 0 eth0
ubuntu@ubuntu:~$ 
```
So let's delete it and add a default route to my router (192.168.0.1):

```
 ubuntu@ubuntu:~$ sudo route del default
ubuntu@ubuntu:~$ sudo route add default gw 192.168.0.1
ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.0.0 * 255.255.255.0 U 0 0 0 ra0
link-local * 255.255.0.0 U 0 0 0 eth0
default 192.168.0.1 0.0.0.0 UG 0 0 0 ra0
ubuntu@ubuntu:~$ 
```

I can now ping the router (if you can ever ping a router, congratulations, the worst is over):

```
 ubuntu@ubuntu:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=9.52 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.63 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=1.59 ms
...
```


**[SIZE=3] 1.5) Configure DNS[/SIZE]**

DNS isn't yet configured:

```
ubuntu@ubuntu:~$ ping google.com
ping: unknown host google.com
```

I want my router to be the DNS server, and this is done by creating (the live CD doesn't have one) an /etc/resolv.conf:

```
 ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# echo "nameserver 192.168.0.1" >> /etc/resolv.conf
root@ubuntu:/home/ubuntu# ping google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=242 time=243 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=242 time=242 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=242 time=243 ms
```

[SIZE=3][B]
1.6) Manual configuration: summary[/B][/SIZE]

This manual configuration can be summed up by these commands:

sudo ifconfig ra0 down # Take interface down for configuration
ubuntu@ubuntu:~$ sudo iwconfig ra0 essid WHALENET # Set the name of the network you want to join
ubuntu@ubuntu:~$ sudo iwpriv ra0 set AuthMode=WPAPSK # I use shared-key WPA authentication
ubuntu@ubuntu:~$ sudo iwpriv ra0 set WPAPSK="My secret WPA key" # My shared key
ubuntu@ubuntu:~$ sudo iwpriv ra0 set EncrypType=TKIP
ubuntu@ubuntu:~$ sudo ifconfig ra0 192.168.0.102 netmask 255.255.255.0 up # Configure interface with IP details
ubuntu@ubuntu:~$ sudo route del default # Delete default (eth0) route for IP traffic
ubuntu@ubuntu:~$ sudo route add default gw 192.168.0.1 # Default route to my router


**[SIZE=4] 2) Automatic configuration on startup[/SIZE]**

We want to do all the above steps automatically when Ubuntu starts. The
/etc/init.d/networking script will invoke 'ifup', which in turn runs the
'ifconfig' and 'route' commands we performed manually above. ifup's
configuration file is /etc/network/interfaces.

So edit /etc/network/interfaces:

```
ubuntu@ubuntu:~$ sudo gedit /etc/network/interfaces 
```and at the beginning, add a section like:

```
 auto ra0
iface ra0 inet static
address 192.168.0.102
netmask 255.255.255.0
gateway 192.168.0.1
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid WHALENET
pre-up iwpriv ra0 set WPAPSK="My secret WPA key"
```Run 'man interfaces' to see a detailed explanation. In short:
[LIST]
[*]     'auto ra0' says that the ra0 interface is to be brought up automatically on system startup ('ifup -a' run from '/etc/init.d/networking start').
[*]     'iface ra0 inet static' defines ra0 as a statically configured TCP/IP interface. If instead you want to use DHCP, instead specify 'iface ra0 inet dhcp' and omit the address, netmask and gateway lines
[*]     address, netmask and gateway is the static IP configuration for my interface.
[*]     the 'pre-up' commands are run before the interface is brought up. Here we configure the interface with our wireless details (step 1.2 above).[/LIST] 
You can test this all by running 'sudo ifdown ra0' and 'sudo ifup ra0', which is essentially what the init.d script does on startup.

If you have any stories of success or failure, or know of an easier/better way of doing things, please let everyone know in the comments.

---

### Post by huygens on 2007-04-25
> **amniarix said:**
> Ubuntu 7.04's NetworkManager (found under System -> Administration -> Network, or from the gnome applet) does not support WPA, so I could not use it.

A small detail, Network Manager does support WPA and even WPA2 (I am using it with an Intel based WiFi card with WPA2, and I have been using it before with WPA).
The problem is that the Ralinktech drivers (both the opensource rt2x00 and the rt61 that one can download from the Ralinktech web site) do not provide the necessary interface in its API to have Network Manager support WPA with this driver.
Check [NetworkManager hardware support wiki]("http://live.gnome.org/NetworkManagerHardware").


But in the end you're right :-) using Network Manager with a Ralink driver and using WPA encryption does not work :-(

---

### Post by jerathim on 2007-04-25
My interface is called ra1 by default and not ra0. I am using WPAPSK and TKIP as in the example.
There is an open access point in the area and it tries to use it instead of my home encrypted network. I edited the instructions to be for ra1 but still it does not associate with my AP. It instead remains connected to the open AP in the area.
With ifdown and ifup I get errors.

I'm using a WMP54G 4.1, had it working fine in Edgy Eft, but in both Ubuntu and Kubuntu 7.04 it has been a major pain. I even tried compiling the serialmonkey CVS build in Kubuntu and it still did not work. However, I did use the dat file when I did that. I did not use the new method of pre-up.
I was trying Kubuntu hoping its wireless managers would be of help. Unfortunately, they did not enable wpa_supplicant for rt61.

Update: After rebooting ifconfig and iwconfig show the correct information but I still can't ping anything.
In the boot CD it is ra0
Update: I pulled out the kernel module that came with ubuntu and replaced it with the latest CVS build, then followed the steps of writing interfaces file. It is ra0, but unfortunately ubuntu no longer boots as it has Soft CPU Lockup 100% of the time. Time to pop in Knoppix...

I'm afraid I'd have to do a fresh install now. I managed to remove the interfaces entry and now I can boot again, but the bleeding edge module is still installed. Maybe the older latest Beta won't crash?

---

### Post by amniarix on 2007-04-25
> **jerathim said:**
> Update: After rebooting ifconfig and iwconfig show the correct information but I still can't ping anything.

If you run 'iwconfig', what does "Link Quality" say? If it's 0/100, you've not connected, and you need to 'sudo ifconfig ra0 down' and try other iwpriv settings (going by what 'sudo iwlist scan' says of your network). If the link quality is nonzero and 'ifconfig' lists the wireless interface, try getting the routing correct before investigating more exotic causes.  'route' should print something like this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 ra0
link-local      *               255.255.0.0     U     1000   0        0 ra0
default         192.168.0.1     0.0.0.0         UG    0      0        0 ra0
```

The contents of /var/log/messages and /var/log/kern.log might also be useful.

---

### Post by jerathim on 2007-04-25
I think I'd better start fresh, I've messed with it too much.

---

### Post by msemenkin on 2007-04-25
Thanks a lot! It was very helpful for me!

---

### Post by thelonelyrider on 2007-04-25
hey!

first of all thank you amniarix for your explanations!

everything is working fine when I configure it manually!

i think i made a mistake in the interface configuration but can't find it.

my /etc/network/interfaces looks like:

auto ra0
iface ra0 inet static
adress 192.168.1.77
netmask 255.255.255.0
gateway 192.168.1.1
pre-up iwconfig ra0 essid hackmichdoch
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set WPAPSK="My secret WPA key"
pre-up iwpriv ra0 set EncrypType=AES

auto lo
iface lo inet loopback

if I try "ifup ra0" it fails with error message "Don't seem to be have all variables for ra0/inet"

Don't know what is wrong. Like I mentioned before, everything works fine manually!
:confused:

---

### Post by jhpope on 2007-04-25
works well up until 1.4

what router are you using? i have a netgear and i think my gateway is 192.168.1.1 not 192.168.0.1
192.168.1.1 is what i use to get to the router config in windows.

i can follow all your steps perfectly and get the same results up to pinging the router. i get no response at either 192.168.1.1 or 0.1 and i have tried configuring w/ both default gateways.

also, my wireless is coming up as ra1 instead of ra0...don't know if this is having anything to do with it.

seems like i'm having the same problems as jerathim...jerathim have you gotten this to work yet? i have the same deal ra0 from the live cd and ra1 after a clean install.

---

### Post by jerathim on 2007-04-26
No, I haven't had any luck yet. I just did a fresh install and haven't messed with it yet. Once again it is ra1 instead of ra0. I have to remain wired to my router until we find a way through this setback. I'm not sure the open wireless is working well, but it might just be a poor signal. I can't do the manual steps to test it because it won't accept my SSID. All I can try is the steps to configure it for startup. (I will have to make someone change their laptop settings to change the SSID on them)
Why would it be ra1 rather than ra0 when I only have one wireless card? This time I'm not touching the module, I'm just using what came with it to test.
How much of the logs would be helpful? I can't really read them well. I don't know what I am looking for.

---

### Post by amniarix on 2007-04-26
> **jerathim said:**
> I can't do the manual steps to test it because it won't accept my SSID.

Have you run 'sudo ifconfig ra1 down' just before trying? My SSID wouldn't change too when the interface was 'up' (listed in ifconfig output).

---

### Post by jerathim on 2007-04-26
Yes, I did. It gave an error because my SSID has non-alphanumeric characters in it. It acted like it tried to execute something because of a symbol in the SSID, so Bash was confused so to speak. I'm going to have to go get my dad to change his SSID on the laptop so we can set a normal one for the network. I still think you should be able to put whatever you want as the SSID...

"bash: !_xxxxx$_xxx: event not found"
(x = the alphanumeric part)

Oh, and by default, network manager sees zero signal strength from my network but a less than 50% strength for the open one.

Ok, I brought the interface back up without successfully doing anything to it, and did a scan and my network shows:

Cell 02 - Address: XXX
                    ESSID:"xxxxxxxx!_xxxxx$_xxx"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Quality:0/100  Signal level:-34 dBm  Noise level:-256 dBm

(x is my censoring once again)

Also if I try this it does this:
xxxxxxx@xxxxxxxx:~$ sudo ifup ra1
Ignoring unknown interface ra1=ra1.

xxxxxxx@xxxxxxxx:~$ sudo ifdown ra1
ifdown: interface ra1 not configured

---

### Post by amniarix on 2007-04-26
Yes, that's bash not liking the exclamation mark:

jturner@psyche:~$ echo "hello!"
bash: !": event not found

You need to quote it in single quotes, eg:

sudo iwconfig ra1 essid 'foo!bar'

---

### Post by jerathim on 2007-04-26
ra1       RT61 Wireless  ESSID:"XXX"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Bit Rate=24 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=47/100  Signal level:-75 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 Cell 01 - Address: XXX
                    ESSID:"XXX"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Quality:80/100  Signal level:-34 dBm  Noise level:-256 dBm

It's working so far!

Uh oh:

X@X:~$ sudo route add default gw 192.168.1.1
X@X:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 ra1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

Not working
Can't ping router

---

### Post by amniarix on 2007-04-26
> **jerathim said:**
> 
X@X:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 ra1


You've got two routes for 192.168.1.x there. Delete the eth0 one - "sudo route del -net 192.168.1.0 netmask 255.255.255.0 eth0"

---

### Post by jerathim on 2007-04-26
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 ra1
link-local      *               255.255.0.0     U     1000   0        0 ra1
default         192.168.1.1     0.0.0.0         UG    0      0        0 ra1
adam808@adam808u:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.111 icmp_seq=1 Destination Host Unreachable
From 192.168.1.111 icmp_seq=2 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, +2 errors, 100% packet loss, time 3010ms
, pipe 2

Also, I put in the Interfaces lines and I can reboot and get up to where I was. It still shows signal being received with a quality of 100/100.
It just can't ping the router. Also, I got Soft CPU Lockup and had to shutdown fully before it cleared.

I looked in the kernel and message logs but did not see anything very helpful about what went wrong. It just showed where the module loads and what driver it is (rt61 1.1.0 CVS from serialmonkey), and shows both the wireless and eth saying that there is no IPv6 router. Also here is the ID of my card from Messages: Vendor = 0x1814, Product = 0x0301

---

### Post by whitie on 2007-04-26
Hi there,

I followed the solution for RT61 and WPA from here [http://ubuntuforums.org/showthread.php?t=415693]("http://ubuntuforums.org/showthread.php?t=415693")
It works fine, but in ifconfig there is a bunch of collisions, Im not sure if this is normal. Plus I think I might like to try this fix as using native ubuntu would definately be better long term.

My problem is that now my "modinfo rt61" shows ...../kernel/drivers/net/rt61/rt61.ko rather than the one as default in feisty which is under ..../ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko. How do I go back to using this driver rather than the one installed?

Thanks.

---

### Post by jhpope on 2007-04-26
copy and overwrite that file whith the one you modified.


I am still having problems with the op's instructions on getting to ping the router.

---

### Post by spacedoubtman on 2007-04-26
Hello,

Before upgrading to feisty I had everything working with the 3rd party RT61STA driver as in amniarix's post. Since that won't build anymore I tried using iwconfig and iwpriv and it seems to work but its not.

Windows sees the network and can connect to it but I cannot ping or use the internet.

I turned off the firewalls (on the windows and linux boxes) and I turned off encryption, ie. iwconfig key off it still doesn't work.

The main difference I am using an Ad-Hoc connection.

Any ideas?
 -- I'm going to try whitie's suggestion. It would be better though if the ubuntu drivers worked :(

Thanks,
Adam

---

### Post by fvig2001 on 2007-04-26
For some reason it only works mostly on the live cd of course during that time it was still ra0.  I was able to at least ping my router. When I performed a clean install of feisty, it stopped working for me. My wireless card was set as ra1 and i couldn't even ping my router. Any help would be nice. :D

---

### Post by aditseng on 2007-04-27
I have an odd problem that no one else seems to have. I managed to set up my DLink G630 with WPAPSK following these instructions, and I can connect and browse.

The odd thing is that the card randomly turns off and on. ifconfig and iwconfig show correct information, but I can no longer ping anything. If I do an ifdown followed by an ifup it works fine... Any suggestions?

---

### Post by briggsy on 2007-04-28
Excellent, that worked just great, thanks.

I had ra1 instead of ra0, but that was no great issue.

```
auto ra1
iface ra1 inet dhcp
pre-up iwconfig ra1 essid kittah
pre-up iwpriv ra1 set AuthMode=WPAPSK
pre-up iwpriv ra1 set EncrypType=AES
pre-up iwpriv ra1 set WPAPSK="stroke the kittah or fear the pain of eternal abba, vile putrid cretin"
```


I found you have to put the EncrypType before the WPAPSK.

I am using a DLink DWL-D510 (writing that for other users who may search Google like I did for a long time) with ralink chipset (I hear some of them have atheros chipsets). I was most annoyed that WPA wasn't supported by the Gnome Network Manager thing for this chipset, but now it is sorted so I don't care.

---

### Post by ushills on 2007-04-30
How do I disable my eth0,  things work fine and the route is correct, however, after a few minutes when I type in route the eth0 has the same route as ra1 (192.168.1.1) then the system crashes.

Where do I prevent eth0 loading, can I just remove it from the interfaces file.

---

### Post by jhpope on 2007-04-30
arghhh...still can't ping my router!

@briggsy - setting the encryptyp before the wpapsk didn't help...i set it to tkip...does it matter what you set it to?

---

### Post by ushills on 2007-04-30
> **jhpope said:**
> arghhh...still can't ping my router!

@briggsy - setting the encryptyp before the wpapsk didn't help...i set it to tkip...does it matter what you set it to?

Have you checked your route settings, you should only have settings in their for ra0 or ra1, I had to delete all those for eth0.

---

### Post by jhpope on 2007-04-30
Question to anyone who has gotten this to work. What wireless card are you using? I have an edimax ew-7128g. Looking at the specs from newegg it looks like it uses AES for WPA [[link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041")]. So should i set the encryptype to AES instead of TKIP? Is the encryp time determined by the card or the router?

I'm at work now so maybe I'll try AES when I get home.

---

### Post by jhpope on 2007-04-30
ok so this is what i get when i follow the instructions


```
jhpope@jhpope-desktop:~$ lsmod | grep rt61
rt61                  251536  1 
jhpope@jhpope-desktop:~$ modinfo rt61
filename:       /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko
license:        GPL
description:    Ralink RT61 802.11abg WLAN Driver 1.1.0 CVS CVS
author:         http://rt2x00.serialmonkey.com
srcversion:     180F8980D3385B365E8F654
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.20-15-generic SMP mod_unload 
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)
parm:           ifname:Network device name (default ra%d) (charp)

jhpope@jhpope-desktop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:EB:D3:DF   
          Bit Rate=24 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=46/100  Signal level:-73 dBm  Noise level:-103 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jhpope@jhpope-desktop:~$ sudo ifconfig ra1 down

jhpope@jhpope-desktop:~$ 
jhpope@jhpope-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:92:21:01:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0x4000 

eth0:avah Link encap:Ethernet  HWaddr 00:1A:92:21:01:71  
          inet addr:169.254.3.219  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3628 (3.5 KiB)  TX bytes:3628 (3.5 KiB)

jhpope@jhpope-desktop:~$ sudo iwconfig ra1 essid nomenclature
jhpope@jhpope-desktop:~$ sudo iwpriv ra1 set AuthMode=WPAPSK
jhpope@jhpope-desktop:~$ sudo iwpriv ra1 set WPAPSK="mykey"
jhpope@jhpope-desktop:~$ sudo iwpriv ra1 set EncrypType=AES

jhpope@jhpope-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"nomenclature"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=47/100  Signal level:-75 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jhpope@jhpope-desktop:~$ sudo ifconfig ra1 192.168.1.6 netmask 255.255.255.0 up

jhpope@jhpope-desktop:~$ ifconfig ra1
ra1       Link encap:Ethernet  HWaddr 00:0E:2E:B2:F0:E2  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:feb2:f0e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:1000 
          RX bytes:147424 (143.9 KiB)  TX bytes:312 (312.0 b)
          Interrupt:17 

jhpope@jhpope-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 ra1
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0

jhpope@jhpope-desktop:~$ sudo route del default
jhpope@jhpope-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 ra1
link-local      *               255.255.0.0     U     0      0        0 eth0

jhpope@jhpope-desktop:~$ sudo route add default gw 192.168.1.1

jhpope@jhpope-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 ra1
link-local      *               255.255.0.0     U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 ra1
jhpope@jhpope-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.6 icmp_seq=1 Destination Host Unreachable
From 192.168.1.6 icmp_seq=2 Destination Host Unreachable
From 192.168.1.6 icmp_seq=3 Destination Host Unreachable

[1]+  Stopped                 ping 192.168.1.1
jhpope@jhpope-desktop:~$ 
```

Also attached a thumbnail. can anyone help?!

---

### Post by omegahelix on 2007-05-02
OMG it finally works!

Kernel: 2.6.20-15-generic
OS:     Ubuntu 7.04 x86 32-bit
Card:   Linksys WRT54G v4.1
Driver: SerialMonkey rt61-1.1.0-b2

Download the driver
make it as root
make install it

$mkdir /etc/Wireless/RT61STA
$cp *.bin from rt61 driver ¨Modules¨ folder to /etc/Wireless/RT61STA

add the following to /etc/network/interfaces:

# The wireless driver - installed by JA 5/2/07
#auto ra0

iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "omegahelix"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="password"
pre-up ifconfig ra0 up

Do an ifup ra0

Boo-yah!

---

### Post by dahen on 2007-05-03
Thank you. This worked, and I like using shipped drivers, which means no re-compilation with each kernel upgrade. However, I reverted back to using RT-drivers (patched according to <[rt61 and Ubuntu Feisty Fawn, 7.04, WPA-PSK problems solved]("http://ubuntuforums.org/showthread.php?p=2583542")>).

The reason is that I sometimes needed to do two or three ifdown ifup with this version before it worked. And since I needed that each boot and didn't want to put an arbitrary number of ifup/ifdown in my boot scripts, I reverted to RT-drivers, which have worked without any problems.

---

### Post by regomodo on 2007-05-03
hmm, can't get any further than 

$sudo iwpriv ra1 set Authmode=WPAPSK

it returns

Interface doesn't accept private ioctl...
set  (8BE2) : Invalid argument

Grrr

---

### Post by dahen on 2007-05-03
Are you sure you didn't by accident write EncryptType when it should be EncrypType?
I did that first and got the same error as you.

---

### Post by regomodo on 2007-05-03
thats the next step. Didn't get that far

Tried again doubly checking the steps and still get the same message.

It's a clean install and i haven't touched any files yet(except for changing 1 number in the xorg)

EDIT: typing error. I was typing Authmode instead of AuthMode

---

### Post by regomodo on 2007-05-03
hmm. now at step 1.5

instead of

$ubuntu@ubuntu:~$ ping google.com
ping: unknown host google.com

i get

"ubuntu@ubuntu:~$ ping google.com
connect: Network is unreachable

On a previous attempt it was normal and i did the folowing step. 

 ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# echo "nameserver 192.168.0.1" >> /etc/resolv.conf

i used

$ root@ubuntu:/home/ubuntu# echo "nameserver 192.168.1.1" >> /etc/resolv.conf

am i supposed to use the essid instead of "nameserver" ?

---

### Post by regomodo on 2007-05-03
cheers. Was praying it'd work. It didn't

God almighty. If it never worked with no security on my router then it'll never work with WEP/WPA, although i did manage to ping my router successfully in WPA

---

### Post by wilk on 2007-05-03
Thanks a lot, it's working perfectly. I'm using a dhcp configuration so my interfaces file look like : 

auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid my_essid
pre-up iwpriv ra0 set WPAPSK="my_pass_key"

My card is a MSI PC60G for those interested.

---

### Post by jhpope on 2007-05-03
did you guys get it working w/ the op's instructions or omegahelix's instructions?

---

### Post by regomodo on 2007-05-03
> **jhpope said:**
> did you guys get it working w/ the op's instructions or omegahelix's instructions?

i tried both. The thread starter's guide gave best results (i was able to ping the router no probs). The 2nd guy's one installed ok but it didn't work

---

### Post by N/A on 2007-05-04
Wee ! :popcorn: 
This is my first post from my cableless pc :)
Thanx for the how to, it work perfect, i only had to make minor modifications as i have ra1 instead of ra0  :)


\\:D/  \\:D/  \\:D/

---

### Post by regomodo on 2007-05-04
Aha!

I don't know what  did but it eventually works!

I think it may have been using DHCP instead of a static IP


freaking awesome!

---

### Post by mrmonday on 2007-05-05
I have just tried these steps, but I can not connect to my network. Where you say "I can now ping the router(if you can ever ping a router, congratulations, the worst is over):"

I can not ping the router. I continued the steps, and restarted, but still no luck. What can I do?

Thanks.

---

### Post by regomodo on 2007-05-07
**I'd like to state that none of these guides work in Xubuntu Feisty. **

The card is recognised in LSPCI but it does not do it's usual blinky thing scanning for networks. All LED's are off

Tried OMEGAHELIX's way of doing it. Doesn't work

Tried OP's guide. iwlist scan tells me that my network is down


Hrrmmph. My lappy isn't quite powerful enough for Ubuntu. Want to put Xubuntu on it instead on a better HDD

EDIT: By using the drivers Omegahelix referred to and setting up interfaces in the manner Wilk did, i am now able to see wireless networks. The link quality to my network is > 0 but i cannot ping my router. However, for some reason, i am able to ping a networked windows PC
EDIT2: OK, all sorted using above technique although it takes a while to connect to internet ~5mins. I can live with that for now

---

### Post by wilk on 2007-05-13
For those experiencing the BUG CPU#0 soft lockup and its random freezes, installing the latest cvs from serialmonkey (rt61-cvs-2007051302) seems to have solved it so far.:) It's supposed to fix the problem with SMP-enabled kernel, which is the default with Ubuntu.

---

### Post by jbullfrog on 2007-05-23
As of today, May 23, this is the only dirver I see on the website: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

RT61_Linux_STA_Drv1.1.0.0.tar

Is this ok to use instead?

---

### Post by jhpope on 2007-05-23
i believe that is the one that is shipped with feisty...you could try one of the betas...i still haven't gotten my edimax 7128g working

---

### Post by sk545 on 2007-05-24
How do i get this to work with WPA2-PSK AES?  I tried to put in the paramater as WPA2PSK, but that gave some ioctl error.

---

### Post by sk545 on 2007-05-27
For some reason, my /etc/network/interfaces keeps getting overwritten.  I put in all the commands that i want, but after a reboot, i can't connect and the interfaces file has different info inside of it for ra0.

---

### Post by rogerln on 2007-05-28
The HOWTO was most useful allowing for a couple of changes which match my system. I wanted to use WPA2 with AES encryption as that was what I had set up for my PC using that other OS that shall remain nameless. Setting the AuthMode to WPA2PSK and EncrypType to AES sorted that though and now all seems fine.

One puzzle remains though - I changed to Feisty from Dapper because I thought networkmanger did support WPA and the first time I tried to use it after a bit of playing around a WPA dialog was displayed and seemed to work fine but at that time my AP was open and I didn't want to leave it that way. When I secured it the next day and then tried to connect in Kubuntu all I could get was the WEP dialog - not a lot of use. However the fact remains the WPA dialog did appear previously, very strange. It does suggest that it should be possible to get networkmanager working properly though.

In the meantime many thanks for the help.:D

---

### Post by regomodo on 2007-06-01
I thought i'd post my method. It combines a few peoples' guides here

1. Download the driver from - 

[http://prdownloads.sourceforge.net/rt2400/rt61-1.1.0-b2.tar.gz?download](http://prdownloads.sourceforge.net/rt2400/rt61-1.1.0-b2.tar.gz?download)

2. Extract the driver using full paths to wherever you want

3. Open terminal and "cd" (change directory) to the "./Module"  folder of the driver

4. Install the driver

$ sudo make
$ sudo make install

5. copy needed files 

$mkdir /etc/Wireless/RT61STA
$cp *.bin from rt61 driver ¨Modules¨ folder to /etc/Wireless/RT61STA

6. edit interfaces file

$  sudo gedit /etc/network/interfaces

add at the bottom [editing the correct bits]

> auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid my_essid
pre-up iwpriv ra0 set WPAPSK="my_pass_key"

[For me i had to replace ra0 with ra1. Do an "ifconfig" to see what your install sees the card as.]

7. Reboot computer [yes you can do an ifup/ifdown but i found this more reliable]

$ sudo reboot -n

8. Sort out the routes [Sometimes i didn't have to do this. Sometimes i do. No idea why.]

$ sudo route del default
$ sudo route add default gw 192.168.1.1 [varies with router]

9. All done! Hopefully.

---

### Post by boudders on 2007-06-02
I am very impressed with your guide! I have been tweaking with my RT2600 and Ubuntu 7.04 for weeks, and your guide is definitely the most comprehensive.

Though I am still having some trouble;

I followed the steps up until I pinged the router, to which I get no reply. I did notice something strange. 

```

reydrekam@SauceBox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:"TheWomb"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-35 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

You will notice my link quality is 100/00 but when I run iwlist I get:

```
reydrekam@SauceBox:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
  
          Cell 01 - Address: 00:18:39:42:89:FA
                    ESSID:"Free Internet"
                    Mode:Managed
                    Channel:5
                    Encryption key:on
                    Quality:0/100  Signal level:-74 dBm  Noise level:-256 dBm

```

The quality link is 0/100

Any ideas?

---

### Post by takuzinis on 2007-06-05
I had one of the cases people having here that after all steps I was not been able to ping the router. Another result was that network interfaces file is completely messed up. 

Mostly peple have dhcp therefore I would suggest instead going all the iwconfig, ifconfig, route and ping sequences you simply:

**Step 1**

```

ubuntu@ubuntu:~$ sudo gedit /etc/network/interfaces

```

Delete everything related to ra0 (or ra1) and around that.

**Step 2**

Add at the beginning of /etc/network/interfaces following:

```

auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid my_essid
pre-up iwpriv ra0 set WPAPSK="my_pass_key"

```

In my case it was:

```

auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid ZEB
pre-up iwpriv ra0 set WPAPSK="zebiekste"

```

*use ra1 instead of ra0 if necessary

**Step 3**

Reboot

**Start browsing**

---

### Post by mathew.chacko on 2007-06-06
I have Edimax EW-7108PCg PCMCIA Wireless Lan Cardbus adapter

Why I cannot configure for WPA, when Encryption key is on, I see Quality = 0/100
at the moment I am only able to connect to "FON_AP" access point.
  
> 
          Cell 05 - Address: 00:14:C1:0D:A1: D4
                    ESSID:"getfirefox.com"
                    Mode:Managed
                    Channel:11
                    Encryption key: on
                    Bit Rates:11 Mb/s
                    Quality:0/100  Signal level:-54 dBm  Noise level:-256 dBm
          Cell 06 - Address: 00:18:4D:69:08:02
                    ESSID:"ubuntu"
                    Mode:Managed
                    Channel:11
                    Encryption key: on
                    Bit Rates:1 Mb/s
                    Quality:0/100  Signal level:-38 dBm  Noise level:-256 dBm
          Cell 07 - Address: 00:19:5B:B3:CA:E9
                    ESSID:"SK-Servette"
                    Mode:Managed
                    Channel:11
                    Encryption key: on
                    Bit Rates:1 Mb/s
                    Quality:0/100  Signal level:-78 dBm  Noise level:-256 dBm
          Cell 08 - Address: 00:18:84:1E:41:91
                    ESSID:"FON_AP"
                    Mode:Managed
                    Channel:1
                    Encryption key: off
                    Bit Rates:11 Mb/s
                    Quality:96/100  Signal level:-48 dBm  Noise level:-256 dBm


---

### Post by brodiepearce on 2007-06-07
> **takuzinis said:**
> I had one of the cases people having here that after all steps I was not been able to ping the router. Another result was that network interfaces file is completely messed up. 

Mostly peple have dhcp therefore I would suggest instead going all the iwconfig, ifconfig, route and ping sequences you simply:

<snip>


I had the same issue, iwconfig would display 97/100 for signal strength, however I couldn't ping the router, just skipping straight to the /etc/network/interfaces file as you suggested didn't yield any returns either.  What's more, I couldn't even get it connected on WEP after WPA refused to work. :O

---

### Post by anywebloco on 2007-06-08
Thanks very much - this worked for me.

But I still have a problem - I can't access my router using a web browser! I can telnet into it, but I'd rather use the web-interface.

Any suggestions?

---

### Post by PlainShane on 2007-06-09
Thank you so very much! I followed your guide after hours of work from others and this one worked like a charm. Just downloaded Ubuntu today (had to see what the hype was about) and had a blast today through the frustration troubleshooting and finally reaching this payoff of it all working!

Yay. Now, to scour these forums to trick this OS out. Peace

Note: If I click on the NetManager icon in the upper right then it all goes down and I have to do sudo ifdown ra1 then sudo ifup ra1. I need to figure out how to not load that at startup... Learning this OS will be fun for the summer.

---

### Post by Alamar on 2007-06-11
Thanks very much to amniarix for posting this HOWTO - I'd previously been using Ralink's drivers with Edgy, and am now very glad not to have to keep using them for Feisty (and recompiling with each new kernel!).

I ended up with a slightly different process to that given in the first post, partly because I'm in the UK and am using one of the 'non-US' channels (number 13).  This meant, among other things, that 'iwlist scan' couldn't initially see my network!

I therefore used iwpriv to add a few more settings I thought should be present from my old Ralink configuration file that I used with Edgy.  Below is the ra0 entry in my current /etc/network/interfaces file, which works a treat.

```
# The wireless network interface
auto ra0
iface ra0 inet static
        address 192.168.0.3
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1
        dns-search myDomain
        pre-up iwpriv ra0 set CountryRegion=1
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set NetworkType=Infra
        pre-up iwconfig ra0 essid mySSID
        pre-up iwpriv ra0 set WPAPSK=longpasswordgoeshere

```

The 'CountryRegion=1' line tells the interface to look on channels 1-13 and the 'NetworkType=Infra' should allow the interface to only connect to infrastructure access points (i.e. not computer-to-computer / adhoc mode).  The network, broadcast and dns-search lines are hangovers from a previous HOWTO-ified setup - I'm not sure if they're needed, but they don't appear to be doing any harm.

I also found that I had to restart the computer to correctly load this configuration; using just ifup at the command line brought ra0 up, but 'iwlist scan' constantly displayed my network as having a link quality of 0/100 and I was unable to ping the router.  Not sure why this was the case.

---

### Post by boesl on 2007-06-13
> **amniarix said:**
> [SIZE=3][B]
1.3) Configure ra0's IP details[/B][/SIZE]

Now configure the ra0 interface's IP. I am using a static IP here (192.168.0.102, randomly picked from the my valid 192.168.0.x range):

```
 ubuntu@ubuntu:~$ sudo ifconfig ra0 192.168.0.102 netmask 255.255.255.0 up
ubuntu@ubuntu:~$ ifconfig ra0
ra0 Link encap:Ethernet HWaddr 00:08:A1:A3:C2:B0
inet addr:192.168.0.102 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::208:a1ff:fea3:c2b0/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5179 errors:0 dropped:0 overruns:0 frame:0
TX packets:12548 errors:0 dropped:0 overruns:0 carrier:0
collisions:1 txqueuelen:1000
RX bytes:554229 (541.2 KiB) TX bytes:3850 (3.7 KiB)
Interrupt:16

ubuntu@ubuntu:~$ 
```


Hello!

Thank you for your post, it is very simple to understand. The only thing I don't know, how to configure the interface's IP with DHPC.

Can you please  write an easy and small direction? 

Thank you.

---

### Post by fenwik on 2007-06-13
Instead of using:
sudo ifconfig ra0 192.168.2.54 netmask 255.255.255.0 up

use:
sudo ifconfig ra0 dynamic up

---

### Post by boesl on 2007-06-13
Hello!

I've done all steps before, but at *1.2 Configure ra0 with iwconfig and iwpriv. *I have no idea:

> **amniarix said:**
> 
[SIZE=3][B]
1.2) Configure ra0 with iwconfig and iwpriv.[/B][/SIZE]

```
 ubuntu@ubuntu:~$ sudo iwconfig ra0 essid WHALENET
ubuntu@ubuntu:~$ sudo iwpriv ra0 set AuthMode=WPAPSK
ubuntu@ubuntu:~$ sudo iwpriv ra0 set WPAPSK="My secret WPA key"
ubuntu@ubuntu:~$ sudo iwpriv ra0 set EncrypType=TKIP
ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"WHALENET" Nickname:""
Mode:Managed Frequency:2.462 GHz Access Point: 00:0F:B5:1D:C2:CE
Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=85/100 Signal level:-50 dBm Noise level:-79 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ubuntu@ubuntu:~$ 
```

Make sure that ESSID has taken the value you set it to. If the interface is working, the 'Link Quality' should be something other than 0/100.

Not working? Then check if the wireless network is even visible with 'iwlist scan':


Here is my iwlist scan:

```
boesl@boesl:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra1       Scan completed :
          Cell 01 - Address: 00:17:9A:F2:A3:AF
                    ESSID:"Heimann"
                    Mode:Managed
                    Channel:10
                    Encryption key:on
                    Quality:66/100  Signal level:-69 dBm  Noise level:-256 dBm

boesl@boesl:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra1       No scan results
boesl@boesl:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra1       Scan completed :
          Cell 01 - Address: 00:17:9A:F2:A3:AF
                    ESSID:"Heimann"
                    Mode:Managed
                    Channel:10
                    Encryption key:on
                    Quality:0/100  Signal level:-67 dBm  Noise level:-256 dBm

boesl@boesl:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra1       Scan completed :
          Cell 01 - Address: 00:17:9A:F2:A3:AF
                    ESSID:"Heimann"
                    Mode:Managed
                    Channel:10
                    Encryption key:on
                    Quality:58/100  Signal level:-67 dBm  Noise level:-256 dBm

boesl@boesl:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra1       Scan completed :
          Cell 01 - Address: 00:17:9A:F2:A3:AF
                    ESSID:"Heimann"
                    Mode:Managed
                    Channel:10
                    Encryption key:on
                    Quality:64/100  Signal level:-67 dBm  Noise level:-256 dBm

boesl@boesl:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra1       Scan completed :
          Cell 01 - Address: 00:17:9A:F2:A3:AF
                    ESSID:"Heimann"
                    Mode:Managed
                    Channel:10
                    Encryption key:on
                    Quality:0/100  Signal level:-69 dBm  Noise level:-256 dBm

boesl@boesl:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra1       Scan completed :
          Cell 01 - Address: 00:17:9A:F2:A3:AF
                    ESSID:"Heimann"
                    Mode:Managed
                    Channel:10
                    Encryption key:on
                    Quality:59/100  Signal level:-69 dBm  Noise level:-256 dBm

```

I don't understand why the link quality isn't stable or there are no scan results for interface ra1.
Does anybody know what's the problem?

At the point 1.4 Configure Routes i've also problems, but i think they belong together.

```
boesl@boesl:~$ route
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
boesl@boesl:~$ sudo route del default
boesl@boesl:~$ sudo route add default gw 192.168.0.1
SIOCADDRT: Network is unreachable


```

Thank you.

---

### Post by boesl on 2007-06-14
Is there no solution for my problem, i can't belive.

I think most of the people use wlan with DHCP or?

---

### Post by AwesomeSauce on 2007-06-22
Sorry if this is a stupid question, but am I supposed to add quotes to my shared key like in the tutorial? Also in the writing the resolv.conf? Do I put in my key as xxxxxxx, or "xxxxxxxx" ?

The problem I am having is that I can ping my router, that's all good, but then after writing resolv.conf I can't ping google.com as the tutorial says. Help?

**edit:** I got it working. I just didn't use quotes when making the resolv.conf. Score!

---

### Post by murmelhunter on 2007-06-26
Well I have a working solution for you, currently I'm using D-Link DWL-G630 Version E2 Firmware 5.0.

The card is using the RT61 chipset means that the solution below may will work also for branded cards. 

I have here a configuration sample for you which allows you to use the card with WPA on automatic dhcp mode. 

To get started:

The beginning is like what I found at this entry:
[http://ubuntuforums.org/showthread.p...light=ethernet](http://ubuntuforums.org/showthread.p...light=ethernet)

1) Manual Configuration

After booting the live CD, or after a clean install, you will see Ubuntu has an interface for the network card already configured:

Code:

ubuntu@ubuntu:~$ ifconfig ra0
ra0 Link encap:Ethernet HWaddr 00:08:A1:A3:C2:B0
inet6 addr: fe80::208:a1ff:fea3:c2b0/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2248 errors:0 dropped:0 overruns:0 frame:0
TX packets:9630 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:235262 (229.7 KiB) TX bytes:0 (0.0 b)
Interrupt:16

ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"" Nickname:""
Mode:Managed Frequency:2.412 GHz Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=0/100 Signal level:-121 dBm Noise level:-111 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

However, as ra0 is unconfigured (ESSID:"", etc), the network connection isn't working. We need to configure it manually. Interface configuration is done with 'ifconfig'. Wireless interfaces need additional configuration with 'iwconfig' and 'iwpriv'.


1.1) Disable the ra0 interface

First thing to note is that if the interface is enabled (listed in 'ifconfig' output), your iwconfig/iwpriv changes won't take effect:

Code:

ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"" Nickname:""
Mode:Managed Frequency:2.412 GHz Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=0/100 Signal level:-121 dBm Noise level:-111 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ubuntu@ubuntu:~$ sudo iwconfig ra0 essid WHALENET
ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"" Nickname:""
Mode:Managed Frequency:2.412 GHz Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=0/100 Signal level:-121 dBm Noise level:-111 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ubuntu@ubuntu:~$

(note no change to ESSID)

So first bring down the ra0 interface:

Code:

ubuntu@ubuntu:~$ sudo ifconfig ra0 down
ubuntu@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:16:177:AC:C1
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:17 Base address:0x6000

eth0:avah Link encap:Ethernet HWaddr 00:16:177:AC:C1
inet addr:169.254.9.63 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:17 Base address:0x6000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:20 errors:0 dropped:0 overruns:0 frame:0
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1432 (1.3 KiB) TX bytes:1432 (1.3 KiB)

ubuntu@ubuntu:~$

Notice that the ra0 interface is gone.


1.2) Configure ra0 with iwconfig and iwpriv.

Now we want to configure the ra0 interface so it connects to the wireless network. I am using WPA with a shared key (WPA PSK), connecting to a network called WHALENET. Your essid and WPAPSK will be different (possibly other settings too, but start with those).

Code:

ubuntu@ubuntu:~$ sudo iwconfig ra0 essid WHALENET
ubuntu@ubuntu:~$ sudo iwpriv ra0 set AuthMode=WPAPSK
ubuntu@ubuntu:~$ sudo iwpriv ra0 set WPAPSK="My secret WPA key"
ubuntu@ubuntu:~$ sudo iwpriv ra0 set EncrypType=TKIP
ubuntu@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

ra0 RT61 Wireless ESSID:"WHALENET" Nickname:""
Mode:Managed Frequency:2.462 GHz Access Point: 00:0F:B5:1D:C2:CE
Bit Rate=54 Mb/s
RTS thrff Fragment thrff
Link Quality=85/100 Signal level:-50 dBm Noise level:-79 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ubuntu@ubuntu:~$

Make sure that ESSID has taken the value you set it to. If the interface is working, the 'Link Quality' should be something other than 0/100.

Not working? Then check if the wireless network is even visible with 'iwlist scan':
Code:

ubuntu@ubuntu:~$ sudo iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

ra0 Scan completed :
Cell 01 - Address: 00:0F:B5:1D:C2:CE
ESSID:"WHALENET"
Mode:Managed
Channel:11
Encryption keyn
Quality:84/100 Signal level:-53 dBm Noise level:-256 dBm

ubuntu@ubuntu:~$


__________________________

So the card is working already now ping the router (if you can ever ping a router, congratulations, the worst is over) ( IP adrres of your router is available in the user guide of your router)

Code:

ubuntu@ubuntu:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=9.52 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.63 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=1.59 ms

double check now if you ping google

ubuntu@ubuntu:~$ ping google.com

Normally you should see something like this:

PING google.com(64.233.187.99) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=9.52 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.63 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=1.59 ms

Now comes the difference to save the info at the network interface.conf correctly

2) Automatic configuration on startup

We want to do all the above steps automatically when Ubuntu starts. The
/etc/init.d/networking script will invoke 'ifup', which in turn runs the
'ifconfig' and 'route' commands we performed manually above. ifup's
configuration file is /etc/network/interfaces.

So edit /etc/network/interfaces:

Code:

ubuntu@ubuntu:~$ sudo gedit /etc/network/interfaces

and at the beginning, add a section like:

Code:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface wlan0 inet dhcp
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto wlan0

iface eth0 inet dhcp

auto eth0

auto ra0

iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid WHALENET
pre-up iwpriv ra0 set WPAPSK="My secret WPA key"



Save the file Interface conf file.


Now unplug your lan cable and reboot while your D Link Card is plugged in and you will see your card working by using the WPA.

View points to add :
I have removed the Network manager completely ( can may overule some settings and done no tests with the network-manager yet.

You can monitor the wfifi connection with wifi-radar

If you see in wifi radar an old connection wifi setup please remove it and select the new connection.(it will be listed)

Normally everything should work now like a dream.

I'm using my card since yesterday (WPA with auto DHCP) and done 20 reboots without any problems.

I hope the solution is clear enough to help you too..

My special thanks goes to amniarix who gave me with his info at this forum as newbie a clear info understanding how to configure a RT61 chipset based wifi card.

Using currently Feisty fawn 7.04 with Beryl correctly configured on a Vaio GRZ 2.4 GHZ 512 MB Ram Ati Raedon mobilty 7500 32 MB and yes the graphic card does direct rendering

---

### Post by SarahKH on 2007-06-28
To the OP,

Blimey, that was easy enough.  One Edimax RT61 based card now on the wireless network.

Ta muchly.

---

### Post by jcw122 on 2007-06-30
It won't let me uninstall Network Manager...whats up w/ that?

---

### Post by murmelhunter on 2007-07-01
Small update

well after further testing and upgrading to Ubuntu studio I have due to the upgrade the Network manager back again.

The network manager is not configured for the wireless connection but the wifi card is still working on WPA due to the modified network.conf file.

---

### Post by jhpope on 2007-07-16
well I can FINALLY say I've joined the ranks of people who have gotten their RT61 wireless card working with WPA.

Decided to give it another go last night. Did a clean install of feisty, went straight to editing the interfaces. created the resolv.conf and pointed it to my router as the nameserver. didn't work, checked my route table, deleted and re-added the default for ra1...WORKS!!!

Thanks to the OP...i guess i over analyzed the instructions for months...it was real easy once I got it.

---

### Post by Ritariassa on 2007-07-16
I also got my rt61 working with WPA2. Thanks for the good how-to.

---

### Post by bigdave146 on 2007-07-17
Having a nightmare with this - see [http://ubuntuforums.org/showthread.php?t=415693&page=3]("http://ubuntuforums.org/showthread.php?t=415693&page=3")

Dave

---

### Post by jhpope on 2007-07-17
i didn't have to download any drivers from ratek or whatever that site was...only had to modify the interfaces and resolv.conf and route table

---

### Post by bigdave146 on 2007-07-17
Hi

I had it working OK on Edgy this morning on an install that had the drivers from Realtek compiled and installed but on a clean Feisty install it give the problem i mention in the other post.  Have tried blacklisting rt61pci in /etc/modules.d/blacklist but now i cant even set the essid on the card.

Dave

---

### Post by jhpope on 2007-07-17
the drivers shipped with feisty should work...that was the main point of this fix i believe...the fact that you didn't have to compile 3rd party drivers.

---

### Post by bigdave146 on 2007-07-17
Could the problem be that the drivers dont support WEP only WPA ?

Dave

---

### Post by jhpope on 2007-07-17
i believe you should be able to get wep no problem...the big problem was wpa...from what i remember at least

---

### Post by bigdave146 on 2007-07-17
Just some more info - my wireless router is a BT Homehub and i am in the UK.

I found the hardware list in the community docs and it says "Works only in Feisty if you put to "blacklist" the "rt61pci" module BEFORE install the card. If not, your computer will freeze often. There is an other module: "rt61" it works fine, with WEP too. " (I have Linksys WMP54g 4.1)

Am reinstalling now with the card removed and will blacklist it, shutdown then install the card,

---

### Post by bigdave146 on 2007-07-17
I just reinstalled again with Feisty and the card removed.  Entered rt61pci into /etc/modules.d/blacklist and rebooted.  All OK.  Powered off, inserted card and booted up.  Card recognised as ra0 from ifconfig.

Did the ifconfig ra0 down, iwconfig, iwlist, etc and AGAIN it hung the PC at the time i typed "iwconfig ra0 set EncrypType=WEP".  Damn thing.  Any ideas anyone ???????????  Must be something to do with the driver as this worked on Edgy.

Dave

---

### Post by jhpope on 2007-07-17
don't type them in manually...write the entry straight into the /etc/network/interfaces file...then reboot...then do the route stuff...then you should be up...thats how i did it...doing it step by step never worked for me

---

### Post by bigdave146 on 2007-07-17
Just did that and it hangs on bootup, i assume at the same place.  This is doing my nut in now......all I want is my MythTV server back......

---

### Post by bigdave146 on 2007-07-17
Right I have changed the wireless to WPA and it now worked first time.  I am able to see google, etc, and have a DHCP issued IP address.  There must be some sort of bug with WEP on the drivers provided.

Dave

---

### Post by shreddi on 2007-07-27
Just to mention it: This Howto works perfectly with D-Link DWL-G510 (RaLink RT2561/RT61 rev B 802.11g).
Some strange things:
*) Booting the liveCD, it fails, if I type 
```
sudo iwpriv ra0 set EncrypType=TKIP
```
after 
```
sudo iwpriv ra0 set WPAPSK="My secret WPA key"
```
But it still works in /etc/network/interfaces .. so who cares ;)
And it doesnt work with ```
sudo iwpriv ra0 essid WHALENET
```, I made the mistake to use iwpriv here instead of iwconfig, which just didnt work.
If you dont mind havin no fancy pop-up graphical management tool, this is the best out-of-the-box solution I tried.

Edit: Warning!! If you use the rt61 driver, that comes with feisty, you will most probably encounter a very unstable system. For example see [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90243]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90243"). Use the driver provided by serialmonkey.com instead, but they are also buggy on debian and derived systems.

---

### Post by dpm on 2007-07-28
In case it helps anyone, here's my configuration (WPA2):

```
auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPA2PSK
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwconfig ra0 essid My_ESSID
pre-up iwpriv ra0 set WPAPSK="My secret WPA key"
```for those using WPA instead of WPA2, this also seemed to work for me:

```
auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid My_ESSID
pre-up iwpriv ra0 set WPAPSK="My secret WPA key"
```I've got a Conceptronic C54RC PC Card with the default rt61 driver that comes with Feisty.

Cheers.

---

### Post by BrendanM on 2007-08-24
I just wanted to say thanks to takuzinis on page 5, your instructions worked like a charm for me. Hooray encrypted wifi.

Edit: For benefit of others searching the forums, my card is a 07:00.0 Network controller: RaLink Ralink RT2600 802.11 MIMO as given by lspci | grep Ra  I am running the latest CVS version of the open source drivers because I was encountering the CPU lockup problem.

---

### Post by wilk on 2007-08-24
The trio rt61pci, rt2x00pci  and rt2x00lib modules work now out of the box in Gutsy (amd64 in my experience) for t rt61 card, with WPA, with nm-applet :) Hooray !

---

### Post by ForceAbuser on 2007-08-27
> **boesl said:**
> 

```
boesl@boesl:~$ route
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
boesl@boesl:~$ sudo route del default
boesl@boesl:~$ sudo route add default gw 192.168.0.1
**SIOCADDRT: Network is unreachable **


```


i second this very frustrating :(

my guess is that it will have to do something with the route couse of the return when i ping my router (192.168.2.1)
it doesnt make sense when it searches in the 169.254.5.147 subnet :-S very weird

```

ForceAbuser@ForceAbuser-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"default"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:50:18:4B:DB:C4   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=81/100  Signal level:-56 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ForceAbuser@ForceAbuser-ubuntu:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 169.254.5.147 icmp_seq=1 Destination Host Unreachable
From 169.254.5.147 icmp_seq=2 Destination Host Unreachable
From 169.254.5.147 icmp_seq=3 Destination Host Unreachable
From 169.254.5.147 icmp_seq=4 Destination Host Unreachable
From 169.254.5.147 icmp_seq=5 Destination Host Unreachable
From 169.254.5.147 icmp_seq=6 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6017ms
, pipe 3
ForceAbuser@ForceAbuser-ubuntu:~$ 

```

and i use 2 wireless networks, with diffrent settings (i use 1 for testing tough); when i finaly get the driver working, i would have to get into the terminal if i want to change to the other network... why is it so hard if the bloody driver is OSS???? :-S :(

this is the only reason why i havent changed from windows XP to ubuntu

---

### Post by Jadd on 2007-09-06
Thanks amniarix for that guide. People like you is what makes Ubuntu so great.

It didn't work at first, I had to disable eth's gateway completely (I think) and edit the /etc/network/interfaces file, but then it worked perfectly. So now I have two questions:

1. How do I encrypt my WPA password? Saving it in /etc/network/interfaces isn't very secure, is it?

2. How do I re-enable ethernet? Here's my /etc/network/interfaces file, if it helps:

```

auto ra1
iface ra1 inet static
address x.x.x.x #I replaced the real IP address with x for privacy reasons, is this overkill, by the way?
netmask 255.255.255.0
gateway x.x.x.x #same here
pre-up iwpriv ra1 set AuthMode=WPAPSK
pre-up iwpriv ra1 set EncrypType=TKIP
pre-up iwconfig ra1 essid Mynet
pre-up iwpriv ra1 set WPAPSK="password password" 

auto lo
iface lo inet loopback


iface eth0 inet static
address x.x.x.x #same here
netmask 255.255.255.0
gateway x.x.x.x #same here

#The rest has been disabled by me, it seemed to help
#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

#auto eth0
```

Thanks again!

---

### Post by penman242 on 2007-09-13
I have dhcp, so I used takuzinis' method (page 5 of this thread) for modifying /etc/network/interfaces on a feisty kde-core installation, and it worked great.  Now here is the but:

I took the wireless card (linksys wmp54g v4.1) and the hard drive out of the computer, to install another hard drive to test wireless with gutsy.  When I put my old feisty hard drive and the linksys card back it, it no longer connected to my wireless network.

Does anyone know how that could've happened and what to do about it?

Thanks in advance for any advice.

---

### Post by Anaphylaxis on 2007-09-21
> **briggsy said:**
> I found you have to put the EncrypType before the WPAPSK.

Great, now it is too late. How do start over without having to install (x)ubuntu again? Where does iwpriv write changes to?

My network doesn't show up after the first few steps of configuration, but the network is fine, cuz I can surf around with my palm tx, connecting with WPA. 

> 
me@ubuntu:~$ sudo iwconfig ra0 essid transporter
me@ubuntu:~$ sudo iwpriv ra0 set AuthMode=WPAPSK
me@ubuntu:~$ sudo iwpriv ra0 set WPAPSK=amoviequotethatiscool
me@ubuntu:~$ sudo iwpriv ra0 set EncrypType=TKIP
me@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:"transporter"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Now what do I do? Why do I get stuck right at the beginning. ARGH!!!!

---

### Post by gladstone on 2007-09-21
I get to this point:

```
sudo iwpriv eth1 set AuthMode=WPAPSK
Invalid command : set

```

how do I get round that?

---

### Post by Grafster on 2007-09-22
This worked -perfectly- for me and is 10x easier than the convoluted first post!
Brilliant!

Using DLink DWL-G630 AirLink Plus

> **takuzinis said:**
> I had one of the cases people having here that after all steps I was not been able to ping the router. Another result was that network interfaces file is completely messed up. 

Mostly people have dhcp therefore I would suggest instead going all the iwconfig, ifconfig, route and ping sequences you simply:

**Step 1**

```

ubuntu@ubuntu:~$ sudo gedit /etc/network/interfaces

```

Delete everything related to ra0 (or ra1) and around that.

**Step 2**

Add at the beginning of /etc/network/interfaces following:

```

auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid my_essid
pre-up iwpriv ra0 set WPAPSK="my_pass_key"

```

In my case it was:

```

auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid ZEB
pre-up iwpriv ra0 set WPAPSK="zebiekste"

```

*use ra1 instead of ra0 if necessary

**Step 3**

Reboot

**Start browsing**

---

### Post by save2 on 2008-06-17
page 1 works like a charm ! thanks !

---

### Post by dmitrijledkov on 2008-08-30
Does it work with network manager in Hardy?

---

