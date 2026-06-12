---
title: "Broadcom 4312 in Natty not working"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by Furbybrain on 2011-09-14
Hi, like a lot of people I've been struggling with the 4312. I sorted out the "wireless disabled by hardware switch" problem (you bizarrely have to turn on Bluetooth in the BIOS), now it's working for a minute after boot up then stopping.   This isn't a security issue, as I tried turning off the encryption on my router and it still didn't work, while my phone connected fine both with and without WPA.  I've followed this thread: [http://ubuntuforums.org/showthread.php?t=1819015&page=2](http://ubuntuforums.org/showthread.php?t=1819015&page=2) but I have both b43-fwcutter and firmware-b43-lpphy-installer installed.  I don't really understand whats going on with b43 and STA- are they alternative drivers? I can't install STA in Additional Drivers either.  Thanks :)

---

### Post by westie457 on 2011-09-14
> **Furbybrain said:**
> Hi, like a lot of people I've been struggling with the 4312. I sorted out the "wireless disabled by hardware switch" problem (you bizarrely have to turn on Bluetooth in the BIOS), now it's working for a minute after boot up then stopping.   This isn't a security issue, as I tried turning off the encryption on my router and it still didn't work, while my phone connected fine both with and without WPA.  I've followed this thread: [http://ubuntuforums.org/showthread.php?t=1819015&page=2](http://ubuntuforums.org/showthread.php?t=1819015&page=2) but I have both b43-fwcutter and firmware-b43-lpphy-installer installed.  I don't really understand whats going on with b43 and STA- are they alternative drivers? I can't install STA in Additional Drivers either.  Thanks :)

Hi referring you back to the link you posted can you post the output of all the commands that wildmanne39 suggested on page 1 of that thread.
He put a lot of effort into helping the OP there and my 2 cents worth was put at the end.

Thank you.

---

### Post by Furbybrain on 2011-09-14
sudo lshw -C network
```
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:24:78:69
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.0.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:7b:cd:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```nm-tool```
NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:22:5F:7B:CD:1B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:23:AE:24:78:69

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

```lspci -nn | grep 0280```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```iwconfig```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"PlusnetWireless8A1F68"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```rfkill list all```
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```lsmod | grep b43```
b43                   163523  0 
ssb                    38671  1 b43
mac80211              205146  1 b43
cfg80211              126517  2 b43,mac80211
led_class               2864  1 b43
```

---

### Post by Furbybrain on 2011-09-14
I've removed all the packages except the  ones you said in the other thread, it still disconnects after a minute or two, having worked perfectly.  I'll post the other outputs as well: 

modinfo b43 ```
filename:       /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
firmware:       b43/pcm5.fw
firmware:       b43/n0initvals11.fw
firmware:       b43/n0bsinitvals11.fw
firmware:       b43/n0absinitvals11.fw
firmware:       b43/lp0initvals15.fw
firmware:       b43/lp0initvals14.fw
firmware:       b43/lp0initvals13.fw
firmware:       b43/lp0bsinitvals15.fw
firmware:       b43/lp0bsinitvals14.fw
firmware:       b43/lp0bsinitvals13.fw
firmware:       b43/b0g0initvals9.fw
firmware:       b43/b0g0initvals5.fw
firmware:       b43/b0g0initvals13.fw
firmware:       b43/b0g0bsinitvals9.fw
firmware:       b43/b0g0bsinitvals5.fw
firmware:       b43/b0g0bsinitvals13.fw
firmware:       b43/a0g1initvals9.fw
firmware:       b43/a0g1initvals5.fw
firmware:       b43/a0g1initvals13.fw
firmware:       b43/a0g1bsinitvals9.fw
firmware:       b43/a0g1bsinitvals5.fw
firmware:       b43/a0g1bsinitvals13.fw
firmware:       b43/a0g0initvals9.fw
firmware:       b43/a0g0initvals5.fw
firmware:       b43/a0g0bsinitvals9.fw
firmware:       b43/a0g0bsinitvals5.fw
license:        GPL
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     529A0228ED5973C9AAB521F
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,led-class,cfg80211
vermagic:       2.6.32-24-generic SMP mod_unload modversions 586 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

```dmesg | grep b43```
[   22.537717] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.537733] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   23.039478] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   23.214789] Registered led device: b43-phy0::tx
[   23.214806] Registered led device: b43-phy0::rx
[   23.214823] Registered led device: b43-phy0::radio
[   27.796264] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   28.386929] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[   28.462949] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[   28.792265] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  244.970730] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  244.970741] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.
[  244.970746] b43-phy0: Controller RESET (DMA error) ...
[  245.204267] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  250.785115] b43-phy0: Controller restarted

```sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 1C:7E:E5:CB:D1:FA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-3 dBm  
                    Encryption key:on
                    ESSID:"SKY12774"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000bb8b6d252
                    Extra: Last beacon: 664ms ago
                    IE: Unknown: 0008534B593132373734
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 30:46:9A:81:05:5E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Nostromo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c1bc398b97
                    Extra: Last beacon: 1168ms ago
                    IE: Unknown: 00084E6F7374726F6D6F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B000103104700108D03B5B1C362E1E98FCA35C33028BD321021000D4E4554474541522C20496E632E10230008574E44523334303010240008574E4452333430301042000230311054000800060050F204000110110008574E445233343030100800020084103C000103
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081100000000000000000000000000000000000000


```

(My router is SKY12774)

---

### Post by westie457 on 2011-09-14
This has got me confused. You have the correct drivers as you have already stated and as you also know the STA driver will not work with your card.

Have been searching for alternatives. This one might work [http://ubuntuforums.org/archive/index.php/t-1700897.html](http://ubuntuforums.org/archive/index.php/t-1700897.html) around post 14 is a viable solution.

Download from the provided link and install. Then remove the current lp-phy driver leaving the fwcutter alone. Reboot and everything should be working properly. If not post back here and there will be more help. 

If it works mark the thread SOLVED using 'Thread Tools' near the top of the page on the right.

Thank you.

---

### Post by Furbybrain on 2011-09-14
It says "Device not ready (firmware missing)" now I've removed firmware-b43-lpphy-installer. Hmm

---

### Post by westie457 on 2011-09-14
Oh well, that idea did not work.

Remove the STA driver I asked you to install and reinstall the lp-phy one and reboot just to get you back to the start.

Open Synaptic Package Manager go to Setting > Repositories and in the update tab check the box for unsupported updates (natty backports) close the window and reload when prompted.

Update Manager will kick in with new updates that you may or may not want - not all of them will be necessary. Check through these updates to see if any are suggested for wireless/bluetooth. If none close update manager and reopen Synaptic. Click on Search not Quick Search and type in compat-wireless. In the results page pick the one that matches your current kernel eg 2.6.35-30. No idea if you will need to reboot however the system will prompt you for that.

Hopefully this will work for you. The idea was found in this old thread [http://ubuntuforums.org/archive/index.php/t-1642663.html](http://ubuntuforums.org/archive/index.php/t-1642663.html)

Good luck.

---

### Post by Furbybrain on 2011-09-15
Oh wow, it seems to have fixed itself... *FOR NOW.* I was messing around with it last night, tried uninstalling all the B43 stuff and had another go with STA. Now I've just purged everything STA related and put the B43 stuff back it's working. Maybe I had to purge it instead of just plain removing it?

Anyway, thanks for your help, a fair few people have had problems with the Broadcom chips so it's good to see how much help theres been on the community since this emerged for me.

---

### Post by Furbybrain on 2011-09-15
It didn't last. So I did what you said westie457, nothing relevant on Update Manager so I searched for compat-wireless.

They're all for 2.6.38, while I'm stuck on 2.6.32 (according to uname -r)... I believe this is a Grub problem, I'll have a look if I can work out why update-grub isn't going to the latest kernel.

---

### Post by Furbybrain on 2011-09-15
So I've fixed Grub (or rather Burg), now it's loading 2.6.38 properly. I installed the compat-wireless (it may have taken the meta-package to work), it's still only working sporadically.

---

