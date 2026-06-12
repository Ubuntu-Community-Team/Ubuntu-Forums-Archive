---
title: "Wireless in 7.10 but not in 8.04"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by thegame310 on 2008-06-18
I have an older laptop (1.13 ghz, 256mb ram) and XP was just getting to be to slow. So I decided to give xubuntu a try. 

When I installed 7.10 all I had to do was select my wireless network, put in my WEP, and I was set. 

Now with 8.10, it seems like it doesnt even detect that I have a wireless card in the laptop. 

The card is a Cisco Systems, Cisco AiroNet 350series Air-Pcm350. It's an old Wireless B card, any info you need, let me know and i'll get it. 

Thanks, for the help, and I cant wait to learn more :)

Eric

---

### Post by Hospadar on 2008-06-18
could you post the output of lspci and lsmod? (I assume it's a PC card wireless? if it's usb, do lsusb instead of lspci)

---

### Post by thegame310 on 2008-06-18
Yup it's a PC Wireless Card, i'll post the output of those commands in a second, it seems to have hung for a few mins here on a reboot.

---

### Post by thegame310 on 2008-06-18
eric@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
02:06.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller


eric@ubuntu:~$ lsmod
Module                  Size  Used by
ipv6                  267780  8 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_smi           6544  0 
speedstep_lib           6532  1 speedstep_smi
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
freq_table              5536  3 speedstep_smi,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
container               5632  0 
af_packet              23812  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
lp                     12324  0 
loop                   18948  0 
geode_aes               7196  1 
blkcipher               8324  1 geode_aes
aes_generic            27712  0 
airo_cs                 7168  2 
airo                   73884  1 airo_cs
joydev                 13120  0 
pcmcia                 40876  1 airo_cs
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_maestro3           26660  1 
snd_ac97_codec        101028  1 snd_maestro3
dcdbas                  9504  0 
evdev                  13056  6 
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
serio_raw               7940  0 
psmouse                40336  0 
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
yenta_socket           27276  4 
snd_seq_oss            35584  0 
rsrc_nonstatic         13696  1 yenta_socket
snd_seq_midi            9376  0 
pcmcia_core            40596  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  13 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
button                  9232  0 
i2c_core               24832  0 
battery                14212  0 
ac                      6916  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
intel_agp              25492  1 
agpgart                34760  1 intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_piix               19588  2 
floppy                 59588  0 
ata_generic             8324  0 
uhci_hcd               27024  0 
libata                159344  3 pata_acpi,ata_piix,ata_generic
ohci1394               33584  0 
usbcore               146028  2 uhci_hcd
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
3c59x                  46376  0 
mii                     6400  1 3c59x
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1

---

### Post by thegame310 on 2008-06-18
So... from just takin a gander at this, it seems like 8.04 does not recognize this old card. And this laptop has USB 1.1 not 2.0...not sure what my options will be besides hardwire.

---

### Post by thegame310 on 2008-06-18
bump

---

### Post by thegame310 on 2008-06-18
Solved, I went wired instead

---

### Post by rhlobo on 2008-06-19
There are some users experiencing some wireless problems when connecting thrue WAP after 06-17 ubuntu updates. The list of disponible networks works correctly but the connection process just hangs and wont connect.

If you think this is your problem, I will be checking [https://answers.launchpad.net/ubuntu/+question/36575](https://answers.launchpad.net/ubuntu/+question/36575) constantly.

Best regards

---

