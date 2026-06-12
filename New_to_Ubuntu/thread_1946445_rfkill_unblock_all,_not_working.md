---
title: "rfkill unblock all, not working"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by Jake5 on 2012-03-24
hey,
so my wifi wont turn on, here is some rfkill outputs:```
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill unblock all
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ sudo rfkill unblock all
[sudo] password for jake: 
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```I can use a wired connection, but im trying to set up remote desktop sharing and i just want to do it over wifi, so i can sit on my couch and help my folks... anyways any help greatly appreciated, if i cant figure it out ill just have to make another ethernet cable, no big deal.

---

### Post by wildmanne39 on 2012-03-24
Hi, these can be hard to fix but not all ways please try this:
```
echo "blacklist hp-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then disconnect your wired connection and reboot.
Thanks

---

### Post by Jake5 on 2012-03-24
So that kind of worked, I have Wireless enabled now, however I cannot connect to my network, I tried connecting to it as a hidden network and every few seconds now its asking me for my password but will not connect.

---

### Post by Jake5 on 2012-03-24
that is to say, it won't recognize any wireless networks, there are about ten that should "pop up" for selection.

---

### Post by Jake5 on 2012-03-24
```
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ iwlist wlan0 scan
wlan0     No scan results

``` any thoughts?

---

### Post by anewguy on 2012-03-24
Post back the output of ifconfig and iwconfig inside the code tags (# on the menu bar) and we'll hopefully see a little more.

A couple of things I'm curious about - is there a hardware switch/keyboard combo that is supposed to enable/disable the wireless radio?  If so, be sure it is switched "on".  Also, are you set for roaming mode so it will actually scan for network?

I'm off for a little supper - be back on later.

Dave ;)

---

### Post by Jake5 on 2012-03-24
Ill get to the commands in a second, but for now, There is a hardware switch, however since i installed ubuntu, the switch hasn't worked, ive been using 
```
ifconfig wlan0 up
``` to turn the switch on, have had no problems before today.

outputs:
```
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:6e:5f:5a  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe6e:5f5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2714310 (2.7 MB)  TX bytes:393583 (393.5 KB)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:a7:d2:9a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ 

```
Thanks for your help, again you guys are my hero's.

---

### Post by wildmanne39 on 2012-03-24
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

Also you should change your network so it can be seen, hidden is actually no more secure that is a myth.
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
nm-tool
lsusb
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by anewguy on 2012-03-24
Hey Jake5, I'm going to leave you with wildmanne39 - he really knows his stuff with this, and I'm still suffering from something dumb this week that aggravated a back injury.  Laying in bed with a netbook, and to be honest pain, just isn't very conducive to me being helpful right now.

I know they'll have you straightened around in no time!

Dave ;)

---

### Post by wildmanne39 on 2012-03-24
Hi anewguy, I know what you mean I have walking pnemonia so I am resting in between helping, I hope your back heals soon.

---

### Post by Jake5 on 2012-03-25
output of ~uname -a:
```
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux jake-Compaq-Presario-CQ60-Notebook-PC 3.0.0-16-generic-pae #29-Ubuntu SMP Tue Feb 14 13:56:31 UTC 2012 i686 i686 i386 GNU/Linux
```output of lspci...:
```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:360b]
    Kernel driver in use: r8169

```lspci... on wifi:
```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:360b]
    Kernel driver in use: r8169
--
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k

```output of nm-tool:
```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1F:16:6E:5F:5A

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.18
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:24:2B:A7:D2:9A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
```NM tool with wifi:
```
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:1F:16:6E:5F:5A

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:24:2B:A7:D2:9A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```rfkill list all:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```lsmod:
```
Module                  Size  Used by
snd_hrtimer            12648  1 
bnep                   17923  2 
bluetooth             148839  7 bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52460  1 
joydev                 17393  0 
arc4                   12473  2 
snd_hda_intel          28358  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ath5k                 145100  0 
ip6t_LOG               16846  4 
ath                    19387  1 ath5k
xt_hl                  12465  6 
ip6t_rt                12473  3 
mac80211              393421  1 ath5k
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  22 
binfmt_misc            17292  1 
xt_addrtype            12596  4 
snd_seq_midi           13132  0 
xt_state               12514  14 
snd_rawmidi            25241  1 snd_seq_midi
psmouse                63474  0 
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
snd_seq_midi_event     14475  1 snd_seq_midi
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
serio_raw              12990  0 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21975  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
cfg80211              172427  3 ath5k,ath,mac80211
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  509554  3 
drm_kms_helper         32889  1 i915
snd                    55902  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   196290  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  0 
uas                    17699  0 
ahci                   21634  2 
libahci                25761  1 ahci
r8169                  47200  0 

```wildmanne39: > Also you should change your network so it can be seen, hidden is actually no more secure that is a myth. my network is not hidden, it was just the only way i could try to get the computer to connect to the router, see attached screen-shot...Look at top right dropdown menu, it is not locating any wireless networks...there should be at least eight in the list right now, or at least normally
Thanks wildmanne39, you too Dave hope you get to feeling better. Tore my meniscus snowboarding this season, been laid up for quite a while myself...  all kinds of new popping and cracking, you could mistake the sound of my knee to a bowl of rice crispies right after you pour the milk in! LAME!

---

### Post by Jake5 on 2012-03-25
> **wildmanne39 said:**
> Hi anewguy, I know what you mean I have walking pnemonia so I am resting in between helping, I hope your back heals soon.
What a sad group we are today! hope you feel better too wildmanne!

---

### Post by anewguy on 2012-03-25
> **wildmanne39 said:**
> Hi anewguy, I know what you mean I have walking pnemonia so I am resting in between helping, I hope your back heals soon.

Hope you get better soon - you contribute a LOT out here!

Dave ;)

---

### Post by Jake5 on 2012-03-25
> **anewguy said:**
> Hope you get better soon - you contribute a LOT out here!

Dave ;)
For sure, I know you two and cortman have been my personal saviours! Thank you both for spending your time helping us newb's

---

### Post by wildmanne39 on 2012-03-25
Hi, try this if it works we will make it permanent. Disconnect wired connectiuon first.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up

```

It is best if encryption is set to wpa2 only and not mixed.
Thanks

---

### Post by anewguy on 2012-03-25
> **wildmanne39 said:**
> Hi, try this if it works we will make it permanent. Disconnect wired connectiuon first.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up

```

It is best if encryption is set to wpa2 only and not mixed.
Thanks

Back scanning to see how things are going.  Was wondering wildmanne39 - is this going to be one of those blacklist ath5k and load in ath9k things?

BTW - I have some bad vertabrea in my low back which makes my back and my legs not work real well and, well, just plain hurt.  I did this dumb thing Wednesday night - I was putting together (what little of it there actually was to do) a smoker, and grabbed a lawn chair from the garage to sit on.  My sister and brother in-law (I rent their basement) had warned me not to use it.  Well, the lawn chair collapsed, legs under the seat, back out flat.  I landed on the place where the nerves that are bad sort of radiate from.  I laid flat on my back, in a broken lawn chair, with metal in my back, for 2 1/4 hours on a cold driveway in the drizzle until at 10:15 p.m. some kids went up the street and I convinced them to get the neighbors to call 911.  The ER said I did a good job sort of hyper-activating the nerves that were already bad.  Had some REALLY good drugs - told the doc it was like a flashback except I was dizzy.  Any way, my sister shows up to pick me up and I have yet to be asked "are you okay?".  All I've gotten is: (1) I wasn't supposed to use that chair (2) she needed to be up at 5:30 to take her granddaughter to breakfast before taking her to school (3) all my "crap" in the garage meant her car had to set out in the rain.  I'm 55, almost 56, have mental illness, and was "forced" to move in here 2 years ago.  I'm going to be moving out on my own again soon I hope.  So, I know miserable.  I also know bad pneumonia - almost died from that a few years ago - and I know it's miserable as well.  I really hope you do feel better soon!!

Dave ;)

---

### Post by Jake5 on 2012-03-25
hey guys, long night, anyways the codes you gave me, wildmanne, are not working, it brought a hard block onto my router, i cant get the switch to turn on, ```
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ sudo ifconfig wlan0 up
[sudo] password for jake: 
SIOCSIFFLAGS: Operation not possible due to RF-kill
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill unblock al
Bogus unblock argument 'al'.
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill unblock all
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
anyways i think the real underlying issue is that my hardware switch does not work, anyone know of a way to try to configure it?

---

### Post by wildmanne39 on 2012-03-25
Hi anewguy, no we are not going to blacklist the driver, I am sorry to hear about your experience.

@Jake5, try this then reboot and run rfkill if it does not connect, please just copy and paste the commands:
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 0:
```
rmmod -r ath5k
rfkill unblock all
modprobe ath5k
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thank you

---

### Post by Jake5 on 2012-03-25
Well my hardware switch turned back on, but I'm not seeing any networks to connect to. Although I am typing this from my cell phone that's connected to my home WiFi network. Just FYI.

---

### Post by wildmanne39 on 2012-03-25
Hi let's see what this tell us:
```
cat /etc/resolv.conf
cat /var/lib/NetworkManager/NetworkManager.state
```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork -e radio -e switch | tail -n75
```
Thanks

---

### Post by Jake5 on 2012-03-25
hey so here is the output of all of those commands lumped into one code bracket...ps, still no wireless networks available for connection:```
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ cat /etc/resov.conf
cat: /etc/resov.conf: No such file or directory
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ cat /var/lib/NetworkManager.state
cat: /var/lib/NetworkManager.state: No such file or directory
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e  wlan -e etork -e radio -e switch | tail -n75
[sudo] password for jake: 
Mar 25 14:57:29 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> wpa_supplicant started
Mar 25 14:57:29 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): supplicant interface state: starting -> ready
Mar 25 14:57:29 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar 25 14:57:29 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): supplicant interface state: ready -> inactive
Mar 25 14:57:29 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Mar 25 14:57:29 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar 25 14:57:30 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   21.522383] Console: switching to colour frame buffer device 170x48
Mar 25 15:01:40 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [    0.008058] SMP alternatives: switching to UP code
Mar 25 15:01:41 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   19.626971] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 25 15:01:41 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0, iface: eth0)
Mar 25 15:01:41 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Mar 25 15:01:41 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 25 15:01:41 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   19.626986] ath5k 0000:02:00.0: setting latency timer to 64
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   19.627037] ath5k 0000:02:00.0: registered as 'phy0'
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.367667] ath: EEPROM regdomain: 0x64
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.367670] ath: EEPROM indicates we should expect a direct regpair map
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.367673] ath: Country alpha2 being used: 00
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.367674] ath: Regpair used: 0x64
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.499707] Registered led device: ath5k-phy0::rx
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.499928] Registered led device: ath5k-phy0::tx
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.499940] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> monitoring kernel firmware directory '/lib/firmware'.
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> WiFi enabled by radio killswitch; enabled by state file
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> WWAN enabled by radio killswitch; enabled by state file
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> WiMAX enabled by radio killswitch; enabled by state file
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): now managed
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): bringing up device.
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): preparing device.
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC dbus[566]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   21.288408] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC dbus[566]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> wpa_supplicant started
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): supplicant interface state: starting -> ready
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar 25 15:01:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): supplicant interface state: ready -> inactive
Mar 25 15:01:43 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   21.945172] Console: switching to colour frame buffer device 170x48
Mar 25 15:06:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) starting connection 'FriscoDisco'
Mar 25 15:06:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 25 15:06:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 25 15:06:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 25 15:06:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 25 15:06:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 25 15:06:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 25 15:06:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 25 15:06:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0/wireless): connection 'FriscoDisco' has security, and secrets exist.  No new secrets needed.
Mar 25 15:06:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 25 15:06:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): supplicant interface state: inactive -> scanning
Mar 25 15:07:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <warn> Activation (wlan0/wireless): association took too long.
Mar 25 15:07:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 25 15:07:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <warn> Activation (wlan0/wireless): asking for new secrets
Mar 25 15:07:10 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): supplicant interface state: scanning -> inactive
Mar 25 15:07:19 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 25 15:07:19 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 25 15:07:19 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar 25 15:07:19 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 25 15:07:19 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 25 15:07:19 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 25 15:07:19 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 25 15:07:19 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0/wireless): connection 'FriscoDisco' has security, and secrets exist.  No new secrets needed.
Mar 25 15:07:19 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 25 15:07:19 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): supplicant interface state: inactive -> scanning
Mar 25 15:07:51 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): device state change: config -> disconnected (reason 'user-requested') [50 30 39]
Mar 25 15:07:51 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Mar 25 15:07:53 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[578]: <info> (wlan0): supplicant interface state: scanning -> inactive
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$
``` Thanks again for all of your time and shared expertice, soooo much appreciated.

---

### Post by Jake5 on 2012-03-25
maybe i typed the first two commands incorrectly I tried again with the ethernet cable plugged in, added comment line when i unplugged the connections and ran the codes again.
```
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ #unpluging wired connection now
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ cat /etc/resolv.conf
# Generated by NetworkManager
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$
```

---

### Post by wildmanne39 on 2012-03-25
Hi, so this command>  cat /var/lib/NetworkManager/NetworkManager.stateit has 2 sets of files in it called main?

This command did not show any out put:
```
cat /etc/resolv.conf
```?

Always just copy and paste for accuracy please.
Thanks

---

### Post by Jake5 on 2012-03-25
hey, sorry. this might help
```
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ cat /var/lib/NetworkManager/NetworkManager.state 

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$
```&```
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ 
```

---

### Post by wildmanne39 on 2012-03-25
Hi, did you let network manager set up your connection for you? 

I recommend deleting all your wireless connection and reboot and see if a connection is found.

Do you have network manager installed it is installed be default.
You can check with this command:
```
ps aux | grep nm-apple
```
Have you clicked on the icon in the top right corner of your screen and make sure enable wireless has a check by it?
Thanks

---

### Post by Jake5 on 2012-03-25
Okay, so enable wireless in upper right hand corner is what I have been refering to when I say, "it turned my hardware switch on"...or off. It came on after we did that really long cmd line in post# 22. I did as you suggested, deleted all of my networks, and rebooted. In the same dropdown menu where the enable wireless checkmark you asked me about. The enable wireless option is now deselected and I am unable to select it. When I try to enable wireless from the terminal it is still not responding to:
rfkill unblock all, or 
ifconfig wlan0 up.  
The last two lines should be in code tags... I know and I am sorry, with my knee I can't really sit on the floor anymore, I can only connect to my network via Ethernet cable, and my phone will only let me post quick replies. Sorry again.

---

### Post by wildmanne39 on 2012-03-25
Hi, you should not need to turn it on or off by the terminal, when you rebooted it should have found your network and you should have been asked for your password.

Please post the output from the command in my previous post so we can see if network manager is running properly.

Also post the results of:
```
rfkill list all
```
Thanks

---

### Post by Jake5 on 2012-03-25
> **wildmanne39 said:**
> Hi, you should not need to turn it on or off by the terminal, when you rebooted it should have found your network and you should have been asked for your password.

I agree, and until the first time i plugged in a lan cable yesterday, It always worked just fine.

here is the output of rfkill list all:```
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ 
```Again, I truly believe that the issue is that my wireless hardware button on my keyboard, the one that is not working, is the issue. The button has power, as it lights up blue when the "Enable Wireless" option in the before mentioned drop down menu is selected. When I am unable to select the "Enable Wireless" button the light turns orange, as it used to a few months ago while running Vista...yes it sucked, but my physical wifi hardware switch (Same switch i am talking about) worked just fine up until the moment I installed ubuntu. I can sometimes get
```
ifconfig wlan0 up
```to change the switch state from off to on, but only when the output of```
rfkill list all
``` says
 ```

This is an example only, not to be mistaken for the actual output of the command rfkill list all

jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$
```which seems to be getting harder to do these days as stated in the title of this thread, rfkill unblock all is not working.

---

### Post by wildmanne39 on 2012-03-25
Hi, post the contents of this file please:
```
gksudo gedit /etc/rc.local
```
it should have unblocked it unless the button is gone completely out.

We had that hardblock gone for a while I thought.
Thanks

---

### Post by Jake5 on 2012-03-25
requested output:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmod -r ath5k
rfkill unblock all
modprobe ath5k

exit 0
```

and yes that hardblock was unblocked previously for a while

---

### Post by anewguy on 2012-03-25
I think there's a typo in that script - shouldn't it be rmmod -r ath5k?  I only see "rmod".

Dave ;)

---

### Post by wildmanne39 on 2012-03-25
Hi, in that file rmod -r ath5k should be:
```
rmmod -r ath5k
```
change that then save gedit then close and reboot.
Thanks

---

### Post by wildmanne39 on 2012-03-25
Hi, exactly anewguy that is why I always ask people to copy and paste.

---

### Post by Jake5 on 2012-03-25
okay, changed the line, thats what i get for not using copy paste. sorry to waste your time guys... please forgive. should i repeat the steps we took after we tried to do that the first time

---

### Post by wildmanne39 on 2012-03-25
Hi, it is ok it helps to improve or skills.

Post the output of:
```
nm-tool
rfkill list all
sudo iwlist scan
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
```
so I guess it did not connect?
thanks

---

### Post by Jake5 on 2012-03-25
yeah, its still not working, unable to connect
```
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1F:16:6E:5F:5A

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:24:2B:A7:D2:9A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$
``````
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$
```Great!
```

[CODE]jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ sudo iwlist scan
[sudo] password for jake: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$
```jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
Mar 25 17:58:08 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[588]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 25 17:58:08 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[588]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 25 17:58:08 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[588]: <info> Activation (wlan0/wireless): connection 'FriscoDisco' has security, and secrets exist.  No new secrets needed.
Mar 25 17:58:08 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[588]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 25 17:58:08 jake-Compaq-Presario-CQ60-Notebook-PC wpa_supplicant[890]: Trying to associate with SSID 'FriscoDisco'
Mar 25 17:58:08 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[588]: <info> (wlan0): device state change: config -> unavailable (reason 'none') [50 20 0]
Mar 25 17:58:08 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[588]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar 25 17:58:08 jake-Compaq-Presario-CQ60-Notebook-PC wpa_supplicant[890]: Association request to the driver failed
Mar 25 17:59:20 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   19.588430] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 25 17:59:20 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0, iface: eth0)
Mar 25 17:59:20 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Mar 25 17:59:20 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 25 17:59:20 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   19.588444] ath5k 0000:02:00.0: setting latency timer to 64
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   19.588497] ath5k 0000:02:00.0: registered as 'phy0'
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.294228] ath: EEPROM regdomain: 0x64
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.294231] ath: EEPROM indicates we should expect a direct regpair map
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.294234] ath: Country alpha2 being used: 00
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.294236] ath: Regpair used: 0x64
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.456150] Registered led device: ath5k-phy0::rx
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.456253] Registered led device: ath5k-phy0::tx
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   20.456264] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> monitoring kernel firmware directory '/lib/firmware'.
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): now managed
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): bringing up device.
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): preparing device.
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC dbus[581]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [   21.361667] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC dbus[581]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> wpa_supplicant started
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): supplicant interface state: starting -> ready
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar 25 17:59:21 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): supplicant interface state: ready -> inactive
Mar 25 18:02:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): now unmanaged
Mar 25 18:02:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Mar 25 18:02:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): cleaning up...
Mar 25 18:02:42 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): taking down device.
Mar 25 18:09:09 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): now managed
Mar 25 18:09:09 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 25 18:09:09 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): bringing up device.
Mar 25 18:09:09 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): preparing device.
Mar 25 18:09:09 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar 25 18:09:09 jake-Compaq-Presario-CQ60-Notebook-PC kernel: [  232.641925] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 25 18:09:09 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): supplicant interface state: starting -> ready
Mar 25 18:09:09 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar 25 18:09:09 jake-Compaq-Presario-CQ60-Notebook-PC NetworkManager[597]: <info> (wlan0): supplicant interface state: ready -> inactive
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$[/CODE]

---

### Post by Jake5 on 2012-03-25
sorry, I tried to edit that last post to insert a code i accidentally deleted:
```
jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$ sudo iwlist scan
[sudo] password for jake: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

jake@jake-Compaq-Presario-CQ60-Notebook-PC:~$
```

---

### Post by wildmanne39 on 2012-03-25
Hi, it is still not scanning, me and the wireless expert have been working on the same problem with the same card with the same ubuntu version for 2 days in another thread and it will not scan either using 11.10, but I had him boot an older kernel earlier and it now scans still did not connect but we are working on it.

I had read a long time back that in 11.10 with this card if you ever turn your wireless off with the switch it will not come back on, in that case the person reinstalled and it worked and he did not turn it of again with the switch.
Thanks

---

### Post by Jake5 on 2012-03-25
and that could be the case, but the thing is, i have lubuntu 11.10 on this machine also, which im typing this on right now over my wifi network. maybe it is just the kernel for ubuntu 11.10 or maybe this info will lead to a possible solution for both of us...maybe. anyways, its not the biggest deal, i will just make a longer ethernet cable tomorrow and i was planning on installing 12.04 as soon as it drops anyways, so i think i can hold out, Thanks again for all your help!

---

### Post by Jake5 on 2012-03-25
Marking thread Solved...For now.

---

### Post by wildmanne39 on 2012-03-25
Hi, ok sorry I could not find the answer you needed.

---

### Post by Jake5 on 2012-03-25
No need for apologies, Thanks again, you have spent so much time helping me out, i feel like i owe you something in return. wish i could reciprocate somehow.

---

### Post by anewguy on 2012-03-25
Go to system admin tools and turn off bluetooth and see if it starts scanning.

Dave ;)

---

### Post by Jake5 on 2012-03-25
Well, I dont know what to say, I shut down the computer a few hours ago, normally. for some reason it ran a checkdisk at boot. and now my wireless works again? what is to be learned from this? from my experience computers dont usually just fix themselves.

Oh and is there a command for shutting down the bluetooth?

---

### Post by wildmanne39 on 2012-03-25
Hi, that is good news maybe we did something right at the very list you know we did not make it worse.

I would not turn the wireless of with the keyboard any more though.
Thanks

---

### Post by wildmanne39 on 2012-03-25
Hi, in post 32 when you fixed that typo in the file did you reboot your computer then if not that is what it was.
Thanks

---

### Post by Jake5 on 2012-03-25
yeah, I do somewhat recall the button physically working one time, as i was checking hardware compatibility post(noob) my first install. ill keep my trigger finger away from now on though,

---

### Post by matt_symes on 2012-03-26
Hi

> Oh and is there a command for shutting down the bluetooth?
To stop bluetooth

```
sudo service bluetooth stop
```

and to start it again.

```
sudo service bluetooth start
```

Kind regards

---

### Post by anewguy on 2012-03-26
I'm glad wildmanne39 was able to walk you through the things that really solved your problem.  Told you they knew their stuff!!  I only mentioned the bluetooth stuff because from many releases ago, old kernels, old driver, this lack of scanning was "cured" by turning off bluetooth on your particular PC.

I'm just glad it's working - thanks wildmanne39 for getting this going for Jake!

Dave ;)

---

### Post by wildmanne39 on 2012-03-26
Hi anewguy, your welcome! depending on the version of ubuntu there are kernel parameters that can be set so they both work together when otherwise the will not.:popcorn:

---

### Post by narcisgarcia on 2012-12-31
Can somebody determine which was the final solution for Jake5 ?
I've tried every solution published with the same computer model and wifi device, but no success.

I'm also with a "Compaq Presario CQ60" and now with Ubuntu 12.10
ath5k seems to have now more possible parameters, but no success trying everyone:

```
$ lspci -k -d 168c:001c
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Hewlett-Packard Company Device 137b
	Kernel driver in use: ath5k
	Kernel modules: ath5k

$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

$ modinfo ath5k
filename:       /lib/modules/3.5.0-21-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     D5039BECA219E59A7332A15
alias:          pci:v0000168Cd0000FF1Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.5.0-21-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           all_channels:Expose all channels the device can use. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)
```

---

### Post by narcisgarcia on 2012-12-31
To shut down the computer properly, I've put apm=power_off as a kernel parameter. In the meanwhile, I've also tested to blacklist the ath5k module (to load it manually with nohwcrypt=1).

These two actions made to work wireless perfectly, but now I have cleaned the kernel parameter and removed the blacklist line. After several shutdowns and starts of the computer, wireless still works.

I suppose the matter can be related with Power Management OR with some state saved to device/board memory.

---

