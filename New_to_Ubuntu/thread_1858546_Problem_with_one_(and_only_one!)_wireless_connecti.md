---
title: "Problem with one (and only one!) wireless connection"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by elizaram on 2011-10-12
Hi all,

I hope you can point me in the right direction here. I know just enough about Linux to be a danger to my computer :p and have definitely come up against my limit here.

I've got an Asus EEE 901 running Eeebuntu 3.0 standard. Frequently I'll take it out to a bar or coffee shop with Wifi. A few weeks ago, however, I went to one of my regular spots and was unable to connect to their wireless. It "churned" for a long time, then popped up the box asking for the password. Entered password, same thing happened. I deleted its entry in the list of wireless connections, no luck. I had two other wireless-capable devices with me, and both of them connected without a problem. The owner was there at the time, so I asked him if there had been a change in his wireless. Turns out his router had recently died, and he'd replaced it with a new one, and set it up using the same SSID and security key.

I have no problem connecting to any other wireless signal; it's only this particular one that is giving me issues. My hunch is that my computer has stored, somewhere, some information about the old hardware and now is unable to connect because the new hardware does not match it. But I've checked with the Gnome keyring manager and found no entries for this connection (since I had deleted it from the list), and have no clue where else to look.

Any ideas?

---

### Post by wolfen69 on 2011-10-12
That's kind of strange that you can connect to all other wireless points. Is there any way you can bring a friend and their laptop to see if they can connect? Maybe it's the cafe's fault, not your computer.

---

### Post by elizaram on 2011-10-12
Did that. Both my other wireless devices (a Kindle and a Zune) could connect. My husband's computer (Windows) could connect. The owner's iPad connects fine. He's never had any other complaints about the wireless.

---

### Post by wolfen69 on 2011-10-12
Did you right click the network icon and select *edit connections* to see if there is a setting that has changed?

---

### Post by Diametric on 2011-10-12
Sounds like the new Wireless router is not recognized by that Ubuntu distro - ask the owner to give you the make and model number and you should then be able to search on that to see if it is supported.  

Hope that helps.

---

### Post by elizaram on 2011-10-12
I did that initially and deleted the connection from the list entirely (did not attempt to edit it), thinking I could re-detect the connection and everything would be peachy, but alas no - it was still unable to connect. I don't have the connection on the list currently (would have to go back to the bar and re-acquire it - but hey, would be a great excuse to go have a beer in the middle of the afternoon :D)

---

### Post by grahammechanical on 2011-10-12
The new router might have the same SSID and security key but is the setting for this connection in network manager set to the same encryption method as that set on the router?

You are right about network manager remembering things. It is my guess that the new router has a different hardware IP address to the old router and that is causing issues. Of course I may be wrong.

Deleting the connection in network manager (which you have done) and starting again with a new connection by selecting the connection from the list in network manager should have fixed it.

Try deleting the connection from network manager before the machine gets in range of this wireless hot spot. This is my "if all else fails, do something silly" option.

Regards.

P.S. Bottoms up! (beer glasses that is)

---

### Post by ajgreeny on 2011-10-12
You could also try using wicd instead of network manager;  some people use it all the time and swear by it, saying it is much better at connecting in difficult wireless connection sites.

You can have both running together if you have them both installed, but I suggest you remove the normal network manager (applet) from startup applications, and try using wicd alone.

---

### Post by wolfen69 on 2011-10-12
> **Diametric said:**
> Sounds like the new Wireless router is not recognized by that Ubuntu distro

Ubuntu connects to signals, not hardware. As long as your pc has the ability to use that type of connection, brand of hardware doesn't matter.

---

### Post by gandaran on 2011-10-12
> Turns out his router had recently died, and he'd replaced it with a new one, and set it up using the same SSID and security key.
okay same SSID and security key but the security mode and channel could have changed and they aren't supported by your wireless drivers.
what wireless card chipset model and brand does the netbook have?

---

### Post by elizaram on 2011-10-12
Ok, I made it out to the bar (yes, I am quite suggestible!) and the owner told me he had changed the SSID on the router in case it might help. So my netbook should see this as an entirely new, unrecognized wireless connection, yes? - but I'm still having the same problem. Which tells me it's probably some fundamental incompatibility between my system and the router.

I've borrowed my son's netbook and am connected on that one at the moment. (Yes, I'm sitting at a bar with 2 computers. I are geek.) It tells me the security on the router is WPA2 Personal, encryption type AES. How can I determine the specs of my wireless card?

I looked into installing wicd. Problem is I can't get it from the file repository; I believe this OS is Jaunty based and that is no longer supported, am I right? In any case, any attempt to update or install programs results in a file not found thingy. Tried doing it via a command line and it wants to uninstall the network manager, which if it can't replace, may leave me without any connectivity at all.

I'm thinking it may be time to wipe and replace this OS. I was hesitant to do that because I have this one configured exactly the way I want it and everything works. Aurora (Eeebuntu 4) is in early early beta and hasn't been updated in ages; I tried it months ago and remember that not all my hardware worked, though I don't recall the particulars...

---

### Post by elizaram on 2011-10-12
Oh also our home network is WPA2 Personal/AES, and I have no problems connecting to it.

---

### Post by wildmanne39 on 2011-10-12
Hi, please post the results of these commands so we can hopefully see what the problem is.

To get the information I need you will have to be at the bar where you want to connect when you run these commands.
```
cat /etc/lsb-release; uname -a
``````
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
dmesg | egrep 'net|eth|sky|sis|via|3c3|3c5|e100|8139|8169|acx|air|ath|atl|ar9|carl|atme|at7|herm|iwl|ipw|rtl8|r81|rt2|rt3|rt6|rt7|tg3|ssb|wl|b43|b44|ori|pri|p5|zd|ndis|wmi|ns8'
```
The reason I gave you so many at once is because you have to leave your home and go somewhere else to run these commands.

You can copy and paste the commands into the terminal by hitting ctrl+alt+t then copy and paste the output to a flash drive to post here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by elizaram on 2011-10-13
Thanks for the detailed instructions. I went out this afternoon to carry them out. This is the output verbatim, except I've altered the SSID slightly - it's the same as the name of the bar and I don't want to mess up his SEO :p

```
elizabeth@Tinycat:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
Linux Tinycat 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
elizabeth@Tinycat:~$ sudo lshw -C network
[sudo] password for elizabeth: 
  *-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:64:f0:fc
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:15:af:e6:5d:07
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:b8:4a:da:a9:9c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
elizabeth@Tinycat:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             unavailable
  Default:           no
  HW Address:        00:22:15:64:F0:FC

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        00:15:AF:E6:5D:07

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    KD Saloon: Infra, 98:2C:BE:58:C2:F9, Freq 2412 MHz, Rate 18 Mb/s, Strength 39 WPA WPA2
    megahoc.v30:     Ad-Hoc, 02:60:30:67:E4:86, Freq 2422 MHz, Rate 0 Mb/s, Strength 10


elizabeth@Tinycat:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
    Kernel driver in use: rt2860
    Kernel modules: rt2860sta
03:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1e Gigabit Ethernet Adapter [1969:1026] (rev b0)
    Kernel driver in use: ATL1E
    Kernel modules: atl1e
elizabeth@Tinycat:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-70 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

elizabeth@Tinycat:~$ rfkill list all
bash: rfkill: command not found
elizabeth@Tinycat:~$ lsmod
Module                  Size  Used by
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
i2c_i801               17296  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
psmouse                61972  0 
snd_rawmidi            29696  1 snd_seq_midi
serio_raw              13316  0 
pcspkr                 10496  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
snd_timer              29704  2 snd_pcm,snd_seq
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
btusb                  19608  2 
usbhid                 42336  0 
rt2860sta             522968  1 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
video                  25360  0 
output                 11008  1 video
eeepc_laptop           18452  0 
atl1e                  40212  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
elizabeth@Tinycat:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 98:2C:BE:58:C2:F9
                    ESSID:"KD Saloon"
                    Mode:Managed
                    Channel:1
                    Quality:39/100  Signal level:-74 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 02:60:30:67:E4:86
                    ESSID:"megahoc.v30"
                    Mode:Ad-Hoc
                    Channel:3
                    Quality:20/100  Signal level:-82 dBm  Noise level:-97 dBm
                    Encryption key:off
                    Bit Rates:11 Mb/s

pan0      Interface doesn't support scanning.

elizabeth@Tinycat:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

ra0       13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

pan0      no frequency information.

elizabeth@Tinycat:~$ 
elizabeth@Tinycat:~$ dmesg | egrep 'net|eth|sky|sis|via|3c3|3c5|e100|8139|8169|acx|air|ath|atl|ar9|carl|atme|at7|herm|iwl|ipw|rtl8|r81|rt2|rt3|rt6|rt7|tg3|ssb|wl|b43|b44|ori|pri|p5|zd|ndis|wmi|ns8'
[    0.596002] APIC calibration not consistent with PM Timer: 115ms instead of 100ms
[    0.684317] net_namespace: 776 bytes
[    1.856496] audit: initializing netlink socket (disabled)
[    1.881697] ACPI: AC Adapter [AC0] (off-line)
[    2.178277] thermal LNXTHERM:01: registered as thermal_zone0
[    2.236208] ACPI: Thermal Zone [TZ00] (33 C)
[    2.605978] Driver 'sd' needs updating - please use bus_type methods
[    2.605999] Driver 'sr' needs updating - please use bus_type methods
[    3.040818] device-mapper: multipath: version 1.0.5 loaded
[    3.040824] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.679229] eeepc: Get control methods supported: 0x101713
[    6.953868] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[    6.963359] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    6.963993] rt2860 0000:01:00.0: setting latency timer to 64
[    8.144620] Adding 224868k swap on /dev/sda5.  Priority:-1 extents:1 across:224868k
[   14.494177] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.548185] ADDRCONF(NETDEV_UP): eth0: link is not ready
elizabeth@Tinycat:~$ 

```

---

### Post by wildmanne39 on 2011-10-13
Hi, KD Saloon is the network you want to connect to right?

If so it would be best to have the router set to wpa2 only that often causes linux computers trouble when connecting.

Also the signal strength is weak, possibly because the wireless power is not turned up too 100 percent or because the driver is an old one.

Also your version of ubuntu is old it is no longer supported so you will not be able to get updates not even security, so your system is at risk for viruses, I would recommend upgrading to 10.04 then get wireless working.

The channel is set to 1 I have seen people have trouble with channel 1, I would set it to 6 or 8 but that has to be done in the router.

Also notice that you did not have a SSID at all in the iwconfig just a nickname, did you take that out or is it just missing?
Thank you

---

### Post by NoBugs! on 2011-10-13
Yeah, if I remember correctly 9.04 or 9.10 (or was it 8.10)? had some bad bugs in network-manager, I think I traced one problem to other Windows machines that were connected at the same time (something like the "Free Public Wifi" bug).

Upgrading should help, recent versions have much improved wifi support.

---

### Post by elizaram on 2011-10-13
The signal is weak because I was sitting just outside the door in my car ;)

I didn't change anything in iwconfig, so that one must be missing.

I do realize that my version is no longer supported. I've been putting off upgrading because it was such a pain to get all the hardware working with this one (it doesn't help that I have no clue what I'm doing). I will try the upgrade to 10.04 and post back here once I've got it up and running.

Thanks for all the help!

---

### Post by wildmanne39 on 2011-10-14
Hi, I will keep a check on this thread.
Thank you

---

### Post by Diametric on 2011-10-16
> **wolfen69 said:**
> Ubuntu connects to signals, not hardware. As long as your pc has the ability to use that type of connection, brand of hardware doesn't matter.

You're right - thank you for the correction.  My thought process was internal wireless card, and i took the wrong detour.  Thanks again...

---

### Post by elizaram on 2011-10-20
Okay, I upgraded to 10.04. I wasn't sure if it would work since the primary SSD on this computer is only 4 GB, but it seems to be running smoothly. And all the hardware worked pretty much from the start, which is awesome.

However, I still can't connect to that one wireless hotspot. I stopped by today to attempt it. The owner wasn't there, but I chatted with the bartender, who's quite computer literate. She said that there had been others (presumably Windows users) who had difficulty connecting with the new router, but their problems were solved by "forgetting" the connection and then rediscovering it. That was the first thing I tried, and it did not work. As far as she knows I'm the only Linux user they've encountered.

I'm at a loss for what else to try. On the plus side, this endeavor has provided a lot of excuses to go out for a beer. :)

---

### Post by wildmanne39 on 2011-10-20
Hi, when you are at the bar run the commands again in post 13 that way I can see if anything has changed since you upgraded.
Thank you

---

### Post by elizaram on 2011-11-04
Oof, busy and didn't get out there last week. Here you go, hope it's not a problem that the commands are slightly out of order. (And once again the signal strength is weak because I was doing this from outside. But I can't get online when inside either.)

```
elizabeth@Tinycat:~$ sudo iwlist scan
[sudo] password for elizabeth: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 98:2C:BE:58:C2:F9
                    Protocol:802.11b/g
                    ESSID:"KD Saloon"
                    Mode:Managed
                    Channel:1
                    Quality:39/100  Signal level:-74 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 02:60:79:9D:E4:86
                    Protocol:802.11b
                    ESSID:"megahoc.v30"
                    Mode:Ad-Hoc
                    Channel:3
                    Quality:10/100  Signal level:-86 dBm  Noise level:-97 dBm
                    Encryption key:off
                    Bit Rates:11 Mb/s

elizabeth@Tinycat:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

elizabeth@Tinycat:~$ dmesg | egrep 'net|eth|sky|sis|via|3c3|3c5|e100|8139|8169|acx|air|ath|atl|ar9|carl|atme|at7|herm|iwl|ipw|rtl8|r81|rt2|rt3|rt6|rt7|tg3|ssb|wl|b43|b44|ori|pri|p5|zd|ndis|wmi|ns8'
[    0.000000]   #5 [00008e1000 - 00008e41f4]              BRK ==> [00008e1000 - 00008e41f4]
[    0.004405] Initializing cgroup subsys net_cls
[    0.004492] CPU0: Thermal monitoring enabled (TM2)
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.335423] audit: initializing netlink socket (disabled)
[    0.415820] thermal LNXTHERM:01: registered as thermal_zone0
[    0.415853] ACPI: Thermal Zone [TZ00] (39 C)
[    0.572369] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.628139] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.679087] device-mapper: multipath: version 1.1.0 loaded
[    0.679095] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.321487] Adding 228344k swap on /dev/sda5.  Priority:-1 extents:1 across:228344k 
[    6.835221] eeepc_laptop: Get control methods supported: 0x6101713
[    7.008384] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[    7.191922] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    7.205324] rt2860 0000:01:00.0: setting latency timer to 64
[    8.038426] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.576086] wlan0: no IPv6 routers present
elizabeth@Tinycat:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux Tinycat 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
elizabeth@Tinycat:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:64:f0:fc
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fbfc0000-fbffffff ioport:ec80(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:15:af:e6:5d:07
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:f7ff0000-f7ffffff
elizabeth@Tinycat:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             unavailable
  Default:           no
  HW Address:        00:22:15:64:F0:FC

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        00:15:AF:E6:5D:07

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    megahoc.v30:     Ad-Hoc, 02:60:79:9D:E4:86, Freq 2422 MHz, Rate 0 Mb/s, Strength 15
    KD Saloon: Infra, 98:2C:BE:58:C2:F9, Freq 2412 MHz, Rate 18 Mb/s, Strength 29 WPA WPA2
    PSRT9:           Infra, 00:15:05:FB:DA:F8, Freq 2452 MHz, Rate 22 Mb/s, Strength 10 WPA
    WendysWiFi:      Infra, 68:7F:74:0C:A5:66, Freq 2457 MHz, Rate 0 Mb/s, Strength 5
    William Wilcox's Network: Infra, 10:9A:DD:88:AA:55, Freq 2412 MHz, Rate 18 Mb/s, Strength 10 WPA2
    P87J8:           Infra, 00:18:01:DA:B3:68, Freq 2452 MHz, Rate 22 Mb/s, Strength 30 WPA
    2WIRE534:        Infra, 00:1F:B3:AC:45:91, Freq 2412 MHz, Rate 18 Mb/s, Strength 15 WEP
    CTW:             Infra, 94:44:52:9E:F9:C2, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2


elizabeth@Tinycat:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
    Kernel driver in use: rt2860
    Kernel modules: rt2860sta
03:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller [1969:1026] (rev b0)
    Kernel driver in use: ATL1E
    Kernel modules: atl1e
elizabeth@Tinycat:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 98:2C:BE:58:C2:F9   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-74 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

elizabeth@Tinycat:~$ rfkill list all
0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: eeepc-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
elizabeth@Tinycat:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288611  3 
drm_kms_helper         29329  1 i915
uvcvideo               57374  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
intel_agp              24375  2 i915
serio_raw               3978  0 
rt2860sta             481561  1 
video                  17375  1 i915
soundcore               6620  1 snd
agpgart                31724  2 drm,intel_agp
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
eeepc_laptop           14331  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
atl1e                  28018  0 
elizabeth@Tinycat:~$ 

```

---

### Post by wildmanne39 on 2011-11-04
Hi, we are limited on what we can do since the router is not yours.

1. Problem could be the router is just set to N speed and your card is only able to use b/g speeds.

2. The wpa/wpa2 encryption often causes issues with linux as previously mentioned but the setting is in the router.

3. The driver your card uses is not great but you do not have a choice there really.

4. You will probably never get a connection from outside in your car to work the signal is just to weak.

We can install wicd through synaptic then get rid of network manager that may help, wicd in most causes can connect when network manager will not.

**[COLOR="Red"]After[/COLOR]** you install wicd run this command to get rid of network manager then reboot your computer please.
```
sudo apt-get purge --remove network-manager network-manager-gnome
```
Thank you

---

### Post by fdrake on 2011-11-04
beside wildmanne39's suggestions I just want to add these tips:
1.try to update/upgrade to a new kernel and see if that solves the problem
2. do you have a smart-phone with wifi? use your phone as a hotspot (or connect to it with a cable) connected to the coffee shop router.

---

