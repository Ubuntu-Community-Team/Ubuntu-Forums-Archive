---
title: "One more wireless Internet connection question from a noob..."
date: 2008-08-21
forum: New to Ubuntu
---

### Post by boulash on 2008-08-21
Hi everyone,
I just installed Ubuntu 8.04 on a Dell Lattitude D610, and I can't figure out the wireless connection part.
My router/modem is a Speedtouch 585i, and my provider Alice/Hansenet (in Germany).

I used the network manager, and everything seems to be working fine (my devices appear and seem to be functionning, IP address was generated, WEP key was accepted...).

From there, I could figure out how to authenticate my connection with my provider using the ADSL Ethernet connection (pppoeconf, etc...), and it works just fine, but I can't find how to do the same using the wireless connection.

As a result, when my Ethernet cable is unplugged, I can't access the Internet...How do I do this "authentication" step (using my provider username and password) ?

I would really appreciate some help on this, preferably through point-and-click instructions (but I can find the terminal if needed :) ).
Thanks in advance!

---

### Post by aloshbennett on 2008-08-21
Usually the authentication credentials are stored on the router. Is there a default router page you can access (192.168.1.1 or 1.2) ?

---

### Post by boulash on 2008-08-21
Ok,I've been good and I've done my homework, so here are some reports:


nathi@nathi-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
nathi@nathi-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f3:0210 Elan Microelectronics Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
nathi@nathi-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
nathi@nathi-laptop:~$ sudo lshw -C network
[sudo] password for nathi: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:c6:53:88
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5751-v3.29a latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:ef:89:84
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
nathi@nathi-laptop:~$ lsmod
Module                  Size  Used by
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
ppdev                  10372  0 
speedstep_centrino      9152  0 
cpufreq_conservative     8712  0 
xt_TCPMSS               5504  1 
cpufreq_ondemand        9740  1 
xt_tcpmss               3200  1 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
xt_tcpudp               4096  1 
cpufreq_userspace       5284  0 
iptable_mangle          3712  1 
freq_table              5536  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
sbshc                   7680  1 sbs
bay                     6912  0 
container               5632  0 
dock                   11280  1 bay
pppoe                  14528  2 
pppox                   4876  1 pppoe
ipv6                  267780  10 
ppp_generic            29588  6 pppoe,pppox
slhc                    7040  1 ppp_generic
iptable_filter          3840  0 
ip_tables              14820  2 iptable_mangle,iptable_filter
x_tables               16132  4 xt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
af_packet              23812  10 
lp                     12324  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
ieee80211_crypt_wep     6272  1 
joydev                 13120  0 
pcmcia                 40876  0 
hci_usb                16540  2 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
evdev                  13056  8 
dcdbas                  9504  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
irda                  203068  0 
crc_ccitt               3072  1 irda
ipw2200               146120  0 
serio_raw               7940  0 
ieee80211              35528  1 ipw2200
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                40336  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
pcspkr                  4224  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
button                  9232  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
battery                14212  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                      6916  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
intel_agp              25492  0 
agpgart                34760  2 drm,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_piix               19588  2 
ata_generic             8324  0 
ahci                   28420  0 
pata_acpi               8320  0 
libata                159344  4 ata_piix,ata_generic,ahci,pata_acpi
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
tg3                   116228  0 
usbcore               146028  5 hci_usb,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
nathi@nathi-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"ALICE-WLAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:7F:27:78:E5   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=82/100  Signal level=-48 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

ppp0      no wireless extensions.

nathi@nathi-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:c6:53:88  
          inet6 addr: fe80::214:22ff:fec6:5388/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3049590 (2.9 MB)  TX bytes:263666 (257.4 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:ef:89:84  
          inet6 addr: fe80::213:ceff:feef:8984/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6996 (6.8 KB)  TX bytes:5055 (4.9 KB)
          Interrupt:18 Base address:0x2000 Memory:dfbff000-dfbfffff 

eth0:avahi Link encap:Ethernet  HWaddr 00:14:22:c6:53:88  
          inet addr:169.254.6.159  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

eth1:avahi Link encap:Ethernet  HWaddr 00:13:ce:ef:89:84  
          inet addr:169.254.9.53  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x2000 Memory:dfbff000-dfbfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76292 (74.5 KB)  TX bytes:76292 (74.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:85.182.66.90  P-t-P:213.191.84.202  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2982065 (2.8 MB)  TX bytes:203920 (199.1 KB)

nathi@nathi-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:7F:27:78:E5
                    ESSID:"ALICE-WLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=79/100  Signal level=-50 dBm  
                    Extra: Last beacon: 2232ms ago

ppp0      Interface doesn't support scanning.

nathi@nathi-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



iface eth1 inet dhcp
wireless-key XXXXXXXXXXX
wireless-essid ALICE-WLAN



auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth1

iface eth0 inet dhcp

auto eth0
nathi@nathi-laptop:~$ nm-tool

NetworkManager Tool

State: connected

print_devices(): didn't get a reply from NetworkManager.
There are no available network devices.
nathi@nathi-laptop:~$

---

### Post by boulash on 2008-08-21
> **aloshbennett said:**
> Usually the authentication credentials are stored on the router. Is there a default router page you can access (192.168.1.1 or 1.2) ?

Thanks for your answer.
I've tried these two in my browser, it doesn't work (I get a network timeout).
I read about a similar solution in "Ubuntu for Dummies", but I guess I need a specific page... Shall I ask my provider for a default router page?

---

### Post by cariboo on 2008-08-21
The documentation should be on the cd you received when you got your router. It should tell you how to access the management page in your router.

Jim

---

### Post by caljohnsmith on 2008-08-21
Boulash, try the following:
```
route -n
```
On the line that begins with destination "0.0.0.0", there should be an entry for the "gateway." That should be the address of your modem/router. Just plug that address into your browser and see if you can get to your router's configuration web page.

---

### Post by boulash on 2008-08-22
This is what I get:

nathi@nathi-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.191.84.202  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

but it doesn't seem to be right, I get page load error.
I tried
213.191.84.202
169.254.0.0

I'll try to find the documents, might bring something...

Is all this supposed to be automatic? Or is this "pasting router address" a standard thing to do?
In Windows there was a function to configure my connection, isn't there something similar in Ubuntu?

Thanks a lot

---

### Post by caljohnsmith on 2008-08-22
I think your Speedtouch router uses a address of 192.168.1.254 by default. Try putting that into your web browser.

---

### Post by boulash on 2008-08-23
I also found this address on a Hansenet forum, but still nothing...

I changed my approach and tried "roaming mode".
I clicked on the network taskbar icon, chose my network, typed the wap key...still not connected, and after 5 minutes I'm asked for my key again.
The "network bar" gets to 60% or so, and then back to 0.

Is there a possibility that I'm chosing the wrong network or typing the wrong key?

---

### Post by nothingspecial on 2008-08-23
Are you choosing the correct security type in the drop down box, wep, wap etc?

---

### Post by boulash on 2008-08-23
> **nothingspecial said:**
> Are you choosing the correct security type in the drop down box, wep, wap etc?

I don't get WAP, only WEP (3 options : passkey, hex or ascii) or LEAP (no idea what that is).
the sticker on my router says it's hex, so I tried that, but the others don't work either.

---

### Post by boulash on 2008-08-24
bump

---

### Post by boulash on 2008-08-26
bump.
can anyone help?
I'm now using roaming mode, but I probably do something wrong.
Shouldn't it be automatic?

I also tried using wicd, didn't help, so I reinstalled network manager.

---

### Post by croniksoft on 2008-08-26
Can you run ifconfig and iwconfig once connected to your wireless network and paste here the results,from what i know i dont think is a ubuntu issue, i think it might be an issue with the way your router is configure.

---

### Post by nicedude on 2008-08-26
I have to inject an idea that I think would both solve your problems and is in my view a must for any broadband Internet connection. Buy a $40US Netgear or Linksys router with Wifi as then the new wifi router can handle your pppoe handshake login for you easily and you can then setup whatever wifi security ( WEP or WPA ) to your router in Ubuntu and it will work just fine. I think this is a must since even when you get a wifi router type modem from your provider they do not give you admin password to properly configure it and it could have any backdoor router pass that they were stupid enough to employ as well ( at least that is how it is in USA where I live ). So if you get a cheap router with wifi and just let it handle your ISP login then it wont matter what you connect to the new router as it will work no matter the OS and without PPPOE login setups. This is also a great extra layer of protection since it will be a security device that you have the admin password to and control :-)

Just my 2 cents.

---

### Post by boulash on 2008-08-26
Thanks, that's tempting, but what's a bit weird is that I don't get any problems to connect to our Wifi network using Windows.
But using Windows I had to configure the connection using my provider username and password.
I actually get the same problem with our Ipod touch: can't connect to our network, though it's clearly visible.

---

### Post by boulash on 2008-08-27
> **croniksoft said:**
> Can you run ifconfig and iwconfig once connected to your wireless network and paste here the results,from what i know i dont think is a ubuntu issue, i think it might be an issue with the way your router is configure.

here it is:

nathi@nathi-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:c6:53:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:ef:89:84  
          inet6 addr: fe80::213:ceff:feef:8984/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:220 (220.0 B)
          Interrupt:18 Base address:0xe000 Memory:dfbff000-dfbfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89100 (87.0 KB)  TX bytes:89100 (87.0 KB)

nathi@nathi-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"ALICE-WLAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:7F:27:78:E5   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=73/100  Signal level=-55 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2


I think it's a router problem too...
I might just buy one as suggested above.
Thanks for your trouble!

---

### Post by shane19174 on 2008-08-27
I don't think I would buy anew router just yet. Not if it works fine with Windows. But make sure you check that: if it doesn't work anymore, then call up Alice and get them to replace it (I only have experience with 1&1 and freenet, but they replaced one for me once without any hassle--picked up the old one when they brought the new one, so no downtime. You should be able to talk Alice into doing the same if there's really a hardware problem.) Anyway, assuming it still works with Windows, make detailed notes of all your configuration settings, including IP address (DHCP or static?), username and password, encryption type, etc. Then try again in Ubuntu. Yes, it should automatic, just as comfortable as in Windows once set up correctly.

Shane

---

