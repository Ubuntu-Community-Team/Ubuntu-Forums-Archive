---
title: "A confused Noob!!"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by chiefwiggum on 2008-04-27
Hi All, i hope you can help me.

i've just installed Ubuntu. having had XP already on the PC i decided to run the live CD 1st, had a quick play and was pleased with what i saw so went ahead and installed it over XP.
now having completed the install i have no sound!! 
But i did when using the live CD.

I've selected my sound csrd from the list (C-media) still nothing, i've tried re booting and its kept my settings but still no sound!!

Please help!! :confused:

---

### Post by nephish on 2008-04-27
two things could help us out a lot here.

open a terminal and in that terminal enter
lspci  and hit enter

then type
lsmod  and hit enter. 

use the copy and paste ( from the termina edit menu ) and paste it here.
It will give us a lot of info for what may be happening.

---

### Post by riven0 on 2008-04-27
This is going to sound stupid, but right click on the sound icon on the top bar and make sure all the settings are at max, (Master, PCM, etc). If it still doesn't work, try restarting Alsa: **sudo /etc/init.d/alsa-utils restart**

---

### Post by chiefwiggum on 2008-04-27
WOW, what quick replies, cheers guys.
I thought i'd try Raven0's suggestion 1st as it seemed easiest, all volumes on max, and tried restarting ASLA, no sound, but the speakers did pop.

so as requested Nephish:

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
00:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0b.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 03)
00:0b.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 03)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
@:~$ lsmod
Module                  Size  Used by
af_packet              23812  2 
ipv6                  267780  12 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
cpufreq_conservative     8712  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
tuner                  42912  0 
tea5767                 6788  1 tuner
tda8290                12420  1 tuner
tuner_simple           10248  1 tuner
mt20xx                 13192  1 tuner
tea5761                 6020  1 tuner
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
gspca                 643920  0 
ipaq                   34712  0 
evdev                  13056  5 
usbserial              35816  1 ipaq
sn9c102               127236  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
snd_cmipci             38528  3 
snd_opl3_lib           12928  1 snd_cmipci
snd_hwdep              10500  1 snd_opl3_lib
pcspkr                  4224  0 
snd_via82xx            29464  4 
gameport               16008  2 snd_cmipci,snd_via82xx
snd_seq_dummy           4868  0 
snd_ac97_codec        101028  1 snd_via82xx
ac97_bus                3072  1 snd_ac97_codec
snd_mpu401_uart         9728  2 snd_cmipci,snd_via82xx
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
cx88_alsa              14216  1 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
nvidia               4718832  32 
snd_pcm                78596  6 snd_cmipci,snd_via82xx,snd_ac97_codec,cx88_alsa,snd_pcm_oss
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_viapro              9876  0 
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
cx8800                 35848  0 
cx88xx                 66088  2 cx88_alsa,cx8800
snd_timer              24836  3 snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ir_common              36100  1 cx88xx
i2c_algo_bit            7300  1 cx88xx
snd                    56996  31 snd_cmipci,snd_opl3_lib,snd_hwdep,snd_via82xx,snd_seq_dummy,snd_ac97_codec,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
tveeprom               16656  1 cx88xx
p54pci                 13440  0 
p54common              13824  1 p54pci
i2c_core               24832  11 tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,nvidia,i2c_viapro,cx88xx,i2c_algo_bit,tveeprom
videodev               29440  4 gspca,sn9c102,cx8800,cx88xx
v4l1_compat            15492  1 videodev
compat_ioctl32          2304  2 sn9c102,cx8800
v4l2_common            18304  5 tuner,sn9c102,cx8800,cx88xx,videodev
videobuf_dma_sg        14980  3 cx88_alsa,cx8800,cx88xx
videobuf_core          18820  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc               5896  3 cx88_alsa,cx8800,cx88xx
mac80211              165652  2 p54pci,p54common
soundcore               8800  1 snd
cfg80211               15112  1 mac80211
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
via_agp                11136  1 
agpgart                34760  2 nvidia,via_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
floppy                 59588  0 
via_rhine              26632  0 
mii                     6400  1 via_rhine
ehci_hcd               37900  0 
uhci_hcd               27024  0 
sata_via               12420  0 
pata_via               13316  2 
pata_acpi               8320  0 
usbcore               146028  8 gspca,ipaq,usbserial,sn9c102,usbhid,ehci_hcd,uhci_hcd
libata                159344  4 ata_generic,sata_via,pata_via,pata_acpi
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

Hope this all means something to you!! :lolflag:

---

### Post by mmb1 on 2008-04-27
Try typing "alsamixer" in a terminal, and posting the output.

---

### Post by chiefwiggum on 2008-04-27
> **mmb1 said:**
> Try typing "alsamixer" in a terminal, and posting the output.

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.15 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: VIA 8237                                                               &#9474;
&#9474; Chip: ICEnsemble VT1616i                                                     &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-9.00, -9.00]                                          &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9484;&#9472;&#9472;&#9488;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;OO&#9474;                        &#9474;MM&#9474;     &#9474;OO&#9474;     &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;   81<>81     81      71<>71      0        0               81<>81    0<>0     &#9474;
&#9474; < Master >Master M  Headphon 3D Contr 3D Contr  3D Contr   PCM    Surround   &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

That seems to show the card as Via 8237, i guess thats the onboard card, which i dont want to use

---

### Post by nephish on 2008-04-27
well, what it means is that linux found your card when it booted up and that the kernel loaded the modules for said card. Both are good news.

What program are you running that needs to play sound ?

pleas try a couple of different apps that use sound and let us know what happened

---

### Post by mmb1 on 2008-04-27
Thanks, now go into the "sound" panel of your preferences and see if the "device" tab displays your sound card.

---

### Post by chiefwiggum on 2008-04-27
> **nephish said:**
> well, what it means is that linux found your card when it booted up and that the kernel loaded the modules for said card. Both are good news.

What program are you running that needs to play sound ?

pleas try a couple of different apps that use sound and let us know what happened

I've tried playing videos on youtube (through firefox) and streaming radio through rhythmbox, could see the video playing, and could see that that the radio was streaming, just couldn't hear anything!!

---

### Post by nephish on 2008-04-27
ok, look in the preferences -> sound and look at the lists where you can select your sound device, let us know if the card you want is listed.

---

### Post by chiefwiggum on 2008-04-27
> **mmb1 said:**
> Thanks, now go into the "sound" panel of your preferences and see if the "device" tab displays your sound card.

I think so! :oops:

---

### Post by riven0 on 2008-04-27
> **chiefwiggum said:**
> &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.15 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: VIA 8237                                                               &#9474;
&#9474; Chip: ICEnsemble VT1616i                                                     &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-9.00, -9.00]                                          &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9484;&#9472;&#9472;&#9488;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;OO&#9474;                        &#9474;MM&#9474;     &#9474;OO&#9474;     &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;   81<>81     81      71<>71      0        0               81<>81    0<>0     &#9474;
&#9474; < Master >Master M  Headphon 3D Contr 3D Contr  3D Contr   PCM    Surround   &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

That seems to show the card as Via 8237, i guess thats the onboard card, which i dont want to use

If it's the onboard card, is it possible it's enabled through the BIOS? I would check the BIOS first and disable it. That should get your other card working.

---

### Post by mmb1 on 2008-04-27
+1 for riven0's advice.

---

### Post by chiefwiggum on 2008-04-27
I've just tried plugging the speakers in to the on board and now i can hear the speakers crackle which i was getting before on full volume!

Time to climb back under the desk and swap it back around!

Ok, will, log out and have a butchers in the Bios

---

### Post by chiefwiggum on 2008-04-27
Sorted! \\:D/

Cheers Guys, must have been as Riven0 suggested as the on board was enabled through the Bios. =D>

must admit, amazed how quickly it shut down! XP would have taken about a day!! :twisted:

---

### Post by findelmundo on 2008-12-08
Hi. I just solved my sound problem on my PackardBell EasyNote (Ubuntu8.10). I downloaded and installed "GNOME ALSA Mixer", opened it from the program menu, and turned off all the "mute" options... Voilaa!!! hehe.. I'm happy):P

---

