---
title: "Can't connect to wireless network with Ubuntu 11.10.."
date: 2012-04-04
forum: New to Ubuntu
---

### Post by Meiji on 2012-04-04
Hi everyone! I've looked a lot on the net but I can't get to solve this problem, hope somebody can help me.

I've installed Ubuntu 11.10 on my Toshiba Satellite A505D-S6958. I can surf the web if I'm using a cable, but when I try to do it with my WiFi, it detects the net, says I'm connected, but I just can't surf, as if I weren't connected at all.

I'm not sure what's the problem and after several days looking for a solution I'm getting desperated. I'm posting some details of my connection:

Driver: rtl819xE

**lspci | grep Realtek**
```

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"INFINITUM7B670F"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 08:76:FF:5D:16:14   
          Bit Rate=65 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-49 dBm  Noise level=-117 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

If you need any other information just let me know. Thanks in advance!

---

### Post by wildmanne39 on 2012-04-04
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by papibe on 2012-04-04
Hi Meiji.

Make sure wlan0 is properly set up. Open 'Network Connection'. Go to the Wireless tab, select wlan0 and press edit.

In the new windows make sure that 'Connect Automatically' is selected. Then in the IPv4 tab, make sure the Method is: Automatic DHCP.

Hope that helps, and tell us how it goes.
Regards.

---

### Post by Meiji on 2012-04-04
Thank you for your answers :)

**Papibe**, yes, it's all already set as you told me: Connected Automatically and method Automatic DHCP.

**wildmanne39**, I'm posting the results of the codes you gave me, hope that helps! Thanks!


**cat /etc/lsb-release; uname -a**
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux meiji-Satellite-A505D 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 athlon i386 GNU/Linux

```

**lspci -nnk | grep -iA2 net**
```

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8182]
	Kernel driver in use: rtl819xE
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: r8169

```

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"INFINITUM7B670F"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 08:76:FF:5D:16:14   
          Bit Rate=65 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=81/100  Signal level=-59 dBm  Noise level=-110 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**rfkill list all**
```

Shows nothing :( ..

```

**lsmod**
```

Module                  Size  Used by
arc4                   12473  2 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
r8192_pci             244331  0 
snd_hda_codec_realtek   254163  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
rtl8192se              94139  0 
rtlwifi                95614  1 rtl8192se
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
mac80211              393421  2 rtl8192se,rtlwifi
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                929507  3 
ttm                    65224  1 radeon
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 radeon
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172427  2 rtlwifi,mac80211
drm                   192194  5 radeon,ttm,drm_kms_helper
sp5100_tco             13495  0 
i2c_algo_bit           13199  1 radeon
soundcore              12600  1 snd
psmouse                73673  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
k10temp                12990  0 
video                  18908  0 
i2c_piix4              13093  0 
shpchp                 32356  0 
serio_raw              12990  0 
sparse_keymap          13658  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci
pata_atiixp            12967  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci

```

---

### Post by wildmanne39 on 2012-04-04
Hi, try this please:
```
echo "blacklist r8192_pci" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
reboot does it work now?
Thanks

---

### Post by Meiji on 2012-04-04
Hi again! I've just tried it and now I doesn't have WiFi signal at all =P.. It does exist if I go to Edit Conections though.. Should I manually configure it? 

Thanks again!

---

### Post by wildmanne39 on 2012-04-04
Hi, no you do not need to manually configure it that will create more problems usually.

Please post the output of:
```
nm-tool
sudo iwlist scan
lsmod | grep rtl
dmesg | egrep 'rtl|firm|radio|switch|wlan0'
```
Thanks

---

### Post by Meiji on 2012-04-04
Hi! Here are the outputs:

**nm-tool**
```

NetworkManager Tool

State: disconnected

- Device: eth0
-----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:1E:33:BE:44:33

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

```

**sudo iwlist scan**
```

[sudo] password for meiji: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

**lsmod | grep rtl**
```

rtl8192se              94139  0 
rtlwifi                95614  1 rtl8192se
mac80211              393421  2 rtl8192se,rtlwifi
cfg80211              172427  2 rtlwifi,mac80211

```

**dmesg | egrep 'rtl|firm|radio|switch|wlan0'**
```

[   18.484761] rtl8192se 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.484772] rtl8192se 0000:02:00.0: setting latency timer to 64
[   18.484842] rtl8192se 0000:02:00.0: PCI INT A disabled
[   20.567582] Console: switching to colour frame buffer device 170x48

```

Thanks a lot!

---

### Post by wildmanne39 on 2012-04-05
Hi, install the rfkill package then run these commands please:
```
rfkill list all
dmesg | grep 819
```
Thanks

---

### Post by Meiji on 2012-04-06
Thank you again wildmanne39! I think I already had rfkill installed, when I ran the sudo I got this (a quick translation to English from me since I have it in Spanish):

**sudo apt-get install rfkill**
```

[sudo] password for meiji: 
Reading list of packages... Done
Creating tree of dependencies
Reading state information... Done
rfkill is already in its most recent version
0 updated, 0 will be installed, 0 will be erased and 0 no updated.

```

Then when I write the codes you gave I get this:

**rfkill list all**
```

Still shows nothing...

```

**dmesg | grep 819**
```

[    0.008197] Initializing cgroup subsys devices
[    0.655217] pci 0000:02:00.0: [10ec:8192] type 0 class 0x000280
[    0.668199] pci 0000:05:00.0: [1180:e822] type 0 class 0x000805
[    1.181947] msgmni has been set to 1676
[    1.568191] hub 1-0:1.0: 6 ports detected
[   17.819157] type=1400 audit(1333611734.445:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=491 comm="apparmor_parser"
[   18.747223] rtl8192se 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.747235] rtl8192se 0000:02:00.0: setting latency timer to 64
[   18.747306] rtl8192se 0000:02:00.0: PCI INT A disabled
[   18.998197] [drm] Radeon display connector LVDS-1: Found valid EDID

```

Thanks a lot!

---

### Post by wildmanne39 on 2012-04-06
Hi, please post the contents of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by Meiji on 2012-04-06
Thank you! Here's the output:

**cat /etc/modprobe.d/blacklist.conf**
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist r8192_pci

```

---

### Post by wildmanne39 on 2012-04-06
Hi, ok let's try using the other driver that was loaded. Please do:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
remove [COLOR="Red"]blacklist r8192_pci[/COLOR] and add [COLOR="Red"]blacklist rtl8192se      [/COLOR]
then save and close gedit, then reboot.
Thanks

---

### Post by Meiji on 2012-04-06
Hi! I've done it. I'm back to the beginning, it detects the network and says I'm connected, but when I open a browser and go to any site, it says 'server not found', as if I weren't connected at all.

---

### Post by wildmanne39 on 2012-04-06
Hi lets try these commands now that you have switched drivers and there should only be one loaded now.
```
nm-tool
sudo iwlist scan
lsmod | grep r81
```
```
sudo cat /var/log/syslog | grep -e r81 -e firmware -e wlan -e wpa -e etork | tail -n55
```
Thanks

---

### Post by Meiji on 2012-04-07
Thank you! It still doesn't work =(  Here're the outputs:


**nm-tool**
```

NetworkManager Tool

State: connected (global)

- Device: wlan0  [INFINITUM7B670F] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xE
  State:             connected
  Default:           yes
  HW Address:        00:24:D2:8A:F1:52

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *INFINITUM7B670F:Infra, 08:76:FF:5D:16:14, Freq 2462 MHz, Rate 1 Mb/s, Strength 82 WEP
    arris54g:        Infra, 00:1D:CF:06:44:83, Freq 2462 MHz, Rate 54 Mb/s, Strength 69
    INFINITUMB5E803: Infra, 00:26:44:D8:67:10, Freq 2412 MHz, Rate 1 Mb/s, Strength 69 WEP
    INFINITUM613568: Infra, 08:76:FF:74:7C:D4, Freq 2462 MHz, Rate 1 Mb/s, Strength 60 WEP
    INFINITUMc4b3:   Infra, 4C:54:99:86:84:00, Freq 2427 MHz, Rate 7 Mb/s, Strength 69 WEP
    INFINITUMc82a:   Infra, 64:16:F0:9F:75:37, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WEP
    Motorola14:      Infra, 00:21:00:18:38:5D, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WEP
    Vaguira:         Infra, 00:15:D1:36:58:14, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA
    vegacruz:        Infra, 00:15:D0:E4:9C:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA

  IPv4 Settings:
    Address:         192.168.1.67
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:1E:33:BE:44:33

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

```

**sudo iwlist scan**
```

[sudo] password for meiji: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 64:16:F0:9F:75:37
                    ESSID:"INFINITUMc82a"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=71/100  Signal level=-59 dBm  Noise level=-105 dBm
                    Extra: Last beacon: 163ms ago
          Cell 02 - Address: 00:26:44:D8:67:10
                    ESSID:"INFINITUMB5E803"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:65 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-59 dBm  Noise level=-102 dBm
                    Extra: Last beacon: 161ms ago
          Cell 03 - Address: 00:1D:CF:06:44:83
                    ESSID:"arris54g"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=69/100  Signal level=-60 dBm  Noise level=-104 dBm
                    Extra: Last beacon: 12ms ago
          Cell 04 - Address: 00:21:00:18:38:5D
                    ESSID:"Motorola14"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=72/100  Signal level=-60 dBm  Noise level=-106 dBm
                    Extra: Last beacon: 6ms ago
          Cell 05 - Address: 08:76:FF:5D:16:14
                    ESSID:"INFINITUM7B670F"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:65 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=79/100  Signal level=-60 dBm  Noise level=-109 dBm
                    Extra: Last beacon: 4ms ago
          Cell 06 - Address: 00:15:D0:E4:9C:E0
                    ESSID:"vegacruz"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=63/100  Signal level=-60 dBm  Noise level=-101 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2ms ago

```

**lsmod | grep r81**
```

r8192_pci             244331  0 
r8169                  43104  0

```

**sudo cat /var/log/syslog | grep -e r81 -e firmware -e wlan -e wpa -e etork | tail -n55**
```

Apr  7 11:02:08 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr  7 11:02:08 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr  7 11:02:08 meiji-Satellite-A505D NetworkManager[856]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr  7 11:02:08 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0/wireless): connection 'INFINITUM7B670F' has security, and secrets exist.  No new secrets needed.
Apr  7 11:02:08 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr  7 11:02:10 meiji-Satellite-A505D NetworkManager[856]: <info> (wlan0): supplicant interface state: inactive -> scanning
Apr  7 11:02:15 meiji-Satellite-A505D wpa_supplicant[1049]: Trying to associate with 08:76:ff:5d:16:14 (SSID='INFINITUM7B670F' freq=2462 MHz)
Apr  7 11:02:15 meiji-Satellite-A505D wpa_supplicant[1049]: Association request to the driver failed
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> (wlan0): supplicant interface state: scanning -> associating
Apr  7 11:02:15 meiji-Satellite-A505D wpa_supplicant[1049]: CTRL-EVENT-DISCONNECTED bssid=08:76:ff:5d:16:14 reason=0
Apr  7 11:02:15 meiji-Satellite-A505D wpa_supplicant[1049]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> (wlan0): supplicant interface state: associating -> disconnected
Apr  7 11:02:15 meiji-Satellite-A505D wpa_supplicant[1049]: Associated with 08:76:ff:5d:16:14
Apr  7 11:02:15 meiji-Satellite-A505D wpa_supplicant[1049]: CTRL-EVENT-CONNECTED - Connection to 08:76:ff:5d:16:14 completed (auth) [id=0 id_str=]
Apr  7 11:02:15 meiji-Satellite-A505D kernel: [   35.829123] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> (wlan0): supplicant interface state: disconnected -> completed
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'INFINITUM7B670F'.
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Beginning IP6 addrconf.
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr  7 11:02:15 meiji-Satellite-A505D dhclient: Listening on LPF/wlan0/00:24:d2:8a:f1:52
Apr  7 11:02:15 meiji-Satellite-A505D dhclient: Sending on   LPF/wlan0/00:24:d2:8a:f1:52
Apr  7 11:02:15 meiji-Satellite-A505D dhclient: DHCPREQUEST of 192.168.1.67 on wlan0 to 255.255.255.255 port 67
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Apr  7 11:02:15 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Apr  7 11:02:15 meiji-Satellite-A505D avahi-daemon[853]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.67.
Apr  7 11:02:15 meiji-Satellite-A505D avahi-daemon[853]: New relevant interface wlan0.IPv4 for mDNS.
Apr  7 11:02:15 meiji-Satellite-A505D avahi-daemon[853]: Registering new address record for 192.168.1.67 on wlan0.IPv4.
Apr  7 11:02:16 meiji-Satellite-A505D avahi-daemon[853]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::224:d2ff:fe8a:f152.
Apr  7 11:02:16 meiji-Satellite-A505D avahi-daemon[853]: New relevant interface wlan0.IPv6 for mDNS.
Apr  7 11:02:16 meiji-Satellite-A505D avahi-daemon[853]: Registering new address record for fe80::224:d2ff:fe8a:f152 on wlan0.*.
Apr  7 11:02:16 meiji-Satellite-A505D kernel: [   36.617625] wlan0: IPv6 duplicate address fe80::224:d2ff:fe8a:f152 detected!
Apr  7 11:02:16 meiji-Satellite-A505D NetworkManager[856]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr  7 11:02:16 meiji-Satellite-A505D NetworkManager[856]: <info> Policy set 'INFINITUM7B670F' (wlan0) as default for IPv4 routing and DNS.
Apr  7 11:02:16 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) successful, device activated.
Apr  7 11:02:16 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Apr  7 11:02:16 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr  7 11:02:35 meiji-Satellite-A505D NetworkManager[856]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr  7 11:02:35 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Apr  7 11:02:35 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Apr  7 11:02:35 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Apr  7 11:02:35 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Apr  7 11:02:35 meiji-Satellite-A505D NetworkManager[856]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Apr  7 11:03:04 meiji-Satellite-A505D dhclient: DHCPREQUEST of 192.168.1.67 on wlan0 to 192.168.1.254 port 67
Apr  7 11:03:21 meiji-Satellite-A505D dhclient: DHCPREQUEST of 192.168.1.67 on wlan0 to 192.168.1.254 port 67
Apr  7 11:07:08 meiji-Satellite-A505D dhclient: DHCPREQUEST of 192.168.1.67 on wlan0 to 192.168.1.254 port 67
Apr  7 11:08:25 meiji-Satellite-A505D dhclient: DHCPREQUEST of 192.168.1.67 on wlan0 to 192.168.1.254 port 67
Apr  7 11:08:43 meiji-Satellite-A505D dhclient: DHCPREQUEST of 192.168.1.67 on wlan0 to 192.168.1.254 port 67
Apr  7 11:09:04 meiji-Satellite-A505D dhclient: DHCPREQUEST of 192.168.1.67 on wlan0 to 192.168.1.254 port 67

```

---

### Post by wildmanne39 on 2012-04-07
Hi, can you change your encryption settings in your router to just wpa2 not wep or wpa/wpa2? if not try wpa2/wpa.

Next set your settings in network manager to look like the settings in the screenshots.

Did you set your settings manually or did you let network manager do it?
Thanks

---

### Post by Meiji on 2012-04-07
> **wildmanne39 said:**
> Hi, can you change your encryption settings in your router to just wpa2 not wep or wpa/wpa2? if not try wpa2/wpa.
Hi! I'm kinda newbie and I'm not really sure how to do that. I checked my router and it doesn't have any button, only the lights I show in the file attached (Internet and Wireless are blinking all the time).

I've set the settings in network manager as you told me anyways, I rebooted and I must say it worked the first minute, after that it isn't working anymore. But this happens sometimes anyways, it suddenly works for 1-2 minutes then again nothing.

I haven't configured it manually, it's all done by network manager. Only thing I did was typing my hex password.

---

### Post by wildmanne39 on 2012-04-07
Hi, when it connected did you actually load web pages?

You should be able to change your encryption in your router by typing 192.168.0.1 into your web browser with your computer hard wired to the internet.
Thanks

---

### Post by yelram on 2012-04-23
Hi I've got a similar problem.  I'm currently running 11.10 on a lenovo T510 with a realtek 8192se wireless.  I can detect wireless networks.  It will connect with authentication.  It will obtain an address from DHCP, I can ping the default gateway, but beyond that... nothing.  I've tried the different kernel modules to no avail.

What I have found is that it works for some wireless networks and not others.  For example, I had a Billion 7402vgp wireless dsl modem at home and that was working fine.  Then I replaced it with a thompson TG587n-v3, and that doesn't work.

It appears that if the access point supports 802.11n, I have problems.  The old 7402vgp didn't support n, the new one does.  One of my customers upgraded their wireless infrastructure and it stopped working when I was on site.  My solution has been to buy a cheap usb 802.11n dongle which works find on all networks I've tried.  But it's annoying to have to pull out a usb dongle.

Oh, this problem has been around since before 11.10 as well.

---

### Post by wildmanne39 on 2012-04-23
Hi, change it in the router to 802.11g only.
Thanks

---

