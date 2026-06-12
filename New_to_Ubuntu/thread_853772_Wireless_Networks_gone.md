---
title: "Wireless Networks gone"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by alexjohnc3 on 2008-07-08
In Hardy Heron, for some reason the option to use Wireless Networks is missing some of the time. It comes back randomly sometimes when I restart the computer, but most of the time it doesn't, even after restarting several times. I have no idea why it does this, but when the text in nm-applet that says "Wireless Networks" isn't a light gray, I can connect to my wireless router without a problem. There doesn't seem to be any reason why this is happening.

---

### Post by alexjohnc3 on 2008-07-09
*Bump*

---

### Post by bobnutfield on 2008-07-09
I have experienced this in the past.  Do you have any other wireless appliances in the same room or near your router (i.e. TV tansmitters, cordless phones)?  Wireless cards work in 2.4Ghz range and so do many other appliances.  Interference of this type will cause the problems you are describing.

Bob

---

### Post by alexjohnc3 on 2008-07-12
> **bobnutfield said:**
> I have experienced this in the past.  Do you have any other wireless appliances in the same room or near your router (i.e. TV tansmitters, cordless phones)?  Wireless cards work in 2.4Ghz range and so do many other appliances.  Interference of this type will cause the problems you are describing.

Bob

Nope, and I only started to have this problem once I upgraded to 8.04. This didn't happen even once in 7.10. :(

---

### Post by alexjohnc3 on 2008-07-23
Bump...

---

### Post by alexjohnc3 on 2008-08-01
Again... a bump.

---

### Post by alexjohnc3 on 2008-08-03
Can anyone help?

---

### Post by bwainscott on 2008-08-03
hey man can you post your lspci and lsmod so we can see how your loaded?  I feel like this might be a module problem.

---

### Post by Living2007 on 2008-08-03
> **alexjohnc3 said:**
> Nope, and I only started to have this problem once I upgraded to 8.04. This didn't happen even once in 7.10. :(
It may just be the wind blowing it off course. One time, one of our laptops picked up the schools wireless network over 150m away! How's That!

---

### Post by alexjohnc3 on 2008-08-04
> **bwainscott said:**
> hey man can you post your lspci and lsmod so we can see how your loaded?  I feel like this might be a module problem.
Lspci:
> 00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

Lsmod:
> Module                  Size  Used by
xt_limit                3584  8 
xt_tcpudp               4096  7 
ipt_LOG                 7296  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5632  1 
nf_conntrack_irc        7576  0 
nf_conntrack_ftp       10144  0 
xt_state                3328  6 
iptable_nat             8324  0 
nf_nat                 20396  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19080  8 iptable_nat
nf_conntrack           66752  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
ieee80211_crypt_wep     6272  1 
af_packet              23812  4 
ipv6                  267780  12 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  1 
ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ac                      6916  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
zd1211rw               56964  0 
ieee80211softmac       30976  1 zd1211rw
ieee80211              35528  2 zd1211rw,ieee80211softmac
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
usblp                  15872  0 
snd_hda_intel         344728  6 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7825536  24 
snd                    56996  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
i2c_nforce2             7680  0 
agpgart                34760  1 nvidia
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
k8temp                  6656  0 
dcdbas                  9504  0 
evdev                  13056  4 
soundcore               8800  1 snd
i2c_core               24832  2 nvidia,i2c_nforce2
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
usbhid                 31872  0 
hid                    38784  1 usbhid
sata_nv                27528  2 
pata_acpi               8320  0 
ata_generic             8324  0 
pata_amd               14212  0 
forcedeth              51980  0 
libata                159344  4 sata_nv,pata_acpi,ata_generic,pata_amd
ohci_hcd               25348  0 
ehci_hcd               37900  0 
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
usbcore               146028  6 zd1211rw,usblp,usbhid,ohci_hcd,ehci_hcd
thermal                16796  0 
processor              36872  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 


---

### Post by alexjohnc3 on 2008-08-12
Does anyone know if they could help? :\

---

### Post by alexjohnc3 on 2008-09-06
Bump...

---

