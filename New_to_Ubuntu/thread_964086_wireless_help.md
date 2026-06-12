---
title: "wireless help"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by dsmcginn on 2008-10-30
im trying to get my wireless working with ubuntu...here's what i'm working with.

 sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:16:be:ac
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.10 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0


any suggestions?

---

### Post by jbrown96 on 2008-10-30
A few things to try: check to see if it is found as a wireless device ```
iwconfig
```, see if the interface is up ```
ifconfig
``` (use ```
sudo ifconfig INTERFACE up
``` where INTERFACE is what was found from iwconfig), and if the module is loaded - post ```
lsmod
```

---

### Post by cairnzi on 2008-10-30
i don't wish to sound condescending but have you tried system\network? or click on network icon and see if it picks up your router?

---

### Post by dsmcginn on 2008-10-30
cairnzi-yes i've tried that. lol.

and when i used the iwconfig it said no wireless extensions

and the ifconfig gave me this:
doug@doug:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:16:be:ac  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe16:beac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4123232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2763354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:915132220 (872.7 MB)  TX bytes:235034995 (224.1 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89400 (87.3 KB)  TX bytes:89400 (87.3 KB)

---

### Post by jbrown96 on 2008-10-30
I don't have experience with lshw -C network. Could you post the output of ```
lspci | grep Network
``` and ```
lsmod
```

---

### Post by dsmcginn on 2008-10-30
lspci | grep Network didn't show anything, so here's lspci and lsmod.

doug@doug:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
doug@doug:~$ lsmod
Module                  Size  Used by
isofs                  36388  0 
udf                    88612  0 
af_packet              23812  2 
ipv6                  267780  10 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
loop                   18948  0 
joydev                 13120  0 
pcmcia                 40876  0 
snd_hda_intel         344856  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                40336  0 
sky2                   47620  0 
serio_raw               7940  0 
snd_timer              24836  2 snd_pcm,snd_seq
ndiswrapper           192920  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
acer_acpi              18112  0 
led_class               6020  1 acer_acpi
container               5632  0 
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_7xx1               8576  0 
video                  19856  0 
output                  4736  1 video
tifm_core              11012  1 tifm_7xx1
intel_agp              25492  1 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
button                  9232  0 
battery                14212  0 
ac                      6916  0 
soundcore               8800  1 snd
wmi_acer                9644  1 acer_acpi
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
agpgart                34760  3 drm,intel_agp
evdev                  13056  7 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
ata_piix               19588  2 
libata                159344  3 ata_generic,pata_acpi,ata_piix
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
doug@doug:~$

---

### Post by dsmcginn on 2008-10-30
here's what happened when i did the first one:

doug@doug:~$ lspci | grep Network
doug@doug:~$

---

### Post by jbrown96 on 2008-10-30
For some reason Atheros chipsets show up as Ethernet Controllers instead of Network Controllers. That's why it didn't return anything; grep returns lines that have a matching word. 
I think I figured out the problem. Try going to System-->Admin-->Hardware Drivers. See if there is an option in there. If not, try installing the restricted modules with ```
sudo apt-get install linux-restricted-modules
``` I believe that you will need to restart since this is changing the kernel. Afterwards it should work. If not try ifconfig, iwconfig, and grep lsmod for mad and ath
```
iwconfig
``` ```
ifconfig
``` ```
lsmod | grep mad
``` ```
lsmod | grep ath
```

---

