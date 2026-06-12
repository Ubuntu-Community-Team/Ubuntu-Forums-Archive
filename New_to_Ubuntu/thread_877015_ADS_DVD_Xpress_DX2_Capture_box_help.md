---
title: "ADS DVD Xpress DX2 Capture box help"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Majora26 on 2008-08-01
Hi, I've compiled the drivers for the dvd xpress dx2 card from the instructions here: [http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Installation](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Installation)

When I try to run a test with gorecord, I get the following.

```
blazn@blazn-desktop:~$ gorecord -input 0 -duration 20 test-video.avi
Unable to read /sys/bus/usb/drivers/go7007: No such file or directory
Is the go7007-usb kernel module loaded?

```

the website says to try using go7007_firmware_load, but doing that yeilds
```

blazn@blazn-desktop:~$ sudo go7007_firmware_load
ERROR: Device not found on usb bus.
```

Here's the output of lsmod:

```
Module                  Size  Used by
af_packet              23812  2 
nfnetlink_queue        13120  1 
nfnetlink               5784  2 nfnetlink_queue
binfmt_misc            12808  1 
nf_conntrack_ipv4      19080  3 
xt_tcpudp               4096  3 
vboxdrv                76736  0 
xt_state                3328  3 
tun                    12672  0 
nf_conntrack           66752  2 nf_conntrack_ipv4,xt_state
xt_NFQUEUE              2816  3 
ppdev                  10372  0 
ipv6                  267780  18 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
dock                   11280  0 
cpufreq_conservative     8712  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
container               5632  0 
battery                14212  0 
iptable_filter          3840  1 
ip_tables              14820  1 iptable_filter
x_tables               16132  4 xt_tcpudp,xt_state,xt_NFQUEUE,ip_tables
nls_iso8859_1           4992  2 
nls_cp437               6656  2 
vfat                   14464  2 
fat                    54556  1 vfat
ac                      6916  0 
joydev                 13120  0 
rt73                  216320  1 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
snd_hda_intel         344728  3 
dcdbas                  9504  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
psmouse                40336  0 
serio_raw               7940  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
sr_mod                 17956  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
cdrom                  37408  1 sr_mod
pcspkr                  4224  0 
ata_generic             8324  0 
evdev                  13056  3 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_seq_dummy           4868  0 
ndiswrapper           192920  0 
fglrx                1721908  21 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                  9232  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              25492  0 
soundcore               8800  1 snd
agpgart                34760  2 fglrx,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
usb_storage            73664  1 
libusual               19108  1 usb_storage
ext3                  136712  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  8 
ata_piix               19588  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
ehci_hcd               37900  0 
pata_acpi               8320  0 
ahci                   28420  5 
libata                159344  4 ata_generic,ata_piix,pata_acpi,ahci
scsi_mod              151436  5 sr_mod,usb_storage,sg,sd_mod,libata
e100                   37388  0 
mii                     6400  1 e100
uhci_hcd               27024  0 
usbcore               146028  8 rt73,ndiswrapper,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 

```



The device shows up in lsusb. I'm not really sure what to do next. Can anyone help?

Thanks

---

### Post by tnsurfer on 2008-11-30
> **Majora26 said:**
> 
The device shows up in lsusb. I'm not really sure what to do next. Can anyone help?

Thanks


Have you got any results that allow you to use the ADS DVD Xpress DX2 since posting this? I found your post hard to understand as to exactly what to do when trying to get Ubuntu to allow me to use my DX2 Capture box.
On my own, I did get it to show up as a device and took 3 jpg's of what the system log saw but all was still Greek to me, a non tech. The jpgs are 164kb, 159kb and 118kb in size if you want to download.
Hoping we can do a break thru into the world of Ubuntu. 
I really need to transfer my old VHS to DVD, don't you?

Mike
TN

---

