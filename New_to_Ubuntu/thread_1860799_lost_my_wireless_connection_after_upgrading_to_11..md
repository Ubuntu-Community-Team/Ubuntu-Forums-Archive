---
title: "lost my wireless connection after upgrading to 11.10"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by shevin on 2011-10-15
Hi , I just upgraded to 11.10 and my wireless stopped working , the problem is I saw no wireless at all in the menu , just wired and VPN .


I should explain that **in 11.04 I had a problem with my Wifi (it used to disconnect every 2 minutes) then I had fixed it by adding the following line :**

```
options iwlagn 11n_disable=1 11n_disable50=1
```

to my "/etc/modprobe.d/options.conf"

then I tried to delete that line in my modeprobe options, and the wireless button is back in 11.10 , but it again disconnects from internet every minute .

I do press the wifi-key on my Toshiba Sattelite laptop but it won't respond , [it wont turn the wifi-light on on my laptop]


if u want to know the result of lspci, here it is  :```

Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)

```

---

### Post by shevin on 2011-10-15
Help Me please !

---

### Post by wildmanne39 on 2011-10-15
Hi, please post the results of these commands here:
```
sudo lshw -C network
```
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
lsmod | grep iwl
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan0 | tail -n25
```

Also add this line please:
> options iwlagn 11n_disable=1
Thank you

---

### Post by mattubu16 on 2011-10-16
Hi!
I had the same problem as you (resulting from the same fix you have). If you haven't had it fixed yet, the solution (found [here]("http://ubuntuforums.org/showthread.php?p=11303276#post11303276")), is to change
```
options iwlagn 11n_disable=1 11n_disable50=1
```
to
```
options iwlagn 11n_disable=1
```

So far it's been working for me by even deleting that line, but I haven't tried it on my work network where it was problematic before.

Good luck!

For reference, I have an intel 5100 agn card.

---

### Post by mattubu16 on 2011-10-16
Don't forget to reboot after editing that file.

Also for newcomers, if the options.conf file doesn't exist, you can create it and simply enter that single line. You'll need administrator privileges to do that, so open a terminal (ctrl-alt-T) and type
```
sudo gedit /etc/modprobe.d/options.conf
```
Enter your password, paste in the line, save, close, and reboot.

---

### Post by wildmanne39 on 2011-10-16
Hi, I need to state that this option will only work for certain drivers like 
> iwlagn
Thank you

---

### Post by shevin on 2011-10-16
> **mattubu16 said:**
> Hi!
I had the same problem as you (resulting from the same fix you have). If you haven't had it fixed yet, the solution (found [here]("http://ubuntuforums.org/showthread.php?p=11303276#post11303276")), is to change
```
options iwlagn 11n_disable=1 11n_disable50=1
```
to
```
options iwlagn 11n_disable=1
```

So far it's been working for me by even deleting that line, but I haven't tried it on my work network where it was problematic before.

Good luck!

For reference, I have an intel 5100 agn card.


Thanks to you and wildmanne39 , it works great now :)

yaaay

---

### Post by mattubu16 on 2011-10-16
You're welcome! Thanks for following up!

---

### Post by sadaruwan12 on 2011-10-16
If your problem is solved please mark the thread as solved.

---

### Post by iFreeBudget on 2011-10-17
I am having exactly same problem, and solutions shown here have not worked. Any help?

I have a Asus laptop model no: U56E-BBL5 with 6gb RAM, Intel core i5

Wireless/wifi stopped working. Outputs from various commands suggested in other threads are pasted here

```
me@me-ubuntu:~$ rfkill list
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wimax: WiMAX
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```
me@me-ubuntu:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```

```
 me@me-ubuntu:~$ dmesg | grep -i firm
[    0.811564] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   15.539802] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   15.667238] elantech: assuming hardware version 3, firmware version 69.15.1
```

```
 me@me-ubuntu:~$ lspci | grep -i network
02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
```

```
 me@me-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric
```

```
 me@me-ubuntu:~$ sudo lshw -C network
[sudo] password for me: 
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:34:fe:d4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn  driverversion=3.0.0-12-generic firmware=41.28.5.1 build 33926 latency=0  link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:50 memory:de800000-de801fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 14:da:e9:2a:1e:bc
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c  driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.2  latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:53 memory:dd400000-dd43ffff ioport:a000(size=128)

```

I also see a lot of ```
iwlagn <ap> fail to flush all tx fifo queues
``` in dmesg

So, wireless is completely not working now and I have to sit near  by shoe closet on the floor to get a wired connection to post this.:sad:

---

### Post by wildmanne39 on 2011-10-17
Hi, please post the results of:
```
lsmod | grep wmi
```
Thank you

---

### Post by TonyLudwick on 2011-10-19
I have the same problem and model as IFreeBudget.  Please Help, Thanks in advance!  Please see my info below:

guestuser@Tux-U56E:~$ lsmod | grep wmi
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_nb_wmi            12517  0 
asus_wmi               20035  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
wmi                    19256  1 asus_wmi

-------------------------------------------------------------------------------------

rfkill list all 
guestuser@Tux-U56E:~$ rfkill list all 
0: asus-wlan: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
1: asus-wimax: WiMAX 
    Soft blocked: yes 
    Hard blocked: no 
2: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
-------------------------------------------------------------------- 
dmesg | grep iwl 
guestuser@Tux-U56E:~$ dmesg | grep iwl 
[   11.923999] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree: 
[   11.924002] iwlagn: Copyright(c) 2003-2011 Intel Corporation 
[   11.924052] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   11.924062] iwlagn 0000:02:00.0: setting latency timer to 64 
[   11.924096] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84 
[   11.934939] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6 
[   11.934943] iwlagn 0000:02:00.0: Device SKU: 0X9 
[   11.934945] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3 
[   11.958993] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels 
[   11.959089] iwlagn 0000:02:00.0: irq 50 for MSI/MSI-X 
[   12.162553] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926 
[   12.175453] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs' 
[   28.556069] iwlagn 0000:02:00.0: fail to flush all tx fifo queues 
[  343.862836] iwlagn 0000:02:00.0: fail to flush all tx fifo queues 
[  343.863085] Modules linked in: bnep rfcomm bluetooth parport_pc ppdev binfmt_misc snd_hda_codec_hdmi snd_hda_codec_realtek arc4 joydev asus_nb_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event usbhid uvcvideo videodev hid snd_seq v4l2_compat_ioctl32 snd_timer snd_seq_device wmi psmouse serio_raw snd iwlagn mac80211 i915 drm_kms_helper drm cfg80211 i2c_algo_bit mei(C) video soundcore snd_page_alloc lp parport ahci libahci atl1c xhci_hcd 
[  346.634717] iwlagn 0000:02:00.0: fail to flush all tx fifo queues 
 
-------------------------------------------------------------------- 
 
lspci -nn 
guestuser@Tux-U56E:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09) 
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) 
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04) 
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05) 
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05) 
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5) 
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5) 
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5) 
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5) 
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05) 
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05) 
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05) 
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05) 
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67) 
03:00.0 USB Controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042] 
04:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0) 
---------------------------------------------------------------- 
 
 
lsmod | grep asus 
guestuser@Tux-U56E:~$ lsmod | grep asus 
asus_nb_wmi            12517  0  
asus_wmi               20035  1 asus_nb_wmi 
sparse_keymap          13890  1 asus_wmi 
wmi                    19256  1 asus_wmi 
--------------------------------------------------------------- 
 
lsmod | grep wl 
guestuser@Tux-U56E:~$ lsmod | grep wl 
iwlagn                314213  0  
mac80211              310872  1 iwlagn 
cfg80211              199587  2 iwlagn,mac80211 
-------------------------------------------------------------- 
 
sudo lshw -C network 
guestuser@Tux-U56E:~$ sudo lshw -C network 
  *-network                
       description: Wireless interface 
       product: Centrino Wireless-N + WiMAX 6150 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wlan0 
       version: 67 
       serial: 40:25:c2:61:e1:7c 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:50 memory:de800000-de801fff 
  *-network 
       description: Ethernet interface 
       product: AR8151 v2.0 Gigabit Ethernet 
       vendor: Atheros Communications 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: c0 
       serial: 14:da:e9:bd:cb:72 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:53 memory:dd400000-dd43ffff ioport:a000(size=128) 
------------------------------------------------------------------- 
 
iwconfig 
guestuser@Tux-U56E:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bgn  ESSID:"HawkNet"   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=15 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
------------------------------------------------------------------ 
 
sudo iwlist scan (Note: HawkNet is my network.) 
guestuser@Tux-U56E:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wlan0     Scan completed : 
          Cell 01 - Address: 00:1A:70:46:D2:F3 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=28/70  Signal level=-82 dBm   
                    Encryption key:on 
                    ESSID:"molrox1" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000000c5d1fae18b 
                    Extra: Last beacon: 468ms ago 
                    IE: Unknown: 00076D6F6C726F7831 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030106 
                    IE: Unknown: 050400010000 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: DD06001018020004 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
          Cell 02 - Address: 00:24:01:CC:57:2E 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=27/70  Signal level=-83 dBm   
                    Encryption key:off 
                    ESSID:"HawkNet" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=0000005acd6a9180 
                    Extra: Last beacon: 188ms ago 
                    IE: Unknown: 00074861776B4E6574 
                    IE: Unknown: 010882848B968C129824 
                    IE: Unknown: 030101 
                    IE: Unknown: 050400010000 
                    IE: Unknown: 0706555320010B1B 
                    IE: Unknown: 200100 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 3204B048606C 
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: DD1A00904C3401051B00000000000000000000000000000000000000 
                    IE: Unknown: 3D1601051B00000000000000000000000000000000000000 
                    IE: Unknown: DD0900037F01010000FF7F 
                    IE: Unknown: DD270050F204104A000110104400010210470010565AA94967C14C0EAA8FF349E6F59311103C000101 
----------------------------------------------------------------- 
 
iwlist chan 
guestuser@Tux-U56E:~$ iwlist chan 
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
-------------------------------------------------------------------- 
 
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan0 | tail -n25 
guestuser@Tux-U56E:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan0 | tail -n25 
Oct 18 11:52:52 Tux-U56E avahi-autoipd(wlan0)[2857]: SIOCSIFFLAGS failed: Permission denied 
Oct 18 11:52:52 Tux-U56E avahi-autoipd(wlan0)[2857]: Callout STOP, address 169.254.9.189 on interface wlan0 
Oct 18 11:52:52 Tux-U56E kernel: [ 1290.229374] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
Oct 18 11:52:52 Tux-U56E kernel: [ 1290.230463] wlan0: direct probe to 00:24:01:cc:57:2e (try 1/3) 
Oct 18 11:52:52 Tux-U56E avahi-autoipd(wlan0)[2858]: client: RTNETLINK answers: No such process 
Oct 18 11:52:52 Tux-U56E kernel: [ 1290.430219] wlan0: direct probe to 00:24:01:cc:57:2e (try 2/3) 
Oct 18 11:52:52 Tux-U56E dhclient: Listening on LPF/wlan0/40:25:c2:61:e1:7c 
Oct 18 11:52:52 Tux-U56E dhclient: Sending on   LPF/wlan0/40:25:c2:61:e1:7c 
Oct 18 11:52:52 Tux-U56E kernel: [ 1290.752207] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
Oct 18 11:52:52 Tux-U56E kernel: [ 1290.753298] wlan0: direct probe to 00:24:01:cc:57:2e (try 1/3) 
Oct 18 11:52:53 Tux-U56E kernel: [ 1290.949457] wlan0: direct probe to 00:24:01:cc:57:2e (try 2/3) 
Oct 18 11:52:53 Tux-U56E kernel: [ 1291.149153] wlan0: direct probe to 00:24:01:cc:57:2e (try 3/3) 
Oct 18 11:52:53 Tux-U56E kernel: [ 1291.348840] wlan0: direct probe to 00:24:01:cc:57:2e timed out 
Oct 18 11:52:53 Tux-U56E dhclient: Listening on LPF/wlan0/40:25:c2:61:e1:7c 
Oct 18 11:52:53 Tux-U56E dhclient: Sending on   LPF/wlan0/40:25:c2:61:e1:7c 
Oct 18 11:52:55 Tux-U56E kernel: [ 1293.349860] iwlagn 0000:02:00.0: fail to flush all tx fifo queues 
Oct 18 11:52:55 Tux-U56E kernel: [ 1293.349972] wlan0: deauthenticating from 00:24:01:cc:57:2e by local choice (reason=3) 
Oct 18 11:52:55 Tux-U56E kernel: [ 1293.350095] Modules linked in: bnep rfcomm bluetooth parport_pc ppdev binfmt_misc snd_hda_codec_hdmi snd_hda_codec_realtek arc4 joydev asus_nb_wmi asus_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event usbhid uvcvideo videodev hid snd_seq v4l2_compat_ioctl32 snd_timer snd_seq_device wmi psmouse serio_raw snd iwlagn mac80211 i915 drm_kms_helper drm cfg80211 i2c_algo_bit mei(C) video soundcore snd_page_alloc lp parport ahci libahci atl1c xhci_hcd 
Oct 18 11:52:55 Tux-U56E kernel: [ 1293.447978] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
Oct 18 11:52:55 Tux-U56E dhclient: Listening on LPF/wlan0/40:25:c2:61:e1:7c 
Oct 18 11:52:55 Tux-U56E dhclient: Sending on   LPF/wlan0/40:25:c2:61:e1:7c 
Oct 18 11:52:55 Tux-U56E dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 
Oct 18 11:52:57 Tux-U56E dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 
Oct 18 11:53:04 Tux-U56E dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
Oct 18 11:53:17 Tux-U56E dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16

---

### Post by wildmanne39 on 2011-10-20
Hi, the issue is a bug and I only no one way to get it to work, but I asked a friend to take a look with a lot more experience then I have in networking so we will see if he has another solution if not we will go with my only method to get it to work.
Thank you

---

### Post by TonyLudwick on 2011-10-20
Thank You very much for your assistance.  I hope some one comes up with a fix or an acceptable work-around really quick.  I think 11.10 is awesome, and it would be a rotten shame if people with laptops immediately gave up on it because they can't get their wireless to work.  I mean, what good is a laptop without wireless?

---

### Post by wildmanne39 on 2011-10-20
Hi, I have not heard from my friend but I have been doing some research and I found a few things we can try if you want too.

The other method that I know is to downgrade the kernel it is not that hard and you would still be using 11.10 but I would prefer to find a fix for the kernel that comes with 11.10.
Thank you

---

### Post by chili555 on 2011-10-20
This may be a long process, so everyone please put on their 'patience' hats.

This suggests it's a firmware issue, although the solution is not reached: [https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=724052](https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=724052)

Your card uses the 6050 firmware:> *-network               
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation> [ 12.162553] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926 [http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads)  As you can see, it specifies what is loading, iwlwifi-6050-ucode-41.28.5.1. My fully updated 11.10 system has two versions of 6050 ucode:iwlwifi-6050-[COLOR="Red"]4[/COLOR].ucode and iwlwifi-6050-[COLOR="Red"]5[/COLOR].ucode. Let's try to load the earlier version:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Add one line:```
alias iwlagn ucode_alternative=/lib/firmware/iwlwifi-6050-4.ucode
```Proofread carefully, save and close gedit. Reboot and let us have your report. ```
dmesg | grep iwl
```

---

### Post by TonyLudwick on 2011-10-21
/etc/modprobe.d/iwlagn.conf
Did not exist, so I created it with the line as you instructed.  Rebooted.  No Change.  See command output you requested below:


guestuser@Tux-U56E:~$ dmesg | grep iwl
[   11.997185] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   11.997188] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   11.997243] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.997253] iwlagn 0000:02:00.0: setting latency timer to 64
[   11.997287] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[   12.007527] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
[   12.007531] iwlagn 0000:02:00.0: Device SKU: 0X9
[   12.007533] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   12.007580] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.007675] iwlagn 0000:02:00.0: irq 50 for MSI/MSI-X
[   12.181382] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   12.184234] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.482662] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   28.923599] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   31.555677] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   38.900711] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   41.548777] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   48.961774] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   51.617821] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[   70.461768] iwlagn 0000:02:00.0: fail to flush all tx fifo queues
[  100.417200] iwlagn 0000:02:00.0: fail to flush all tx fifo queues

---

### Post by wildmanne39 on 2011-10-25
Hi, here is a link to the method that is working.
[http://ubuntuforums.org/showthread.php?t=1862484&page=5](http://ubuntuforums.org/showthread.php?t=1862484&page=5)

Read post 42.
Thank you

---

### Post by UncleJack0 on 2011-12-30
> **mattubu16 said:**
> Hi!
I had the same problem as you (resulting from the same fix you have). If you haven't had it fixed yet, the solution (found [here]("http://ubuntuforums.org/showthread.php?p=11303276#post11303276")), is to change
```
options iwlagn 11n_disable=1 11n_disable50=1
```
to
```
options iwlagn 11n_disable=1
```

So far it's been working for me by even deleting that line, but I haven't tried it on my work network where it was problematic before.

Good luck!

For reference, I have an intel 5100 agn card.

Hey, just willing to tell everybody that I had this same problem after doing a massive 265 MB sudo apt-get upgrade recently. The solution in the quote fixed the problem dearly, thank you.

My computer is an Asus K40IJ with an Atheros wireless card.

Oh yes, and my options.conf doesn't have anything in it, so I added the latter line in the quotation.

---

### Post by mattubu16 on 2011-12-30
> **UncleJack0 said:**
> Hey, just willing to tell everybody that I had this same problem after doing a massive 265 MB sudo apt-get upgrade recently. The solution in the quote fixed the problem dearly, thank you.

My computer is an Asus K40IJ with an Atheros wireless card.

Oh yes, and my options.conf doesn't have anything in it, so I added the latter line in the quotation.

 Great! I'm glad it worked for you!

---

