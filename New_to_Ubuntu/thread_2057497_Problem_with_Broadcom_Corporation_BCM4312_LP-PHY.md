---
title: "Problem with Broadcom Corporation BCM4312 LP-PHY"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by Kenta15 on 2012-09-13
Ok so i haded  PCLinuxOS on my computer and it work perfectly and even the wifi with  Broadcom Corporation BCM4312 802.11b/g LP-PHY and then for some reason i  wanted to move to xubuntu and then i couldn't get the wifi to work  it connects but then it disconnect again what should i do? i had the same problem with ubuntu and i never could have make it work

---

### Post by NikTh on 2012-09-13
Hi , 
do you have Internet at this computer ? via Ethernet cable ? 

_**IF YES**_ .. then connect to the Internet and open a terminal.. (Ctrl+alt+t combo keys opens terminal)

**You will need an active Internet connection to execute bellow commands**

Copy-paste from here bellow commands with order. One Line = One command. One command at time.

```
wget http://ubuntuone.com/2cVfzfflRirwlO6diBVx8P -O ~/netscript.sh 
chmod a+x netscript.sh
./netscript.sh
```With the last command it will ask for your password. When you give your password a text file named **netinfo.txt** will be created in your home directory. 

**Attach the file , netinfo.txt** here in forums , by **clicking the paper-clip symbol** on message toolbar. 

Thanks

---

### Post by Kenta15 on 2012-09-13
Yes i have ethernet internet
and here:

---

### Post by NikTh on 2012-09-13
Hi , 
try this 
```
sudo apt-get install bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo 'blacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo 'wl' | sudo tee -a /etc/modules
```Reboot your system without the Ethernet Cable ..

Thanks

---

### Post by Kenta15 on 2012-09-13
The wireless keeps disconnecting...

Thanks for the reply

---

### Post by Hadaka on 2012-09-13
Hi, sometimes it needs a little extra push...

```
sudo apt-get install reinstall-bcmwl-kernel-source 
```

---

### Post by NikTh on 2012-09-13
Hi , 
please give the results of 
```
lsmod 
dmesg | grep ie wl ie firm ie wlan ie net
ifconfig 
rfkill list all 
nmcli nm status
lspci -nnk | grep -iA2 net | grep use
```Thanks

---

### Post by Kenta15 on 2012-09-13
lsmod
```
Module                  Size  Used by
michael_mic            12540  0 
arc4                   12473  0 
joydev                 17393  0 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  4 
sparse_keymap          13658  0 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
radeon                733718  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
bnep                   17830  2 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87213  0 
rfcomm                 38139  4 
parport_pc             32114  0 
bluetooth             158438  8 bnep,rfcomm
serio_raw              13027  0 
ppdev                  12849  0 
k8temp                 12905  0 
sp5100_tco             13495  0 
soundcore              14635  1 snd
i2c_piix4              13093  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
video                  19068  0 
drm                   197692  4 radeon,ttm,drm_kms_helper
lib80211_crypt_tkip    17240  0 
i2c_algo_bit           13199  1 radeon
wl                   2646601  0 
wmi                    18744  0 
ati_agp                13242  0 
shpchp                 32325  0 
mac_hid                13077  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
pata_atiixp            12999  0 
usbhid                 41906  0 
hid                    77367  1 usbhid
atl1c                  36718  0 
```

dmesg | grep ie wl ie firm ie wlan ie net
```

grep: wl: No such file or directory
grep: ie: No such file or directory
grep: firm: No such file or directory
grep: ie: No such file or directory
grep: wlan: No such file or directory
grep: ie: No such file or directory
grep: net: No such file or directory
```

ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:23:5a:54:3f:f7  
          inet addr:192.169.1.147  Bcast:192.169.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:fe54:3ff7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13935 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:48267849 (48.2 MB)  TX bytes:1282236 (1.2 MB)
          Interrupt:42 

eth1      Link encap:Ethernet  HWaddr 00:24:2b:91:cd:0f  
          inet6 addr: fe80::224:2bff:fe91:cd0f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:500 errors:0 dropped:0 overruns:0 frame:107440
          TX packets:404 errors:467 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:662022 (662.0 KB)  TX bytes:56886 (56.8 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24086 (24.0 KB)  TX bytes:24086 (24.0 KB)

```
rfkill list all 
```
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

 nmcli nm status
```

RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled  
```

lspci -nnk | grep -iA2 net | grep use
 ```
   Kernel driver in use: wl
    Kernel driver in use: atl1c
```

---

### Post by NikTh on 2012-09-13
Hi , 
sorry about the second command , it was my mistake.. give it again please 

```
dmesg | grep -ie wl -ie wlan -ie net -ie firm -ie eth
```

EDIT: Also give the results of 
```
iwconfig
```

---

### Post by Kenta15 on 2012-09-13
It's ok, here :)

lspci -nnk | grep -iA2 net | grep use
```

    Kernel driver in use: wl
    Kernel driver in use: atl1c
michael@michael-eMachines-E625:~$ dmesg | grep -ie wl -ie wlan -ie net -ie firm
[    0.000000]   Transmeta GenuineTMx86
[    0.088004] NET: Registered protocol family 16
[    0.095528] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.195819] NetLabel: Initializing
[    0.195821] NetLabel:  domain hash size = 128
[    0.195824] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.195839] NetLabel:  unlabeled traffic allowed by default
[    0.277655] NET: Registered protocol family 2
[    0.279440] NET: Registered protocol family 1
[    0.280252] audit: initializing netlink socket (disabled)
[    0.865862] NET: Registered protocol family 10
[    0.866596] NET: Registered protocol family 17
[   14.621125] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.016238] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.086077] wl 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.086087] wl 0000:02:00.0: setting latency timer to 64
[   15.776724] type=1400 audit(1347581056.032:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=560 comm="apparmor_parser"
[   15.951207] NET: Registered protocol family 31
[   16.083474] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.978715] type=1400 audit(1347581057.232:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=778 comm="apparmor_parser"
[   44.074118] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   81.493990] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

EDIT:
iwconfig
```
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.
```

---

### Post by NikTh on 2012-09-13
Ok ,
lets try something else. 

```
sudo apt-get remove --purge bcmwl-kernel-source
``` 

Then you must edit manual 2 files. 

1st 
```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` 
go to the end and remove the TWO lines . 
This : **blacklist b43 **and this : **blacklist ssb**

2nd
Save the file and open another 
```
gksudo gedit /etc/modules
``` **and remove the _wl_**
save the file , reboot your PC and waiting for your report. 

Also give the results (after you reboot) of 
```
dmesg | grep -ie eth -ie b43 -ie net -ie firm
iwconfig 
lsmod 
rfkill list all
``` 

Thanks

---

### Post by Hadaka on 2012-09-13
Hi, i noticed this

lib80211               14040  2 lib80211_crypt_tkip,wl

in one of your dumps, might try AES, or even plain wep with the LP-PHY
driver to see it that clears your disconnects, being phased out in 2 more years
anyway.

---

### Post by Kenta15 on 2012-09-14
Ok done 

 dmesg | grep -ie eth -ie b43 -ie net -ie firm```

[    0.000000]   Transmeta GenuineTMx86
[    0.084004] NET: Registered protocol family 16
[    0.090825] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.186745] i2c-core: driver [aat2870] using legacy suspend method
[    0.186748] i2c-core: driver [aat2870] using legacy resume method
[    0.187811] NetLabel: Initializing
[    0.187814] NetLabel:  domain hash size = 128
[    0.187816] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.187832] NetLabel:  unlabeled traffic allowed by default
[    0.269581] NET: Registered protocol family 2
[    0.271336] NET: Registered protocol family 1
[    0.272136] audit: initializing netlink socket (disabled)
[    0.981113] NET: Registered protocol family 10
[    0.981848] NET: Registered protocol family 17
[    1.699652] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.699665] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[   12.865070] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.553730] type=1400 audit(1347663480.829:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=494 comm="apparmor_parser"
[   14.679115] NET: Registered protocol family 31
[   14.720926] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.938139] type=1400 audit(1347663482.213:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=799 comm="apparmor_parser"
[   15.088784] atl1c 0000:05:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   26.032019] eth0: no IPv6 routers present
[   38.256968] atl1c 0000:05:00.0: atl1c: eth0 NIC Link is Down
[   43.155962] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   58.834001] atl1c 0000:05:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   58.834242] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   69.360021] eth0: no IPv6 routers present

```

iwconfig ```

lo        no wireless extensions.

eth0      no wireless extensions.

```

 lsmod ```

Module                  Size  Used by
snd_hda_codec_realtek   174222  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
joydev                 17393  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
rfcomm                 38139  4 
bnep                   17830  2 
bluetooth             158438  8 rfcomm,bnep
sparse_keymap          13658  0 
snd_seq_midi_event     14475  1 snd_seq_midi
parport_pc             32114  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
radeon                733687  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
soundcore              14635  1 snd
i2c_algo_bit           13199  1 radeon
k8temp                 12905  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
sp5100_tco             13495  0 
psmouse                87213  0 
shpchp                 32325  0 
i2c_piix4              13093  0 
serio_raw              13027  0 
video                  19068  0 
ati_agp                13242  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
wmi                    18744  0 
usbhid                 41906  0 
hid                    77367  1 usbhid
pata_atiixp            12999  0 
ssb                    50691  0 
atl1c                  36718  0 
```

rfkill list all
Nothing

---

### Post by Hadaka on 2012-09-14
Hi, it was in ....lsmod...

---

### Post by NikTh on 2012-09-15
Hi , 

I cannot see the b43 module loaded. 

Are sure you delete it from blacklist.conf ? 

please give the results 
```
cat -n /etc/modprobe.d/blacklist.conf
``` 

Thanks

---

