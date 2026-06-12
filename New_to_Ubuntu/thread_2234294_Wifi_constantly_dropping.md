---
title: "Wifi constantly dropping"
date: 2014-07-13
forum: New to Ubuntu
---

### Post by beanbaag on 2014-07-13
Hi all, dell latitude 5400 running 13.10. wifi signal is very unstable, some days its very bad others maybe 5 or 10 disconnects. Decided to do a fresh reinstall and the exact same problem started happening and on top of that the laptop has started turning off randomly. It seems the fan runs flat out nearly all the time where as before never ran fast for extended periods. When the wifi drops i get a small warning, the laptop freeze for a split second, when it turns off altogether it freezes for 5 seconds and goes.
This might be helpful
```
jack@jack-Latitude-E5400:~$ ifconfigeth0      Link encap:Ethernet  HWaddr 00:23:ae:43:13:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1166991 (1.1 MB)  TX bytes:1166991 (1.1 MB)


wlan0     Link encap:Ethernet  HWaddr 00:22:fb:af:f5:74  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:fbff:feaf:f574/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:592412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:367461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:761556718 (761.5 MB)  TX bytes:35808940 (35.8 MB)


jack@jack-Latitude-E5400:~$ iwconfig
wlan0     IEEE 802.11abgn  ESSID:"eircom31431119"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: FC:F5:28:25:E1:F0   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.


jack@jack-Latitude-E5400:~$ lsmod
Module                  Size  Used by
zram                   18070  2 
vesafb                 13500  0 
snd_hda_codec_hdmi     40402  1 
snd_hda_codec_idt      44710  1 
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  0 
joydev                 17097  0 
kvm                   368967  0 
gpio_ich               13229  0 
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
dell_laptop            17161  0 
dcdbas                 14383  1 dell_laptop
bnep                   18959  2 
bluetooth             323512  10 bnep,rfcomm
snd_hda_intel          42658  4 
snd_hda_codec         164003  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
arc4                   12536  2 
snd_pcm                89488  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
pcmcia                 51368  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
iwldvm                219872  0 
mac80211              517482  1 iwldvm
microcode              18894  0 
i915                  594547  3 
psmouse                91078  0 
iwlwifi               147801  1 iwldvm
binfmt_misc            13140  1 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13189  0 
drm_kms_helper         46867  1 i915
yenta_socket           40193  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  18 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
pcmcia_rsrc            18319  1 yenta_socket
lpc_ich                16864  0 
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
drm                   242400  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
cfg80211              401762  3 iwlwifi,mac80211,iwldvm
soundcore              12600  1 snd
video                  18777  1 i915
wmi                    18590  1 dell_wmi
mac_hid                13037  0 
coretemp               13195  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
sdhci_pci              18456  0 
firewire_ohci          35463  0 
sdhci                  37644  1 sdhci_pci
firewire_core          57689  1 firewire_ohci
ahci                   25579  2 
crc_itu_t              12627  1 firewire_core
libahci                26619  1 ahci
tg3                   152066  0 
ptp                    18156  1 tg3
pps_core               18546  1 ptp
jack@jack-Latitude-E5400:~$ ^C
jack@jack-Latitude-E5400:~$ demsg | grep wlan1
No command 'demsg' found, did you mean:
 Command 'dmesg' from package 'util-linux' (main)
demsg: command not found
jack@jack-Latitude-E5400:~$ dmesg | grep wlan1
jack@jack-Latitude-E5400:~$ dmesg|grep wlan1
jack@jack-Latitude-E5400:~$ sudo lshw -C network
[sudo] password for jack: 
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:af:f5:74
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-24-generic firmware=8.83.5.1 build 33692 ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:44 memory:f69fe000-f69fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5761e Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:23:ae:43:13:20
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 firmware=5761e-v3.60 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:f68e0000-f68effff memory:f68f0000-f68fffff



```

---

### Post by beanbaag on 2014-07-16
anyone? at my wits end.

---

### Post by jeremy31 on 2014-07-16
Try 14.04 as 13.10 is no longer supported

---

