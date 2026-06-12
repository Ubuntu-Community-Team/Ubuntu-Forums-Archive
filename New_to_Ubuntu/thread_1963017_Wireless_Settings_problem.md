---
title: "Wireless Settings problem"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Deadman390 on 2012-04-21
ok after much headache frustrated moments and a carton of cigs i have got the internet working and is all good but after a shut down or restart i lose it and have to reinstall the driver everytime i log on

---

### Post by wildmanne39 on 2012-04-21
Deleted

---

### Post by wildmanne39 on 2012-04-21
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Deadman390 on 2012-04-22
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```by clicking on new reply and click # and paste the information between the brackets.
Thank you
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13fe:3623 Kingston Technology Company Inc. 
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"DEADMAN-PC_Network_1"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 98:FC:11:C1:E3:CA   
          Bit Rate=52 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Module                  Size  Used by
ndiswrapper           193669  0 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
nls_utf8               12493  1 
isofs                  39549  1 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
snd_hda_codec_hdmi     31426  4 
binfmt_misc            17292  1 
snd_seq_midi           13132  0 
snd_hda_codec_realtek   254163  1 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hda_intel          24262  3 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
nouveau               663263  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  2 snd_seq,snd_pcm
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
snd                    55902  16 snd_hda_codec_hdmi,snd_rawmidi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
drm                   192194  4 nouveau,ttm,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  18908  1 nouveau
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  1 
uas                    17699  0 
ahci                   21634  1 
libahci                25727  1 ahci
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
```ok thats what i got when i entered the codes....sri if i sent more information than needed

---

### Post by wildmanne39 on 2012-04-22
Hi, I believe this will fix your problem.
```
sudo su 
echo ndiswrapper >> /etc/modules 
exit
```
Then reboot.
Thanks

---

### Post by Deadman390 on 2012-04-22
> **wildmanne39 said:**
> Hi, I believe this will fix your problem.
```
sudo su 
echo ndiswrapper >> /etc/modules 
exit
```
Then reboot.
Thanks

ok so i entered the above code and now my wireless card works but it cant acquire any wireless signal it just hunts and hunts and never actually connects

---

### Post by wildmanne39 on 2012-04-22
Hi, that is strange I do not think it is because of the code I gave you that code just makes it started on boot up.

Please post the output from:
```
nm-tool
sudo iwlist scan
lsmod | grep ndiswrapper
```
```
sudo cat /var/log/syslog | grep -e ndi -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by Deadman390 on 2012-04-22
> **wildmanne39 said:**
> Hi, that is strange I do not think it is because of the code I gave you that code just makes it started on boot up.

Please post the output from:
```
nm-tool
sudo iwlist scan
lsmod | grep ndiswrapper
```
```
sudo cat /var/log/syslog | grep -e ndi -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

problem with posting lol im on my wifes laptop atm i have my command center running now lol laptop next to the desktop so i can type everything is puts out but it will just take me awhile

---

### Post by wildmanne39 on 2012-04-22
Hi, do you have a flash drive you can copy and paste too and from?
Thanks

---

### Post by Deadman390 on 2012-04-22
the thing i can tell u the fastest is that the last command u gave me i get a no such file or directory code

---

### Post by wildmanne39 on 2012-04-22
The long command by itself?

---

### Post by Deadman390 on 2012-04-22
> **wildmanne39 said:**
> Hi, do you have a flash drive you can copy and paste too and from?
Thanks

```
- Device: wlan0  [HPC310a.CE48D8] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connecting (configuring)
  Default:           no
  HW Address:        20:4E:7F:F2:0C:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    HPC310a.CE48D8:  Ad-Hoc, E6:F2:D8:6E:79:16, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    NETGEAR1:        Infra, C0:3F:0E:AD:F7:1A, Freq 2462 MHz, Rate 54 Mb/s, Strength 19
    DEADMAN-PC_Network_1: Infra, 98:FC:11:C1:E3:CA, Freq 2437 MHz, Rate 54 Mb/s, Strength 95
    Tyler's Network: Infra, 00:1C:DF:F2:D4:B1, Freq 2437 MHz, Rate 54 Mb/s, Strength 25
    dlink:           Infra, 14:D6:4D:2A:F3:8E, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    dg:              Infra, 00:11:50:9E:58:3C, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    DWG855B3:        Infra, 00:1E:69:94:C1:B8, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    ASHLEY-PC_Network_1: Infra, 20:4E:7F:08:63:36, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2


deadman390@ubuntu:~$ sudo iwlist scan
[sudo] password for deadman390: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 98:FC:11:C1:E3:CA
                    ESSID:"DEADMAN-PC_Network_1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: E6:F2:D8:6E:79:16
                    ESSID:"HPC310a.CE48D8"
                    Protocol:IEEE 802.11g
                    Mode:Ad-Hoc
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 14:D6:4D:2A:F3:8E
                    ESSID:"dlink"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 20:4E:7F:08:63:36
                    ESSID:"ASHLEY-PC_Network_1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:11:50:9E:58:3C
                    ESSID:"dg"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

deadman390@ubuntu:~$ lsmod | grep ndiswrapper
ndiswrapper           193669  0 
deadman390@ubuntu:~$ sudo cat /war/log/syslog  |  grep -e ndi -e firmware -e wpa -e wlan -e etork  |  tail -n55
cat: /war/log/syslog: No such file or directory
```

and the idea with the jump drive is why I am asking the questions and YOU are answering them lol i didnt even think of that man

---

### Post by wildmanne39 on 2012-04-22
Hi, try this command again and just copy and paste for accuracy:
```
sudo cat /var/log/syslog | grep -e ndi -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by Deadman390 on 2012-04-22
```

deadman390@ubuntu:~$ sudo cat /war/log/syslog  |  grep -e ndi -e firmware -e wpa -e wlan -e etork  |  tail -n55
cat: /war/log/syslog: No such file or directory
deadman390@ubuntu:~$ 


sudo cat /var/log/syslog | grep -e ndi -e firmware -e wpa -e wlan -e etork | tail -n55








Apr 22 13:33:13 ubuntu NetworkManager[803]: <info> (wlan0): supplicant interface state: completed -> disconnected
Apr 22 13:33:16 ubuntu NetworkManager[803]: <info> Activation (wlan0) starting connection 'HPC310a.CE48D8'
Apr 22 13:33:16 ubuntu NetworkManager[803]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 22 13:33:16 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 22 13:33:16 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 22 13:33:16 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 22 13:33:16 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 22 13:33:16 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 22 13:33:16 ubuntu NetworkManager[803]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 22 13:33:16 ubuntu NetworkManager[803]: <info> Activation (wlan0/wireless): connection 'HPC310a.CE48D8' requires no security.  No secrets needed.
Apr 22 13:33:16 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 22 13:33:16 ubuntu wpa_supplicant[1003]: Trying to associate with SSID 'HPC310a.CE48D8'
Apr 22 13:33:16 ubuntu kernel: [ 5812.021260] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Apr 22 13:33:16 ubuntu wpa_supplicant[1003]: Association request to the driver failed
Apr 22 13:33:16 ubuntu NetworkManager[803]: <info> (wlan0): supplicant interface state: disconnected -> associating
Apr 22 13:33:17 ubuntu wpa_supplicant[1003]: Associated with e6:f2:d8:6e:79:16
Apr 22 13:33:17 ubuntu wpa_supplicant[1003]: CTRL-EVENT-CONNECTED - Connection to e6:f2:d8:6e:79:16 completed (reauth) [id=0 id_str=]
Apr 22 13:33:17 ubuntu NetworkManager[803]: <info> (wlan0): supplicant interface state: associating -> completed
Apr 22 13:33:17 ubuntu NetworkManager[803]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HPC310a.CE48D8'.
Apr 22 13:33:17 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 22 13:33:17 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 22 13:33:17 ubuntu NetworkManager[803]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 22 13:33:17 ubuntu NetworkManager[803]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 22 13:33:17 ubuntu NetworkManager[803]: <info> Activation (wlan0) Beginning IP6 addrconf.
Apr 22 13:33:17 ubuntu avahi-daemon[801]: Withdrawing address record for fe80::224e:7fff:fef2:c00 on wlan0.
Apr 22 13:33:17 ubuntu avahi-daemon[801]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::224e:7fff:fef2:c00.
Apr 22 13:33:17 ubuntu avahi-daemon[801]: Interface wlan0.IPv6 no longer relevant for mDNS.
Apr 22 13:33:17 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 22 13:33:17 ubuntu NetworkManager[803]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 22 13:33:17 ubuntu dhclient: Listening on LPF/wlan0/20:4e:7f:f2:0c:00
Apr 22 13:33:17 ubuntu dhclient: Sending on   LPF/wlan0/20:4e:7f:f2:0c:00
Apr 22 13:33:17 ubuntu dhclient: Sending on   Socket/fallback
Apr 22 13:33:17 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Apr 22 13:33:19 ubuntu avahi-daemon[801]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::224e:7fff:fef2:c00.
Apr 22 13:33:19 ubuntu avahi-daemon[801]: New relevant interface wlan0.IPv6 for mDNS.
Apr 22 13:33:19 ubuntu avahi-daemon[801]: Registering new address record for fe80::224e:7fff:fef2:c00 on wlan0.*.
Apr 22 13:33:19 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Apr 22 13:33:24 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 22 13:33:28 ubuntu kernel: [ 5823.736011] wlan0: no IPv6 routers present
Apr 22 13:33:37 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Apr 22 13:33:37 ubuntu NetworkManager[803]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 22 13:33:37 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Apr 22 13:33:37 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Apr 22 13:33:37 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Apr 22 13:33:37 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Apr 22 13:33:37 ubuntu NetworkManager[803]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Apr 22 13:33:37 ubuntu NetworkManager[803]: <warn> Activation (wlan0) failed for access point (HPC310a.CE48D8)
Apr 22 13:33:37 ubuntu NetworkManager[803]: <warn> Activation (wlan0) failed.
Apr 22 13:33:37 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 22 13:33:37 ubuntu NetworkManager[803]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Apr 22 13:33:37 ubuntu NetworkManager[803]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 22 13:33:37 ubuntu NetworkManager[803]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 22 13:33:37 ubuntu NetworkManager[803]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2035
Apr 22 13:33:37 ubuntu wpa_supplicant[1003]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Apr 22 13:33:37 ubuntu NetworkManager[803]: <info> (wlan0): supplicant interface state: completed -> disconnected
```

ok this is what i got im sorry it took so long had to go on a pizza run lol

---

### Post by wildmanne39 on 2012-04-22
Hi, this is the network you want to connect to correct?> DEADMAN-PC_Network_1
This is the network it is connecting to> HPC310a.CE48D8which is setup wrong for your needs.

You need to make sure you connect to your network.
Thanks

---

### Post by Deadman390 on 2012-04-22
i dont know what just happened but i reset my modem and router for a PS3 problem and now it works lol but it is the deadman390 and now its working i havent tried rebooting yet though so

---

### Post by wildmanne39 on 2012-04-22
Hi, that is good I was going to get to that.
If it works after reboot please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by Deadman390 on 2012-04-22
Thank you so much it works now i have rebooted and it is now working as designed HOORAY i appreciate all your help and patience dont worry ill run into sumthing else within the next 30 mins that will req sum1 to help i will definitely keep the forums from stagnation untill i get it all down lol

---

### Post by wildmanne39 on 2012-04-22
Hi, your welcome! it can be a maze when first navigating linux.
Enjoy

---

