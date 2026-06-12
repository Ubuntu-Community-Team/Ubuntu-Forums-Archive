---
title: "Zero response to  I/O magic external USB DVD-ROM drive"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by urinophoria on 2008-11-28
Well, I've spent a couple hours now trying different searches and running through the absolute beginner section manually, so please be gentle if I actually missed this problem or the solution  :)

just installed eeebuntu standard 1.0 on my asus eee 701 a few days ago, so far it works brilliantly barring a few hiccups, and I've been having a blast solving it's few problems.  The one I had the most difficulty with was getting it to recognize with read/write privileges an 8g sdhc card.  Problem solved via another thread in these forums using the sudo gedit /etc/fstab command.  

My issue at this point, is that I downloaded the full desktop version of ubuntu to make a cd to install on my desktop and when I went to plug in my external dvd-rom drive nothing-at-all happened.  this drive is still fully functional plugged into a windows system, it's powered on and cycles when I plug it into a usb port on my eee system.  Just no response at all from the computer end.

Since it's a likely culprit, this is the end result of my fstab modifications I used to get the sdhc working.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ba60cfe0-22a6-44a5-85b9-a14daca250ac /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4b04a9b6-415e-45b7-ba40-264695afabff none            swap    sw              0       0
/dev/sdb /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/sd vfat user,noauto,exec 0 0
```

I have checked file manager and looked in the partition editor and there is no sign of the dvd-rom anywhere, zero response from the OS.

thanks so much for your help  :)

---

### Post by lemming465 on 2008-11-29
If you run*lsusb* in a terminal session is the DVD drive listed? If the answer is no, could we get the output of ```
sudo fdisk -l
lsmod
```

---

### Post by urinophoria on 2008-11-30
results from lsusb:

```
paul@minimorbus:~$ lsusb
Bus 005 Device 005: ID 067b:2506 Prolific Technology, Inc. 
Bus 005 Device 004: ID eb1a:2761 eMPIA Technology, Inc. 
Bus 005 Device 003: ID 0951:1606 Kingston Technology 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

Verified it is the **prolific technology inc** entry by unplugging the usb dvd rom drive and plugging it back in, so it does register under that command.

results from sudo fdisk -l   lsmod command just in case you still want it:


```
Disk /dev/sda: 4001 MB, 4001292288 bytes
255 heads, 63 sectors/track, 486 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x332b332a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         458     3678853+  83  Linux
/dev/sda2             459         486      224910    5  Extended
/dev/sda5             459         486      224878+  82  Linux swap / Solaris

Disk /dev/sdb: 8068 MB, 8068268032 bytes
255 heads, 63 sectors/track, 980 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b9c22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         980     7871818+   b  W95 FAT32
paul@minimorbus:~$ lsmod
Module                  Size  Used by
wlan_tkip              12416  2 
nls_iso8859_1           4096  1 
nls_cp437               5760  1 
vfat                   13440  1 
fat                    52892  1 vfat
af_packet              21764  4 
ipv6                  256580  8 
i915                   31232  2 
drm                    80660  3 i915
cpufreq_conservative     7200  0 
cpufreq_powersave       1792  0 
cpufreq_userspace       4248  0 
cpufreq_ondemand        8084  0 
cpufreq_stats           5124  0 
freq_table              4484  2 cpufreq_ondemand,cpufreq_stats
container               4736  0 
sbs                    14216  0 
sbshc                   6784  1 sbs
dock                   10124  0 
iptable_filter          2944  0 
ip_tables              12872  1 iptable_filter
x_tables               14724  1 ip_tables
eeepc_acpi              7568  0 
pciehp                 37784  0 
pci_hotplug            14216  1 pciehp
joydev                 11840  0 
wlan_scan_sta          14848  1 
ath_rate_sample        14976  1 
evdev                  11776  8 
uvcvideo               57352  0 
compat_ioctl32          1408  1 uvcvideo
videodev               28288  1 uvcvideo
v4l1_compat            14596  2 uvcvideo,videodev
v4l2_common            17408  2 uvcvideo,videodev
psmouse                39056  0 
serio_raw               6916  0 
battery                13316  0 
video                  18832  0 
output                  3712  1 video
ac                      6020  0 
snd_hda_intel         342680  1 
snd_pcm_oss            40608  0 
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                75272  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         10504  2 snd_hda_intel,snd_pcm
snd_hwdep               9476  1 snd_hda_intel
pcspkr                  3072  0 
iTCO_wdt               11808  0 
iTCO_vendor_support     3972  1 iTCO_wdt
ath_pci               230200  0 
wlan                  233840  5 wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               303968  3 ath_rate_sample,ath_pci
atl2                   31640  0 
snd_seq_dummy           3972  0 
button                  8336  0 
snd_seq_oss            33920  0 
snd_seq_midi            8352  0 
snd_rawmidi            24608  1 snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51024  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23556  2 snd_pcm,snd_seq
snd_seq_device          8588  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54564  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24596  1 
soundcore               7520  2 snd
agpgart                33328  3 drm,intel_agp
ext3                  133128  1 
jbd                    43284  1 ext3
mbcache                 8192  1 ext3
usb_storage            72256  1 
libusual               18208  1 usb_storage
sg                     36256  0 
sd_mod                 29584  5 
pata_acpi               7424  0 
ata_generic             7428  0 
ata_piix               18692  2 
ahci                   27268  0 
libata                159600  4 pata_acpi,ata_generic,ata_piix,ahci
scsi_mod              151180  4 usb_storage,sg,sd_mod,libata
ehci_hcd               36876  0 
uhci_hcd               25744  0 
usbcore               143980  6 uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                15772  0 
processor              27824  2 thermal
fan                     4740  0 
fuse                   48532  1 
paul@minimorbus:~$ 

```  thanks very much for your reply and your help  :)

---

### Post by lemming465 on 2008-11-30
Hmm.  The device is being seen on the USB bus, and the relevent USB driver modules are loaded, but the storage subsystem isn't seeing anything; we'd expect to see it in the fdisk output.

Is there anything about USB or SCSI errors at the end of /var/log/messages just after you plug in the drive?  Try e.g. *tail -40 /var/log/messages* in a terminal window.

How is the device powered?  I've seen suggestions elsewhere that this can be due to insufficient power.  E.g. the USB spec promises devices can draw 500 mA per port, but on battery a host system may only offer 100 mA.  Does it have an external powerpack?  If not, can you plug it into an external powered hub?  Does it make a difference whether or not the notebook is plugged in?

Once it starts showing up in the fdisk output, if you have any further trouble with the automounting stuff, there was a posting in an [old thread ]("http://ubuntuforums.org/showpost.php?p=3412958&postcount=14") about that.

---

### Post by arleslie on 2009-01-28
I'm having basicly the same problem. I'm pretty sure its the same drive he has. I'm trying to install Linux on my external harddrive and I can't boot from DVDs or CDs using my external DVD drive. The BIOS reads the drive is there, I went thought the Boot start up and selected the drive and I get "Booting from CD..." and thats it. I even waited 30 minutes for the drive to even idle and I still had "Booting from CD..." I have a Acer Aspire One.

---

