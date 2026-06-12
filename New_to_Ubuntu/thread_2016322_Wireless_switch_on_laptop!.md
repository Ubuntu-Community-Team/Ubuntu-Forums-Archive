---
title: "Wireless switch on laptop!"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by sonicyouth on 2012-07-04
My last hope....! 
Hi guys, im a totally newbie to linux, just installed ubuntu 12.04 on my fujitsu siemens amilo pro v3405 laptop. having a total nightmare, cannot for the life of me get the sh*tting killswitch to activate on the laptop, dont know any linux command syntax and have been through dozens of different guides installing acerhkgui and python updates and nothing i do will activate the wifi on the laptop, in rfkill list it says software is on hardware is off, i cant change anything.
so any help would be appreciated, in the meantime ill crack on with my ubuntu for dummies book....

---

### Post by matt_symes on 2012-07-04
Hi

Welcome to the forums sonicyouth.

Please open a terminal and type

```
sudo apt-get install rfkill
```Enter your password. It will not be echoed to the screen.

Then type

```
rfkill list all
```Post the results back here by copying and pasting from the terminal into your next post.

Post the results back here between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```.

After that type

```
sudo lshw -c network
```and post that back here as well.

If i cannot help then i am sure others can.

Kind regards

---

### Post by sonicyouth on 2012-07-07
hi matt thanks for your swift reply, this is the terminal output from those commands.
```
unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ sudo apt-get install rfkill
[sudo] password for unclefester: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rfkill is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 299 not upgraded.
unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ rfkill all
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-1ubuntu2 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ sudo lshw -c network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:11:ac:bc
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.2.0-23-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:43 memory:d4000000-d4000fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:bb:de:06
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.6 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:4000(size=256) memory:d8000000-d80000ff
```

---

### Post by plucky on 2012-07-08
> unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ rfkill all
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-1ubuntu2 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm


That should be ```
rfkill list all
```

Good luck

---

### Post by sonicyouth on 2012-07-08
i get ya....

```
 unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by matt_symes on 2012-07-08
Hi

> **plucky said:**
> That should be ```
rfkill list all
```Good luck

D'oh. Thanks plucky :)

I'll edit my previous post.

Kind regards

---

### Post by wildmanne39 on 2012-07-08
Hi, a hardblock usually means the physical switch is off on the computer so try to turn it on by pressing a key combination or a button and check it with: 
```
rfkill list all
```
if in doubt look up documentation for your computer on the manufacturers website.

If that does not work try:
```
sudo rfkill unblock all
```
Thanks

---

### Post by sonicyouth on 2012-07-08
im such a novice on this, ive tried loads of things including that command.
Yes the wireless hw switch is turned off, thats the problem, nothing will make it activate, the bios settings are set to wireless enabled by default.
I had a previous problem I tried to change the wireless card in the laptop for a newer one, as soon as I installed it i had the same problems (on windows 7), it seems only the original set up of the supplied wifi card and drivers will let me activate the wifi button on the laptop.
The Fn + F10 function key wont work either that supposed to activate the wifi.
Still stuck :-(

Thanks so far for the suggestions though! While im here what are the syntax basics? Like what does 'sudu' mean etc

taa

---

### Post by NikTh on 2012-07-08
Your wireless should be fine , but  its disabled. If switch don't work try from BIOS . Check if something about wireless or wifi is disabled in Bios configuration.

---

### Post by sonicyouth on 2012-07-08
the bios settings are fine, last week windows 7 was installed, the wireless worked fine, the button etc. now with ubuntu its impossible to turn it on, seems others had similar problems with the same laptop but i cant find any info

---

### Post by spiky001 on 2012-07-08
Hi  I,m having similar problems but I changed my card as you mentioned. (not fixed) Do you have windows on the system as well as Ubuntu? I have read that in some cases it must be working in windows for it to work in ubuntu, I,E the light must be on.

---

### Post by sonicyouth on 2012-07-08
> **spiky001 said:**
> Hi  I,m having similar problems but I changed my card as you mentioned. (not fixed) Do you have windows on the system as well as Ubuntu? I have read that in some cases it must be working in windows for it to work in ubuntu, I,E the light must be on.

  I just did a clean install of ubuntu so no dual boot im afraid, cant believe i cant win this one!!

---

### Post by wildmanne39 on 2012-07-08
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
nm-tool
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thanks

---

### Post by plucky on 2012-07-08
> **sonicyouth said:**
> I just did a clean install of ubuntu so no dual boot im afraid, cant believe i cant win this one!!

[This](http://carolina.mff.cuni.cz/~trmac/blog/wistron_btns/) driver allowed me to get my wireless switch working on a Fujitsu-Siemens M7400 Amilo.

You could try it with one command ```
sudo modprobe wistron_btns
```
This will load the module into the kernel.Then try the switch.

If that works,you then have to edit /etc/modules and add wistron_btns to the list so it is loaded at every reboot.

Not sure it will work on your laptop,but there is no harm in trying.

Good Luck

---

### Post by sonicyouth on 2012-07-10
> **wildmanne39 said:**
> Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
nm-tool
iwconfig
rfkill list all
lsmod
```by clicking on new reply and click # then paste the information between the brackets.
Thanks

```

unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux unclefester-AMILO-Pro-Edition-V3405 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux
unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1001]
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
0a:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Fujitsu Technology Solutions Device [1734:10c1]
    Kernel driver in use: 8139too
unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:0A:E4:BB:DE:06

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unavailable
  Default:           no
  HW Address:        00:18:DE:11:AC:BC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ lsmod
Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  0 
ppdev                  12849  0 
bluetooth             158438  10 bnep,rfcomm
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   174055  1 
joydev                 17393  0 
snd_hda_intel          32765  6 
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
snd_pcm                80845  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                72919  0 
serio_raw              13027  0 
iwl3945                73152  0 
iwl_legacy             71134  1 iwl3945
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
mac80211              436455  2 iwl3945,iwl_legacy
i915                  414655  3 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
snd                    62064  20 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0 
8139cp                 26759  0 

```

---

### Post by sonicyouth on 2012-07-10
> **plucky said:**
> [This]("http://carolina.mff.cuni.cz/%7Etrmac/blog/wistron_btns/") driver allowed me to get my wireless switch working on a Fujitsu-Siemens M7400 Amilo.

You could try it with one command ```
sudo modprobe wistron_btns
```This will load the module into the kernel.Then try the switch.

If that works,you then have to edit /etc/modules and add wistron_btns to the list so it is loaded at every reboot.

Not sure it will work on your laptop,but there is no harm in trying.

Good Luck

```

unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ sudo modprobe wistron_btns
[sudo] password for unclefester: 
FATAL: Error inserting wistron_btns (/lib/modules/3.2.0-26-generic-pae/kernel/drivers/input/misc/wistron_btns.ko): No such device

```

---

### Post by wildmanne39 on 2012-07-10
Hi, please do by coping and pasting:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off

```
above exit0, then save gedit, close and reboot.

Then post the output of:
```
cat /var/lib/NetworkManager/NetworkManager.state
```
```
dmesg | egrep 'iwl|firm|radio|switch|wlan0'
```
Thanks

---

### Post by sonicyouth on 2012-07-10
> **wildmanne39 said:**
> Hi, please do by coping and pasting:
```
gksudo gedit /etc/pm/power.d/wireless
```(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off

```above exit0, then save gedit, close and reboot.

Then post the output of:
```
cat /var/lib/NetworkManager/NetworkManager.state
``````
dmesg | egrep 'iwl|firm|radio|switch|wlan0'
```Thanks

here ya go (thanks)
```

unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ gksudo gedit /etc/pm/power.d/wireless
unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

unclefester@unclefester-AMILO-Pro-Edition-V3405:~$ dmesg | egrep 'iwl|firm|radio|switch|wlan0'
[   17.072317] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   17.072322] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   17.072420] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.072437] iwl3945 0000:02:00.0: setting latency timer to 64
[   17.113111] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   17.113117] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   17.113275] iwl3945 0000:02:00.0: irq 43 for MSI/MSI-X
[   17.590452] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   18.413220] Console: switching to colour frame buffer device 160x50
[   21.649019] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by wildmanne39 on 2012-07-10
Hi, just copy and paste the command you left out '.
Thanks

---

