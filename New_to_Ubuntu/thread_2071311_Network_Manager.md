---
title: "Network Manager"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by Inisfad on 2012-10-15
Hi all.  I have a wireless wifi modem, and when I fire up Ubuntu, network manager automatically sees the wifi and connects.  Sometimes, however, I forget to put the modem on before I start up my computer.  If my computer is already on when the modem is activated, network manager will not connect, and the drop down menu only shows 'enable wireless', 'edit connections', etc.  I usually re-start my computer (a PIA) and network manager automatically connects.  So my question: Is there any way (command, etc) to get network manager to search for my wifi, if the modem has been activated after start up??  Other than re-starting the computer??  Thanks!!

---

### Post by NikTh on 2012-10-15
Hi  , 

probably the problem here is that when you have your modem closed , then the Linux Kernel not finding any modules to load. So you  must load the module manually from terminal. 

A workaround to your problem could be to add that module in to /etc/modules file , so the Kernel will loads the module at every startup either your modem is off or on. 

What you can do to find what module loaded ? 

Switch ON your modem and boot into Ubuntu. Then open a terminal (Ctrl+Alt+T keys combo) and paste this command inside ```
sudo lshw -C network
``` 
You can find the appropriate interface (Wireless) and see what driver= is loaded. 
Alternately you can paste this command ```
lspci -nnk | grep -iA2 net
``` and take a look at "Network Controller" --> Kernel driver in use: 

Giving this command ```
lsmod
``` 
probably you will see the module listed there. 
Then you can force the module to be loaded in every boot with this command 
```
echo "module-name" | sudo tee -a /etc/modules
``` 

Thanks

---

### Post by Inisfad on 2012-10-15
Hmmm, not quite sure I understand - I know the driver, etc., for the wireless modem.  If the modem is on when I boot, network manager sees it right away and connects.  No problem there.  If the modem is off when I boot, network manager (of course) sees nothing.  I then have to turn off the computer, turn on the modem and re-boot.  I would like to find a way to boot up the computer, and, if I have forgotten to turn on the modem, turn on the modem after the computer has booted, and get network manager to locate the modem so I can make the wifi connection.  I was hoping there was some command that would force network manager to look for (and connect - or give the option to connect) the modem after the computer is running.

---

### Post by NikTh on 2012-10-15
Hi , 
we can take it step by step if you want and we will see. 

Switch ON the modem and boot to Ubuntu. Then open a terminal (Ctrl+Alt+T keys combo) and give the results of these 3 commands : 
```
sudo lshw -C network
``````
lspci -nnk | grep -iA2 net
``````
lsmod
```Be aware that the second command will ask for your password. Write it carefully and normally . It will not appear anything (like you don't write anything). 
Put the results between the brackets [noparse]```
Here
```[/noparse] so can be readable.

Thanks

---

### Post by Inisfad on 2012-10-15
OK:
sudo lshw -C network
```
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:c3:ae:35
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:21 memory:c0300000-c0301fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:08:9d:06
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-32-generic firmware=410.2160 ip=192.168.0.100 link=yes multicast=yes wireless=IEEE 802.11bg
```lspci -nnk | grep -iA2 net

```
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01f5]
    Kernel driver in use: b44
```lsmod
```
Module                  Size  Used by
rfcomm                 38139  1 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  6 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
binfmt_misc            17292  1 
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  7 
xt_tcpudp              12531  18 
dm_crypt               22528  0 
xt_addrtype            12596  4 
xt_state               12514  13 
ip6table_filter        12711  1 
snd_hda_codec_idt      60251  1 
ip6_tables             18432  2 ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
nf_nat_ftp             12595  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
nf_nat                 24959  1 nf_nat_ftp
arc4                   12473  2 
snd_seq_midi           13132  0 
nf_conntrack_ipv4      19084  9 nf_nat
snd_rawmidi            25424  1 snd_seq_midi
joydev                 17393  0 
snd_seq_midi_event     14475  1 snd_seq_midi
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
b43                   342643  0 
iptable_filter         12706  1 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              18106  1 iptable_filter
x_tables               21974  12 xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
dell_laptop            17767  0 
mac80211              436455  1 b43
dcdbas                 14098  1 dell_laptop
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
dm_multipath           22710  0 
soundcore              14635  1 snd
psmouse                96684  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
shpchp                 32325  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
k8temp                 12905  0 
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
serio_raw              13027  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
radeon                733789  3 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
b44                    31412  0 
pata_atiixp            12999  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197599  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
ssb                    50691  2 b43,b44
ati_agp                13242  0 
zram                   18193  1 
```

---

### Post by NikTh on 2012-10-15
OK , 
now open a terminal and give this command 

```
echo "b43" | sudo tee -a /etc/modules
``` 

Then switch OFF your modem , boot into Ubuntu and Switch ON your modem and see if works. 

Thanks

---

### Post by Inisfad on 2012-10-15
Sadly, no.  When I rebooted with the modem off, and then turned the modem on, network manager did not see the wifi - just did nothing.  Currently, my 'workaround' has been to go into 'edit connections' and  click 'save', as though I am changing my specs (but actually do nothing but click save), and then, sometimes (not always) network manager will look for the wifi connection.  When I boot up without the modem on, network manager does not list previous connections that I can click on to activate them.  This would be what I am looking for.....

---

### Post by Inisfad on 2012-10-15
I have continued to search through the forum, and found this: [http://ubuntuforums.org/showthread.php?t=1656890](http://ubuntuforums.org/showthread.php?t=1656890)  Will try the command that is in that post.  Hopefully this will work for me.  Thanks for your help!!

---

### Post by NikTh on 2012-10-15
> **Inisfad said:**
> I have continued to search through the forum, and found this: [http://ubuntuforums.org/showthread.php?t=1656890](http://ubuntuforums.org/showthread.php?t=1656890)  Will try the command that is in that post.  Hopefully this will work for me.  Thanks for your help!!

OK , good catch. If you manage to solve your problem do not forget to mark the thread as solved. 

You can also try this command 

```
sudo service network-manager restart
``` 

Or you can try to edit your connection with admin privileges 
```
gksudo nm-connection-editor
``` edit your connection and make sure that "available to all users" and "connect automatically" are marked (checked). 

Thanks

---

