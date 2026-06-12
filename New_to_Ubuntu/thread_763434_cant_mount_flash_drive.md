---
title: "cant mount flash drive"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by gnomes11 on 2008-04-23
i can not mount any flash drives and i couldnt figer out how to fix the bug with gconftool please help

---

### Post by opscure on 2008-04-23
What do you get when you type:
```

mkdir /media/usb
sudo mount /dev/sda1 /media/usb

```

---

### Post by gnomes11 on 2008-04-23
i made /media/usb and used the oher comand and got this 'mount: /dev/sda1 already mounted or /media/usb busy
mount: according to mtab, /dev/sda1 is already mounted on /media/usb'

and my flash drive still says it cant mount

---

### Post by opscure on 2008-04-23
Alright, well there is a couple things we can do to try and figure out why this is happening.  First, we can try unmounting and remounting the device (where is your device sda?, sdb?, is your hard drive sda? mounted on /?)
Here's for sdb usb drive.
```
sudo umount /media/usb
sudo mount /dev/sdb1 /media/usb
```
This will simply try and unmount and remount the drive.  This will likely not work since for some reason or another your system seems to think your drive is already mounted.  

If it doesn't then let's see what's going on in your mtab file with
```
cat /etc/mtab
```
Please post what you get from this.

Also, you could enter:
```
lsof | grep usb
```
and post the output to help see what might be locking up the mounting process.

Other commands that would yield output that would be helpful in figuring out what's going on:
```

lsusb
lsmod
ps aux |grep usb

```

---

### Post by Tatty on 2008-04-23
Can you plug in your usb stick then post the output of ```
sudo fdisk -l
``` (thats a lowercase L) 

and ```
lsusb
```

---

### Post by gnomes11 on 2008-04-23
i got this from the comands tatty gave me

jables@jables-laptop:~$ sudo fdisk -l

Disk /dev/sda: 4001 MB, 4001292288 bytes
255 heads, 63 sectors/track, 486 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bf43bf3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         418     3357553+  83  Linux
/dev/sda2             419         486      546210    5  Extended
/dev/sda5             419         486      546178+  82  Linux swap / Solaris

Disk /dev/sdb: 4075 MB, 4075290624 bytes
7 heads, 6 sectors/track, 189513 cylinders
Units = cylinders of 42 * 512 = 21504 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             196      189514     3975680    b  W95 FAT32

Disk /dev/sdc: 4059 MB, 4059561984 bytes
229 heads, 32 sectors/track, 1081 cylinders
Units = cylinders of 7328 * 512 = 3751936 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1082     3964399+   c  W95 FAT32 (LBA)
jables@jables-laptop:~$ lsusb
Bus 005 Device 004: ID 054c:0243 Sony Corp. 
Bus 005 Device 002: ID 0951:1606 Kingston Technology 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by gnomes11 on 2008-04-23
this is what i got from opscures comands

jables@jables-laptop:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sdb1 /media/usb vfat rw 0 0
jables@jables-laptop:~$ lsof | grep usb
usb-stora 2181       root  cwd   unknown                           /proc/2181/cwd (readlink: Permission denied)
usb-stora 2181       root  rtd   unknown                           /proc/2181/root (readlink: Permission denied)
usb-stora 2181       root  txt   unknown                           /proc/2181/exe (readlink: Permission denied)
usb-stora 2181       root NOFD                                     /proc/2181/fd (opendir: Permission denied)
usb-stora 5702       root  cwd   unknown                           /proc/5702/cwd (readlink: Permission denied)
usb-stora 5702       root  rtd   unknown                           /proc/5702/root (readlink: Permission denied)
usb-stora 5702       root  txt   unknown                           /proc/5702/exe (readlink: Permission denied)
usb-stora 5702       root NOFD                                     /proc/5702/fd (opendir: Permission denied)
jables@jables-laptop:~$ lsusb
Bus 005 Device 004: ID 054c:0243 Sony Corp. 
Bus 005 Device 002: ID 0951:1606 Kingston Technology 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
jables@jables-laptop:~$ lsmod
Module                  Size  Used by
isofs                  36412  0 
udf                    87204  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
af_packet              24840  4 
ipv6                  273892  8 
i915                   25856  1 
drm                    83348  2 i915
ppdev                  10244  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
asus_acpi               9760  0 
button                  8976  0 
video                  18060  0 
sbs                    19592  0 
container               5504  0 
dock                   10656  0 
ac                      6148  0 
battery                11012  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
wlan_scan_sta          14976  1 
ath_rate_sample        15232  1 
snd_hda_intel         263712  2 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
ath_pci               114600  0 
wlan                  211120  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               280544  3 ath_rate_sample,ath_pci
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
serio_raw               8068  0 
psmouse                39952  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
atl2                   33304  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              25620  1 
snd                    54660  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
agpgart                35016  3 drm,intel_agp
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usb_storage            73024  1 
sg                     36764  0 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
sd_mod                 30336  5 
ata_generic             8452  0 
ata_piix               17540  2 
ahci                   23300  0 
libata                125168  3 ata_generic,ata_piix,ahci
scsi_mod              147084  4 usb_storage,sg,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
jables@jables-laptop:~$ ps aux |grep usb
root      1999  0.0  0.0      0     0 ?        S<   13:48   0:00 [ksuspend_usbd]
root      2181  0.0  0.0      0     0 ?        S<   13:48   0:00 [usb-storage]
root      5702  0.0  0.0      0     0 ?        S<   15:00   0:00 [usb-storage]
jables    5925  0.0  0.1   2980   768 pts/1    R+   15:09   0:00 grep usb

---

### Post by Tatty on 2008-04-23
> **gnomes11 said:**
> i got this from the comands tatty gave me

jables@jables-laptop:~$ sudo fdisk -l

Disk /dev/sda: 4001 MB, 4001292288 bytes
255 heads, 63 sectors/track, 486 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bf43bf3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         418     3357553+  83  Linux
/dev/sda2             419         486      546210    5  Extended
/dev/sda5             419         486      546178+  82  Linux swap / Solaris

Disk /dev/sdb: 4075 MB, 4075290624 bytes
7 heads, 6 sectors/track, 189513 cylinders
Units = cylinders of 42 * 512 = 21504 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             196      189514     3975680    b  W95 FAT32

Disk /dev/sdc: 4059 MB, 4059561984 bytes
229 heads, 32 sectors/track, 1081 cylinders
Units = cylinders of 7328 * 512 = 3751936 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1082     3964399+   c  W95 FAT32 (LBA)



Im seeing three separate drives here,  The first I assume is your primary hard disk because that is where the linux partitions are, although this disk appears to be only 4Gb big - is this correct?

 The other two drives are both FAT32 partitions,and again both appear to be 4gb. One of these will be your flash drive.  I am assuming it is sdc.

Try this:

```
sudo mkdir /media/usbdrive
sudo mount /dev/sdc1 /media/usdrive
```

Then if you navigate to /media/usbdrive, that should be your usb stick.

---

### Post by gnomes11 on 2008-04-23
yes i have a asus eee pc 4G surf so i have a 4G built in a 4G sd card that works  and the 4G flash drive 

i used 'sudo mkdir /media/usbdrive' made the file and then used 'sudo mount /dev/sdc1 /media/usdrive' and it says 'mount: mount point /media/usdrive does not exist' then i tryed mkdir /media/usbdrive again and it says the file exists

---

### Post by Tatty on 2008-04-23
> **gnomes11 said:**
> yes i have a asus eee pc 4G surf so i have a 4G built in a 4G sd card that works  and the 4G flash drive 

i used 'sudo mkdir /media/usbdrive' made the file and then used 'sudo mount /dev/sdc1 /media/usdrive' and it says 'mount: mount point /media/usdrive does not exist' then i tryed mkdir /media/usbdrive again and it says the file exists

Apologies, there is a typo in what i wrote (lol i do that too often, mental note to check what i write more carefully ;))
try this:

```
sudo mkdir /media/usbdrive
sudo mount /dev/sdc1 /media/usbdrive
```

If your usb stick is sdc (which i assume it is) then it will mount it to /mount/usbdrive.  
Really the stick should be automounting, im not sure why it isnt. But if this works then we can eliminate a hardware problem, and you can use it as a temporary workaround until someone can figure out a more permanent solution.

---

### Post by gnomes11 on 2008-04-23
that works it mounted and let me use it thanks alot

---

### Post by Tatty on 2008-04-23
> **gnomes11 said:**
> that works it mounted and let me use it thanks alot

No Problem :)

As i say, it should be automounting really, I just found this thread which sounds similar to the problem you are having: [http://ubuntuforums.org/showthread.php?t=582045](http://ubuntuforums.org/showthread.php?t=582045)

to run gconf-editor just type sudo gconf-editor in a terminal.

Or of course if you plan on updating to hardy tomorrow you could just wait to see if that fixes it.

---

### Post by gnomes11 on 2008-04-23
im ot getting hardy untill the torrent for the eeeXubutu version is up

---

