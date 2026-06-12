---
title: "wireless issue! please help"
date: 2012-07-29
forum: New to Ubuntu
---

### Post by sutibun on 2012-07-29
So my wireless was just fine but few day's ago i could not connect to the internet. I was able to connect to the router though!
Any ideas and solution's?

Thanks

---

### Post by wildmanne39 on 2012-07-29
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by sutibun on 2012-07-29
> **wildmanne39 said:**
> Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```by clicking on new reply and click # then paste the information between the brackets.
Thank you

TO AVOID ANY CONFUSE I WANNA MAKE CLEAR: I can see the wireless i can connect to it BUT i cant connect to the internet! 
(i have good signal)

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux nabi 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
 i686 i386 GNU/Linux

``````
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:011c]
    Kernel driver in use: tg3
--
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Kernel driver in use: b43-pci-bridge

``````
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 12d1:14ac Huawei Technologies Co., Ltd. 

``````
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wwan0     no wireless extensions.

ppp0      no wireless extensions.

```
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
Module                  Size  Used by
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
cdc_ether              13312  0 
usbnet                 25214  1 cdc_ether
option                 21205  2 
usb_wwan               19779  1 option
usbserial              37203  7 option,usb_wwan
usb_storage            44173  0 
uas                    17699  0 
rfcomm                 38408  0 
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
pcmcia                 39822  0 
arc4                   12473  2 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
b43                   318816  0 
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
mac80211              272785  1 b43
tifm_7xx1              12937  0 
psmouse                73673  0 
tifm_core              15040  1 tifm_7xx1
serio_raw              12990  0 
snd_seq_midi           13132  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
nsc_ircc               23240  0 
cfg80211              172392  2 b43,mac80211
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_rawmidi            25241  1 snd_seq_midi
i915                  505108  3 
irda                  185428  1 nsc_ircc
snd_seq_midi_event     14475  1 snd_seq_midi
crc_ccitt              12595  2 ppp_async,irda
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
binfmt_misc            17292  1 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
wmi                    18744  1 acer_wmi
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
tg3                   132972  0 
ssb                    50682  1 b43

```Thanks for the fast response.
I hope i did this right.
Thanks in advances

---

### Post by wildmanne39 on 2012-07-29
Hi, you did it right. Please do:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
Reboot
Thanks

---

### Post by sutibun on 2012-07-29
> **wildmanne39 said:**
> Hi, you did it right. Please do:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```Reboot
Thanks

Sorry for my late response but firmware reinstall failed 2 times (my current internet connection fails). So now i dont even have the firmware ( next to the wireless connections it says no firmware) Its ok to just intsall it again and reboot?or i will have to use the command you send to me?

---

### Post by wildmanne39 on 2012-07-29
Hi, you can just reinstall the firmware then reboot but I would use the commands, were you connected to the internet with a wired connection when you ran the commands?
Thanks

---

### Post by sutibun on 2012-07-29
> **wildmanne39 said:**
> Hi, you can just reinstall the firmware then reboot but I would use the commands, were you connected to the internet with a wired connection when you ran the commands?
Thanks

No i use broadband but 3 times now failed to reinstall it!
Ok i will try it for 4th time. If it fails again can i install them from synaptic?

Before the command you gave me i had the firmware.Just saying...

---

### Post by wildmanne39 on 2012-07-29
Hi, yes you can install it from synaptic but the command does the exact same thing, what errors are showing in the terminal?
Thanks

---

### Post by sutibun on 2012-07-29
> **wildmanne39 said:**
> Hi, yes you can install it from synaptic but the command does the exact same thing, what errors are showing in the terminal?
Thanks

```
bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

``````
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Ok  firmwate-b43-installer and b43-fwcutter  are reinstalled from synaptic and i will now reboot correct?

Edit: dint work :/

---

### Post by sutibun on 2012-07-29
it dint work :/  i can do anything else?

---

### Post by wildmanne39 on 2012-07-29
Hi, please post the output of:
```
nm-tool
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by sutibun on 2012-07-29
> **wildmanne39 said:**
> Hi, please post the output of:
```
nm-tool
``````
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```Thanks

nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:1D:72:28:DF:B9

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:1F:3A:56:5E:73

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    EFESSOU GEUSEIS: Infra, 00:05:59:0B:6C:37, Freq 2437 MHz, Rate 54 Mb/s, Strength 50


- Device: ttyUSB0  [Cosmote Default] -------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         31.152.20.182
    Prefix:          32 (255.255.255.255)
    Gateway:         10.64.64.64

    DNS:             94.143.178.17
    DNS:             195.167.65.194


```

```
Jul 30 06:24:56 nabi kernel: [ 2317.834019] wlan0: authenticate with 00:05:59:0b:6c:37 (try 1)
Jul 30 06:24:56 nabi wpa_supplicant[1029]: Trying to associate with 00:05:59:0b:6c:37 (SSID='EFESSOU GEUSEIS' freq=2437 MHz)
Jul 30 06:24:56 nabi kernel: [ 2317.836262] wlan0: authenticated
Jul 30 06:24:56 nabi kernel: [ 2317.837196] wlan0: associate with 00:05:59:0b:6c:37 (try 1)
Jul 30 06:24:56 nabi kernel: [ 2317.840290] wlan0: RX ReassocResp from 00:05:59:0b:6c:37 (capab=0x461 status=0 aid=1)
Jul 30 06:24:56 nabi kernel: [ 2317.840295] wlan0: associated
Jul 30 06:24:56 nabi wpa_supplicant[1029]: Associated with 00:05:59:0b:6c:37
Jul 30 06:24:56 nabi wpa_supplicant[1029]: CTRL-EVENT-CONNECTED - Connection to 00:05:59:0b:6c:37 completed (reauth) [id=0 id_str=]
Jul 30 06:24:56 nabi NetworkManager[554]: <info> (wlan0): supplicant interface state: authenticating -> completed
Jul 30 06:24:56 nabi NetworkManager[554]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'EFESSOU GEUSEIS'.
Jul 30 06:24:56 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 30 06:24:56 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 30 06:24:56 nabi NetworkManager[554]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 30 06:24:56 nabi NetworkManager[554]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 30 06:24:56 nabi NetworkManager[554]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jul 30 06:24:56 nabi avahi-daemon[550]: Withdrawing address record for fe80::21f:3aff:fe56:5e73 on wlan0.
Jul 30 06:24:56 nabi avahi-daemon[550]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::21f:3aff:fe56:5e73.
Jul 30 06:24:56 nabi avahi-daemon[550]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jul 30 06:24:56 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 30 06:24:57 nabi dhclient: Listening on LPF/wlan0/00:1f:3a:56:5e:73
Jul 30 06:24:57 nabi dhclient: Sending on   LPF/wlan0/00:1f:3a:56:5e:73
Jul 30 06:24:57 nabi dhclient: DHCPREQUEST of 192.168.2.5 on wlan0 to 255.255.255.255 port 67
Jul 30 06:24:57 nabi NetworkManager[554]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 30 06:24:57 nabi NetworkManager[554]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul 30 06:24:57 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 30 06:24:57 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 30 06:24:57 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jul 30 06:24:57 nabi avahi-daemon[550]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.5.
Jul 30 06:24:57 nabi avahi-daemon[550]: New relevant interface wlan0.IPv4 for mDNS.
Jul 30 06:24:57 nabi avahi-daemon[550]: Registering new address record for 192.168.2.5 on wlan0.IPv4.
Jul 30 06:24:58 nabi avahi-daemon[550]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::21f:3aff:fe56:5e73.
Jul 30 06:24:58 nabi avahi-daemon[550]: New relevant interface wlan0.IPv6 for mDNS.
Jul 30 06:24:58 nabi avahi-daemon[550]: Registering new address record for fe80::21f:3aff:fe56:5e73 on wlan0.*.
Jul 30 06:24:58 nabi NetworkManager[554]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jul 30 06:24:58 nabi NetworkManager[554]: <info> Policy set 'EFESSOU GEUSEIS 1' (wlan0) as default for IPv4 routing and DNS.
Jul 30 06:24:58 nabi NetworkManager[554]: <info> Activation (wlan0) successful, device activated.
Jul 30 06:24:58 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 30 06:24:58 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 30 06:25:07 nabi kernel: [ 2328.096030] wlan0: no IPv6 routers present
Jul 30 06:25:17 nabi NetworkManager[554]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul 30 06:25:17 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Jul 30 06:25:17 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Jul 30 06:25:17 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jul 30 06:25:17 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 30 06:25:17 nabi NetworkManager[554]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Jul 30 06:25:21 nabi NetworkManager[554]: <info> Policy set 'EFESSOU GEUSEIS 1' (wlan0) as default for IPv4 routing and DNS.
Jul 30 06:25:21 nabi NetworkManager[554]: <info> (wlan0): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jul 30 06:25:21 nabi NetworkManager[554]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Jul 30 06:25:21 nabi NetworkManager[554]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2213
Jul 30 06:25:21 nabi avahi-daemon[550]: Withdrawing address record for 192.168.2.5 on wlan0.
Jul 30 06:25:21 nabi avahi-daemon[550]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.5.
Jul 30 06:25:21 nabi avahi-daemon[550]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jul 30 06:25:21 nabi kernel: [ 2342.086156] wlan0: deauthenticating from 00:05:59:0b:6c:37 by local choice (reason=3)
Jul 30 06:25:21 nabi wpa_supplicant[1029]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Jul 30 06:25:21 nabi NetworkManager[554]: <info> (wlan0): supplicant interface state: completed -> disconnected

```

---

### Post by wildmanne39 on 2012-07-29
Hi, set your network settings in network manager to match the screenshots please.

You can not be connected to a broadband connection at the same time as you want to use your wireless so disconnect it then reboot.

Also your signal strength is a little weak can you get closer to your router?
Thanks

---

### Post by sutibun on 2012-07-29
> **wildmanne39 said:**
> Hi, set your network settings in network manager to match the screenshots please.
Done!

> **wildmanne39 said:**
> 
You can not be connected to a broadband connection at the same time as you want to use your wireless so disconnect it then reboot.
I know and i did.

> **wildmanne39 said:**
> 
Also your signal strength is a little weak can you get closer to your router?
Thanks
Ok i will try.

But still cant connect to the internet :/

---

### Post by wildmanne39 on 2012-07-29
Hi, post the output of:
```
cat /etc/resolv.conf
nm-tool
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/nm-system-settings.conf
cat /etc/network/interfaces
lsmod | grep b43
dmesg | grep etork
```
thanks

---

### Post by sutibun on 2012-07-29
> **wildmanne39 said:**
> Hi, post the output of:
```
cat /etc/resolv.conf
nm-tool
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/nm-system-settings.conf
cat /etc/network/interfaces
lsmod | grep b43
dmesg | grep etork
```thanks

I dont know if it makes any difference if i am connected through my broadband or the wireless when i hit the commands you ask me so if it is please tell me to repost
[B][U]
When connected with broadband:[/U][/B]

```
# Generated by NetworkManager
nameserver 94.143.178.17
nameserver 195.167.65.194

```


```

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:1D:72:28:DF:B9

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:1F:3A:56:5E:73

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    EFESSOU GEUSEIS: Infra, 00:05:59:0B:6C:37, Freq 2437 MHz, Rate 54 Mb/s, Strength 54


- Device: ttyUSB0  [Cosmote Default] -------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         31.152.83.70
    Prefix:          32 (255.255.255.255)
    Gateway:         10.64.64.64

    DNS:             94.143.178.17
    DNS:             195.167.65.194

```

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:05:59:0B:6C:37
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"EFESSOU GEUSEIS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000023be8341b6
                    Extra: Last beacon: 688ms ago
                    IE: Unknown: 000F45464553534F552047455553454953
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

ppp0      Interface doesn't support scanning.

```

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

```
cat /etc/NetworkManager/nm-system-settings.conf
cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory

```

```
auto lo
iface lo inet loopback

```


this 
```
dmesg | grep etork
```
Gave me nothing


Thanks

---

### Post by wildmanne39 on 2012-07-29
Hi, reset your router then disconnect from the broadband connection and reboot, if it does not connect repost the commands you just posted but with the broadband connection disconnected.

Post:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by sutibun on 2012-07-29
> **wildmanne39 said:**
> Hi, reset your router then disconnect from the broadband connection and reboot, if it does not connect repost the commands you just posted but with the broadband connection disconnected.

Post:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```Thanks

Sadly the router is in my cousins house and hes out for vacation.So i cant reset it until he gets back

Broadband disconnected


```
# Generated by NetworkManager

```

```
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:1D:72:28:DF:B9

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:1F:3A:56:5E:73

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    EFESSOU GEUSEIS: Infra, 00:05:59:0B:6C:37, Freq 2437 MHz, Rate 54 Mb/s, Strength 55


- Device: ttyUSB0 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             disconnected
  Default:           no

  Capabilities:



```

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:05:59:0B:6C:37
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"EFESSOU GEUSEIS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024deb6f1b6
                    Extra: Last beacon: 644ms ago
                    IE: Unknown: 000F45464553534F552047455553454953
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

wwan0     Interface doesn't support scanning.


```

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

```
cat /etc/NetworkManager/nm-system-settings.conf
cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory

```

```
auto lo
iface lo inet loopback


```

```
b43                   318816  0 
mac80211              272785  1 b43
cfg80211              172392  2 b43,mac80211
ssb                    50682  1 b43

```

this gave nothing again
```
dmesg | grep etork
```

```
 sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
Jul 30 08:58:46 nabi NetworkManager[570]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 30 08:58:46 nabi NetworkManager[570]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 30 08:58:46 nabi NetworkManager[570]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 30 08:58:46 nabi NetworkManager[570]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 30 08:58:46 nabi NetworkManager[570]: <info> Activation (wlan0/wireless): connection 'EFESSOU GEUSEIS' requires no security.  No secrets needed.
Jul 30 08:58:46 nabi NetworkManager[570]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 30 08:58:46 nabi NetworkManager[570]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jul 30 08:58:47 nabi wpa_supplicant[1024]: Trying to authenticate with 00:05:59:0b:6c:37 (SSID='EFESSOU GEUSEIS' freq=2437 MHz)
Jul 30 08:58:47 nabi NetworkManager[570]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 30 08:58:47 nabi wpa_supplicant[1024]: Trying to associate with 00:05:59:0b:6c:37 (SSID='EFESSOU GEUSEIS' freq=2437 MHz)
Jul 30 08:58:47 nabi kernel: [   28.524099] wlan0: authenticate with 00:05:59:0b:6c:37 (try 1)
Jul 30 08:58:47 nabi kernel: [   28.525569] wlan0: authenticated
Jul 30 08:58:47 nabi NetworkManager[570]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 30 08:58:47 nabi wpa_supplicant[1024]: Associated with 00:05:59:0b:6c:37
Jul 30 08:58:47 nabi wpa_supplicant[1024]: CTRL-EVENT-CONNECTED - Connection to 00:05:59:0b:6c:37 completed (auth) [id=0 id_str=]
Jul 30 08:58:47 nabi kernel: [   28.548096] wlan0: associate with 00:05:59:0b:6c:37 (try 1)
Jul 30 08:58:47 nabi kernel: [   28.550240] wlan0: RX AssocResp from 00:05:59:0b:6c:37 (capab=0x461 status=0 aid=1)
Jul 30 08:58:47 nabi kernel: [   28.550243] wlan0: associated
Jul 30 08:58:47 nabi kernel: [   28.550985] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 30 08:58:47 nabi NetworkManager[570]: <info> (wlan0): supplicant interface state: associating -> completed
Jul 30 08:58:47 nabi NetworkManager[570]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'EFESSOU GEUSEIS'.
Jul 30 08:58:47 nabi NetworkManager[570]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 30 08:58:47 nabi NetworkManager[570]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 30 08:58:47 nabi NetworkManager[570]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 30 08:58:47 nabi NetworkManager[570]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 30 08:58:47 nabi NetworkManager[570]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 30 08:58:47 nabi dhclient: Listening on LPF/wlan0/00:1f:3a:56:5e:73
Jul 30 08:58:47 nabi dhclient: Sending on   LPF/wlan0/00:1f:3a:56:5e:73
Jul 30 08:58:47 nabi dhclient: DHCPREQUEST of 192.168.2.5 on wlan0 to 255.255.255.255 port 67
Jul 30 08:58:47 nabi NetworkManager[570]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 30 08:58:48 nabi NetworkManager[570]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul 30 08:58:48 nabi NetworkManager[570]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 30 08:58:48 nabi NetworkManager[570]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 30 08:58:48 nabi NetworkManager[570]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jul 30 08:58:48 nabi avahi-daemon[567]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.5.
Jul 30 08:58:48 nabi avahi-daemon[567]: New relevant interface wlan0.IPv4 for mDNS.
Jul 30 08:58:48 nabi avahi-daemon[567]: Registering new address record for 192.168.2.5 on wlan0.IPv4.
Jul 30 08:58:49 nabi NetworkManager[570]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jul 30 08:58:49 nabi NetworkManager[570]: <info> Policy set 'EFESSOU GEUSEIS' (wlan0) as default for IPv4 routing and DNS.
Jul 30 08:58:49 nabi NetworkManager[570]: <info> Activation (wlan0) successful, device activated.
Jul 30 08:58:49 nabi NetworkManager[570]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 30 08:58:49 nabi NetworkManager[570]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 30 08:58:49 nabi avahi-daemon[567]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::21f:3aff:fe56:5e73.
Jul 30 08:58:49 nabi avahi-daemon[567]: New relevant interface wlan0.IPv6 for mDNS.
Jul 30 08:58:49 nabi avahi-daemon[567]: Registering new address record for fe80::21f:3aff:fe56:5e73 on wlan0.*.
Jul 30 08:58:58 nabi kernel: [   39.552049] wlan0: no IPv6 routers present
Jul 30 09:00:11 nabi NetworkManager[570]: <info> (wlan0): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jul 30 09:00:11 nabi NetworkManager[570]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Jul 30 09:00:11 nabi NetworkManager[570]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1336
Jul 30 09:00:11 nabi avahi-daemon[567]: Withdrawing address record for 192.168.2.5 on wlan0.
Jul 30 09:00:11 nabi avahi-daemon[567]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.5.
Jul 30 09:00:11 nabi avahi-daemon[567]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jul 30 09:00:11 nabi kernel: [  112.483168] wlan0: deauthenticating from 00:05:59:0b:6c:37 by local choice (reason=3)
Jul 30 09:00:11 nabi wpa_supplicant[1024]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Jul 30 09:00:11 nabi NetworkManager[570]: <info> (wlan0): supplicant interface state: completed -> disconnected

```

---

### Post by sutibun on 2012-07-30
Just in case you assume i am stealing internet and you dont reply I AM NOT. This is my cousins router and hes out for vacation and i am paying to him the half so i can use it! but i cant get in his house when hes not home.

So please help me

---

### Post by wildmanne39 on 2012-07-30
Hi, no I did not think that or I would have said that and then I would have closed the thread, I have just been busy today and I am about out of idea's.

Quality=35/70 is to low to connect, at least part of it is because of that, which can be because of distance and interference like walls and things, but I do not know what else to try without making changes to the router.
Thanks

---

### Post by sutibun on 2012-07-30
> **wildmanne39 said:**
> Hi, no I did not think that or I would have said that and then I would have closed the thread, I have just been busy today and I am about out of idea's.

Quality=35/70 is to low to connect, at least part of it is because of that, which can be because of distance and interference like walls and things, but I do not know what else to try without making changes to the router.
Thanks

oh:/ i got any chances by geting closer to the router? :/

---

### Post by wildmanne39 on 2012-07-30
Hi, it is possible you will just have to try it and see.
Thanks

---

