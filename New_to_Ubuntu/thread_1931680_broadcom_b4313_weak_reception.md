---
title: "broadcom b4313 weak reception"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by DGINSD on 2012-02-26
I've noticed that my computer is only seeing 2 networks which is odd because I know there's about 20 visible in my area to my windows machines and even my old Ubuntu one.

Also the one I actually use it says is very weak even when sitting right next to the router while the other machines see it at full strength. If I leave the room; disconnect.

I didn't have to install any proprietary drivers to get wireless to work. I did install the STA driver recommended by jockey which completed and said it was installed, but no change, I also think it didn't install properly mainly because the output of "lshw -C network" shows the same driver, here's the output with jockey saying STA is activated.

```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 78:e3:b5:66:24:0e
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: e4:d5:3d:ba:99:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes** driver=brcmsmac** driverversion=3.0.0-16-generic firmware=N/A ip=192.168.0.104 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0300000-f0303fff

```

So what am I doing wrong, I even tried re-installing the STA with synaptic, same result?

---

### Post by wildmanne39 on 2012-02-26
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thanks

---

### Post by DGINSD on 2012-02-26
```
david@david-HP-Pavilion-g6-Notebook-PC:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux david-HP-Pavilion-g6-Notebook-PC 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:169b]
	Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1795]
	Kernel driver in use: brcmsmac

```

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SITH_LAIR"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:26:5A:CE:6B:A5   
          Bit Rate=58.5 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:37   Missed beacon:0

```

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
david@david-HP-Pavilion-g6-Notebook-PC:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
binfmt_misc            17540  1 
wl                   2568210  0 
lib80211               14991  1 wl
joydev                 17693  0 
bcma                   20219  0 
arc4                   12529  2 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_codec_idt      70553  1 
snd_seq_midi           13324  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_rawmidi            30547  1 snd_seq_midi
snd_hda_codec_hdmi     32040  1 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
video                  19412  0 
wmi                    19256  1 hp_wmi
fglrx                3127712  103 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
brcmsmac              631693  0 
brcmutil               17837  1 brcmsmac
mac80211              462046  1 brcmsmac
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              13301  0 
snd_timer              29991  2 snd_seq,snd_pcm
k10temp                13166  0 
snd                    68266  14 snd_hda_codec_idt,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
rts_pstor             445246  1 
psmouse                73882  0 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199630  2 brcmsmac,mac80211
crc_ccitt              12667  1 brcmsmac
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  52788  0 
ahci                   26002  3 
libahci                26861  1 ahci

```

Here it be.

---

### Post by bkratz on 2012-02-26
> **DGINSD said:**
> I've noticed that my computer is only seeing 2 networks which is odd because I know there's about 20 visible in my area to my windows machines and even my old Ubuntu one.

Also the one I actually use it says is very weak even when sitting right next to the router while the other machines see it at full strength. If I leave the room; disconnect.

I didn't have to install any proprietary drivers to get wireless to work. I did install the STA driver recommended by jockey which completed and said it was installed, but no change, I also think it didn't install properly mainly because the output of "lshw -C network" shows the same driver, here's the output with jockey saying STA is activated.

```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 78:e3:b5:66:24:0e
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: e4:d5:3d:ba:99:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes** driver=brcmsmac** driverversion=3.0.0-16-generic firmware=N/A ip=192.168.0.104 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0300000-f0303fff

```So what am I doing wrong, I even tried re-installing the STA with synaptic, same result?


There are conflicts between brcmsmac and the STA driver.  I don't know whether sta will work any better ( but it will work).  You will need to blacklist two files to allow it to get control. If it doesn't work any better we can always go back. In the terminal:

```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

```

Reboot and the sta driver should take control and show up as the driver in the listing above rather than brcmsmac.

---

### Post by DGINSD on 2012-02-26
Worked like a charm, I'm five feet from my router and I got full bars, and can also see about 10 networks now. Thank you very much.

I was also getting some drop outs but time will tell on those.

If ya got a second can you explain those commands for me?

---

### Post by bkratz on 2012-02-26
> **DGINSD said:**
> Worked like a charm, I'm five feet from my router and I got full bars, and can also see about 10 networks now. Thank you very much.

I was also getting some drop outs but time will tell on those.

If ya got a second can you explain those commands for me?

Congratulations!

Sure, those two commands added two files to the blacklist ( modules not loaded at boot time).  Those two files are part of Ubuntu (while the STA driver itself is provided by Broadcom). Both tried to gain control of the device and the wrong one won! Well not really wrong, just another one. By blacklisting we prevented the other modules from loading during booting.  Sure glad it helped, I just bought a laptop that uses the same card and will need that myself!  Anyway, be sure to return to the thread tools and mark it as solved (if this was enough explanation!).

---

### Post by DGINSD on 2012-02-26
Excellent, thank you very much. I had just not seen the "tee" command before and was curious what it does?

---

### Post by wildmanne39 on 2012-02-26
Hi, I am glad you got it sorted, would you please use thread tools and mark the thread solved.
Thanks

---

### Post by bkratz on 2012-02-26
> **DGINSD said:**
> Excellent, thank you very much. I had just not seen the "tee" command before and was curious what it does?


The best explanation is found in the terminal itself.  Just type in 

man tee

for an explanation.

---

