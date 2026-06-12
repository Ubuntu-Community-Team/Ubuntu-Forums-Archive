---
title: "How to get headphones only ??"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Drakkor on 2008-07-26
Yeah, how can I shut out my speakers and get headphone sound only ? Guess I got the OSS mixer. :confused:

---

### Post by Drakkor on 2008-07-27
no one has any idea ??:(

---

### Post by eightmillion on 2008-07-27
This can be a real pain. I had the same problem with Gutsy. My upgrade to Hardy fixed the issue. Could you run the command
> lspci -v
and post the output of the Audio section?

---

### Post by ajmorris on 2008-07-27
> **Drakkor said:**
> Yeah, how can I shut out my speakers and get headphone sound only ? Guess I got the OSS mixer. :confused:

Hi there,
what sound card do you have? (post the output of sudo lspci if you dont know) and what driver are you using for your card?
Also, have you tried running sudo alsaconf to reconfigure alsa to use the correct driver? (if you are using ALSA)

AJ

---

### Post by Drakkor on 2008-07-27
OK, here's the output of ```
lspci -v 
``` 

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
	Subsystem: Acer Incorporated [ALI] Unknown device 0137
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at fea78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

---

### Post by Drakkor on 2008-07-27
*bumpitybumpbump*

---

### Post by ajmorris on 2008-07-28
> **Drakkor said:**
> OK, here's the output of ```
lspci -v 
``` 
 
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
    Subsystem: Acer Incorporated [ALI] Unknown device 0137
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    Memory at fea78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
 
ok, you will want snd-hda-intel for that sound card. Run sudo alsaconf and select it as the driver. Then test your headphones again. If that doesnt work, can you post the output of sudo lsmod. I would like to see which driver is in use.
 
AJ

---

### Post by Drakkor on 2008-07-28
OK, here we go !
Edit: A note here, I have a tvtuner card,and a SBLive soundcard,and onboard sound. I tried deactivating the onboard sound,in the bios,but it still didn't work

drakkor@drakkor-desktop:~$ sudo alsaconf
sudo: alsaconf: command not found
drakkor@drakkor-desktop:~$ sudo lsmod
Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
vboxdrv                60720  0 
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
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
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
snd_emu10k1_synth       8064  0 
snd_emux_synth         36224  1 snd_emu10k1_synth
snd_seq_virmidi         8192  1 snd_emux_synth
snd_seq_midi_emul       7552  1 snd_emux_synth
snd_bt87x              16868  1 
bt878                  11832  0 
tuner                  42912  0 
tea5767                 6788  1 tuner
tda8290                12420  1 tuner
tuner_simple           10248  1 tuner
mt20xx                 13192  1 tuner
tea5761                 6020  1 tuner
tvaudio                24476  0 
snd_emu10k1           146880  3 snd_emu10k1_synth
msp3400                32160  0 
snd_ac97_codec        101028  1 snd_emu10k1
snd_hda_intel         344728  3 
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
bttv                  175860  1 bt878
ir_common              36100  1 bttv
snd_pcm                78596  5 snd_bt87x,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_pcm_oss
compat_ioctl32          2304  1 bttv
i2c_algo_bit            7300  1 bttv
snd_seq_dummy           4868  0 
videobuf_dma_sg        14980  1 bttv
videobuf_core          18820  2 bttv,videobuf_dma_sg
usblp                  15872  0 
psmouse                40336  0 
snd_seq_oss            35584  0 
snd_page_alloc         11400  4 snd_bt87x,snd_emu10k1,snd_hda_intel,snd_pcm
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
btcx_risc               5896  1 bttv
tveeprom               16656  1 bttv
videodev               29440  1 bttv
v4l2_common            18304  5 tuner,tvaudio,msp3400,bttv,videodev
serio_raw               7940  0 
wmi_acer                9644  0 
emu10k1_gp              4608  0 
gameport               16008  2 emu10k1_gp
v4l1_compat            15492  2 bttv,videodev
snd_seq_midi            9376  0 
snd_hwdep              10500  3 snd_emux_synth,snd_emu10k1,snd_hda_intel
snd_rawmidi            25760  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
nvidia               7825536  34 
snd_seq_midi_event      8320  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                54224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9612  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                34760  1 nvidia
snd                    56996  28 snd_emux_synth,snd_seq_virmidi,snd_bt87x,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_core               24832  12 tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,tvaudio,msp3400,bttv,i2c_algo_bit,tveeprom,nvidia
soundcore               8800  1 snd
evdev                  13056  4 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_amd               14212  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
usb_storage            73664  0 
libusual               19108  1 usb_storage
ata_generic             8324  0 
ohci1394               33584  0 
ahci                   28420  2 
pata_acpi               8320  0 
ieee1394               93752  2 sbp2,ohci1394
ohci_hcd               25348  0 
libata                159344  4 pata_amd,ata_generic,ahci,pata_acpi
ehci_hcd               37900  0 
scsi_mod              151436  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
forcedeth              51980  0 
usbcore               146028  7 usblp,usbhid,usb_storage,libusual,ohci_hcd,ehci_hcd
thermal                16796  0 
processor              36872  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
drakkor@drakkor-desktop:~$

---

### Post by ajmorris on 2008-07-28
to run alsaconf you will need to install the alsa-utils package from the repos.

---

