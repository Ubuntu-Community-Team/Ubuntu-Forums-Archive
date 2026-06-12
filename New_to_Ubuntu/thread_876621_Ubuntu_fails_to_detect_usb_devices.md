---
title: "Ubuntu fails to detect usb devices"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by chris66 on 2008-07-31
I am totally new to linux and ubuntu and have just installed ubuntu 8.04 with a dual boot setup on my Toshiba A200 Satellite laptop. Problem is, ubuntu fails to detect any of my usb devices when I plug them in. I have 3 different memory sticks and an external HDD, none of which work but all of which work fine in Vista. When I plug any of them into any of the 4 usb ports not only do they not automount but they do not appear in the places>computer window. lsusb always returns

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

The only device which will work (sort of) is my usb wireless mouse which will work if plugged in at boot up. If I then unplug it and plug it back in, it does not work and is not recognised by lsusb. It seems to do this in all the usb ports. lsusb with mouse plugged in at boot up:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

If I boot up my mate's notebook (Dell inspiron) using the same Live disk that I used to install, all my devices automount perfectly. Using the live disk on my machine gives me my original problem. So I guess it is not the devices or a corrupted disk.

I have searched the forums and tried lots of commands that have solved similar problems without any luck.  I'll post the output of fdisk -l with 2 1gb usb flash drives plugged in below (I don't understand it but maybe it will be useful)
  
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x109a5f45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        3299    24961914+   7  HPFS/NTFS
/dev/sda3            9112        9729     4957184   17  Hidden HPFS/NTFS
/dev/sda4            3300        9111    46684890    5  Extended
/dev/sda5            3300        8868    44732961   83  Linux
/dev/sda6            8869        9111     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order


Has anybody had a similar problem or have any useful suggestions about what to try next? Remember I an Absolute Beginner so please keep it simple!

---

### Post by NewDisciple on 2008-08-01
See this link: [http://ubuntuforums.org/showthread.php?t=874729&highlight=%2Fdev%2Fsdb+won%27t+show]("http://ubuntuforums.org/showthread.php?t=874729&highlight=%2Fdev%2Fsdb+won%27t+show")

---

### Post by Cypher on 2008-08-01
Please provide the output of
```

lsmod
cat /proc/interrupts
dmesg

```
The output of the final command AFTER you plug in the USB devices are especially helpful.

---

### Post by chris66 on 2008-08-01
Thanks for the replies.

Cypher: here are the outputs from

lsmod

Module                  Size  Used by
af_packet              23812  4 
ipv6                  267780  10 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
joydev                 13120  0 
pcmcia                 40876  0 
snd_hda_intel         344728  3 
iwl3945                89844  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
iwlwifi_mac80211      219108  1 iwl3945
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
cfg80211               15112  1 iwlwifi_mac80211
sky2                   47492  0 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
sdhci                  19076  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tifm_7xx1               8576  0 
video                  19856  0 
output                  4736  1 video
serio_raw               7940  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mmc_core               51460  1 sdhci
tifm_core              11012  1 tifm_7xx1
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                40336  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      6916  0 
battery                14212  0 
button                  9232  0 
intel_agp              25492  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
pcspkr                  4224  0 
agpgart                34760  3 drm,intel_agp
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
evdev                  13056  7 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ata_piix               19588  2 
ata_generic             8324  0 
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
ohci1394               33584  0 
scsi_mod              151436  5 sbp2,sg,sd_mod,sr_mod,libata
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 


cat /proc/interrupts

           CPU0       CPU1       
  0:     103955          0   IO-APIC-edge      timer
  1:        303          0   IO-APIC-edge      i8042
  8:         36          0   IO-APIC-edge      rtc
  9:      10147          0   IO-APIC-fasteoi   acpi
 12:      48417          0   IO-APIC-edge      i8042
 14:      19069          0   IO-APIC-edge      libata
 15:      11109          0   IO-APIC-edge      libata
 16:          4          0   IO-APIC-fasteoi   ohci1394
 17:      53911          0   IO-APIC-fasteoi   uhci_hcd:usb4, i915@pci:0000:00:02.0
 18:         10          0   IO-APIC-fasteoi   uhci_hcd:usb3, yenta, tifm_7xx1, sdhci:slot0
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb1
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 21:        782          0   IO-APIC-fasteoi   HDA Intel
219:      22322          0   PCI-MSI-edge      iwl3945
220:          1          0   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:      14269      59774   Local timer interrupts
RES:      62333      76525   Rescheduling interrupts
CAL:         68        238   function call interrupts
TLB:        120        502   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0


last few lines of dmesg (after plugging a device into all usb slots)

[   84.808874] CPU0 attaching sched-domain:
[   84.808884]  domain 0: span 03
[   84.808888]   groups: 01 02
[   84.808898] CPU1 attaching sched-domain:
[   84.808903]  domain 0: span 03
[   84.808908]   groups: 02 01
[   89.294006] NET: Registered protocol family 17
[   91.130893] wlan0: Initial auth_alg=1
[   91.130900] wlan0: authenticate with AP 00:13:33:06:f3:70
[   91.133336] wlan0: RX authentication from 00:13:33:06:f3:70 (alg=1 transaction=2 status=0)
[   91.133341] wlan0: replying to auth challenge
[   91.134953] wlan0: RX authentication from 00:13:33:06:f3:70 (alg=1 transaction=4 status=0)
[   91.134963] wlan0: authenticated
[   91.134968] wlan0: associate with AP 00:13:33:06:f3:70
[   91.136498] wlan0: RX AssocResp from 00:13:33:06:f3:70 (capab=0x411 status=0 aid=1)
[   91.136507] wlan0: associated
[   91.138554] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  106.562589] wlan0: no IPv6 routers present
chris@Archimedes:~$ 



The dmesg log thing doesn't seem to recognise the devices at all. The lights in the usb sticks all flicker on when plugged in then stay off. The usb HDD powers up but no indication from the computer that it is plugged in.


NewDisciple: thanks for the link, I have checked it out but don't really understand it. I plugged in a flash drive and tried the commands

sudo mkdir /media/disk
sudo mount /dev/sdb1 /media/disk

and got

mount: special device /dev/sdb1 does not exist


I much appreciate any advice you guys can give. It is weird that everything works fine on another computer using the Live disk but not this one. I wondered about reinstalling ubuntu, would that help?

---

### Post by NewDisciple on 2008-08-01
I didn't notice it earlier, but I see that you have boot installed on the second partition rather than the first one.  I'm kinda wondering if thats why your computer can't see usb devices.  I'll check around and see if I can find anything about that.

---

### Post by unutbu on 2008-08-01
Power down. Plug in a USB device. Then power up.
Open a terminal and type

```
lspci -nn
dmesg | bzip2 -c > dmesg.out.bz2
```

Then post the output of lspci, and dmesg.out.bz2 as an attachment.

---

### Post by NewDisciple on 2008-08-01
In that command > sudo mkdir /media/disk
sudo mount /dev/sdb1 /media/disk you would only use the name "sdb1" if that is the actual name of the drive.  For example, my harddrive is /dev/sda.  My external hd is /dev/sdb.  My second external is /dev/sdc and my usb (flash drive) is /dev/sdd.  Since yours didn't open with the lsusb or fdisk -l commands I would mount it on a different machine to find the name using a partion editor.

---

### Post by chris66 on 2008-08-03
unutbu: output of lnpci -nn below, dmesg.out.bz2 attached. That's with the wireless mouse plugged in (and working), and a usb flash drive and ext HDD plugged in (and not working).

:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
07:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
07:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
07:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
07:06.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]


NewDisciple: I don't know about the partition that boot is installed on. When I installed ubuntu I just used the menus on the Live disk and let it do its thing. 

I tried one of the flash drives, on a different machine it is called "sdc1". I tried plugging it in and mounting it but got the response: "mount: special device /dev/sdc1 does not exist". 

Thanks for the replies. Your help is much appreciated, as a newb I am totally in the dark.

---

### Post by unutbu on 2008-08-03
If you run 
```
dmesg | grep ehci
```
I think you will find:
```
[   72.715905] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   72.715931] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   72.720166] ehci_hcd 0000:00:1d.7: can't setup
[   72.720170] ehci_hcd 0000:00:1d.7: USB bus 5 deregistered
[   72.720200] ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -110
[   72.720205] ehci_hcd: probe of 0000:00:1d.7 failed with error -110
```

I'm guessing that the ehci_hcd kernel module is not interacting well with the Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc].

What happens if you:

First remove the undetected USB devices. Then type
```
sudo modprobe -r ehci_hcd
```
Then insert the USB device again

Does it work?
(Note, even if it does work, this is not a completely satisfactory fix, because it means your USB 2.0 devices will be treated like USB 1.1 devices -- resulting in slower transfer speed.)

---

### Post by NewDisciple on 2008-08-03
Post results of: > sudo blkid and > cat /etc/fstab.

---

### Post by chris66 on 2008-08-04
unutbu: you are right about 

```
dmesg | grep ehci
```

I do get the output you posted. I tried the modprobe command but that doesn't help. If it is a problem with the USB controller and the kernel, what can I do? Am I stuck with Vista or could I use an older version of ubuntu?


NewDisciple: here the outputs of 

```
:~$ sudo blkid
/dev/sda1: UUID="AAA6902EA68FF8D9" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="FEA094B1A09471BF" LABEL="Optimus Prime" TYPE="ntfs" 
/dev/sda3: UUID="FA1698C3169881F5" LABEL="HDDRECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="06482bd2-02dc-4342-9164-da9b46547f3a" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="efd8a237-af96-4409-8a87-d6b42e7c65c4" 

```

and

```
:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=06482bd2-02dc-4342-9164-da9b46547f3a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=efd8a237-af96-4409-8a87-d6b42e7c65c4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by NewDisciple on 2008-08-04
Link Re: usb mount point [www.linuxforums.org/forum/redhat-fedora-linux-help/100102-usb-mount-point.html]("www.linuxforums.org/forum/redhat-fedora-linux-help/100102-usb-mount-point.html")& [URL="www.linuxforums.org/forum/debian-linux-help/44541-usb-mount-point.html"]
[/URL]This is the grub menu on my USB:
> default=0
timeout=5
gfxmenu (hd0,1)/boot/grub/message
title NimbleX 2007 - Boot in KDE
	root (hd0,1)
	kernel /NimbleX/base/vmlinuz max_loop=255 init=linuxrc load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=5120 probeusb root=/dev/ram0 rw quiet vga=771 changes=nimblex.data from=NimbleX autoexec=startx
	initrd /NimbleX/base/initrd.gz
title Boot in Desktop Manager
	root (hd0,1)
	kernel /NimbleX/base/vmlinuz vga=771 max_loop=255 init=linuxrc load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=5120 probeusb root=/dev/ram0 rw quiet changes=nimblex.data autoexec=kdm;sleep~604800 from=NimbleX
	initrd /NimbleX/base/initrd.gz
title NimbleX 2007 - Configure Display
	root (hd0,1)
	kernel /NimbleX/base/vmlinuz max_loop=255 init=linuxrc load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=5120 probeusb root=/dev/ram0 rw quiet vga=771 changes=nimblex.data from=NimbleX autoexec=xconf2;startx
	initrd /NimbleX/base/initrd.gz
title NimbleX 2007 - Command Line
	root (hd0,1)
	kernel /NimbleX/base/vmlinuz max_loop=255 init=linuxrc load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=5120 probeusb root=/dev/ram0 rw quiet changes=nimblex.data from=NimbleX
	initrd /NimbleX/base/initrd.gz
title Boot from the first harddisk partition
	rootnoverify (hd1,0)
	makeactive
	chainloader +1

You will note again that it searches the first hard drive partion as mentioned in the first link above and to the best of my knowledge that is why your computer can't see it.  As I earlier mentioned I think your mount point on your computer is on the wrong partition.  The grub menu is being directed to root (hd0,1), not the second partition.
Extra Links:
[URL="www.eeepclinuxos.com/distribution/viewtopic.php?f=7&t=165"]
[/URL][linux.die.net/man/1/gnome-mount]("linux.die.net/man/1/gnome-mount")
[homepages.cwi.nl/~aeb/linux/man2html/man2/mount.2.html]("homepages.cwi.nl/~aeb/linux/man2html/man2/mount.2.html")
[dev.gentoo.org/~swift/linux_sea/x902.html]("dev.gentoo.org/~swift/linux_sea/x902.html")

---

### Post by chris66 on 2008-08-04
NewDisciple: ok, is there a way to put the mount point on the first hard drive partition? Also shouldn't it bypass the problem if I boot off the Live CD (it doesn't)?redirect the computer to the

---

### Post by NewDisciple on 2008-08-04
Yep! You are correct.  I forgot that you had tried it with a live cd.  Sorry.
Recommend you re-install. At this point we're just spinning our wheels and not
getting anywhere.  Could be the easy solution.

---

### Post by NewDisciple on 2008-08-05
Did some more research and found this site: [http://www.linux-usb.org/]("http://www.linux-usb.org/").  From what I've read there it leads me to believe that unutbu is on the right target.
Here is a excerpt from that site:
> Q:  Why doesn't USB work at all? I get "device not accepting address".

A: This can be one of several problems:

    * High speed devices sometimes have problems with cables used to connect them. They're more sensitive to signal quality issues than older usb 1.1 full or low speed devices. If the device works OK at full speed on the same system, after you "rmmod ehci-hcd", this is likely the problem you're seeing. There are a lot of things you can do to change signal quality.
          o Use a different cable. Some are even marketed specifically for use with high speed devices. Most USB 1.1 cables work just fine at high speed, but the one you're using might be an exception (maybe it's been damaged).
          o Switch to a different USB connector on your computer. Back panel connectors are often right on the motherboard, with much care taken to preserve signal quality. A front panel connector probably doesn't use cabling designed with USB in mind; and its cable could be damaged by bending, baking or something else even when it's not routed through the power supply.
          o Use an external high speed hub. Those hubs have signal conditioning circuitry that may cover up certain flaws.
          o Make sure your device is using its own external power supply, or that its battery is fully charged. 
      You might be able to get the same device to work at high speed on a different machine.
    * You may have some problem with your PCI setup that's preventing your USB host controller from getting hardware interrupts. (Current Linux 2.6 kernels will actually tell you when they notice this problem; see the "dmesg" output.) When Linux submits a request, but never hears back from the controller, this is the diagnostic you'll see. To see if this is the problem, look at /proc/interrupts to see if the interrupt count for your host controller driver ever goes up. If it doesn't, this is the problem: either your BIOS isn't telling the truth to Linux (ACPI sometimes confuses these things, or setting the expected OS to windows in your BIOS), or Linux doesn't understand what it's saying.
    * Sometimes a BIOS fix will be available for your motherboard, and in other cases a more recent kernel will have a Linux fix. You may be able to work around this by passing the noapic boot option to your kernel, or (when you're using an add-in PCI card) moving the USB adapter to some other PCI slot. If you're using a current kernel and BIOS, report this problem to the Linux-kernel mailing list, with details about your motherboard and BIOS.


---

### Post by chris66 on 2008-08-06
Yes I think you are right. I tried reinstalling which didn't fix the problem. Thanks for the info, I'll do some reading and see if I can work out what to do. Seems like a fairly major problem, might have to (reluctantly) reinstall Vista!

---

### Post by NewDisciple on 2008-08-06
Seems like there is a lot of anecdotal evidence in these forums that Toshiba owners have trouble with linux.  Have you considered using Wubi?  Might be a way to use ubuntu until Toshiba issues are resolved.

---

### Post by chris66 on 2008-08-07
Yeah that is a good idea. I am keen to use linux instead of windows so wubi could be a good alternative. Will check it out.

Thanks NewDisciple for your help, much appreciated.

---

### Post by tgyorgyi on 2008-09-14
I have an FSC laptop, but it did not pick up any USB devices until I found [this]("http://ubuntuforums.org/showthread.php?t=81153&highlight=noapic+usb") post.

Trying it is not a big deal, after all you can do temporary altering of the kernel line by editing it during boot for just that one time. If it does not work, you can forget about it, if it does, there instructions on how to make the changes stick.

---

### Post by mcavady on 2008-10-20
Hey I got a "**Technika 4 port hub**", "**Model TECHHUB1**",

The temporary fix described about sorted it out.

'**sudo modprobe -r ehci_hcd**'

Posted this here so that people with the same 4 port hub can at least have the hub work, though at a lower speed.

**Before**

> desktop:~$ dmesg | grep ehci
[   28.065203] ehci_hcd 0000:00:13.3: EHCI Host Controller
[   28.065283] ehci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   28.065320] ehci_hcd 0000:00:13.3: debug port 1
[   28.065336] ehci_hcd 0000:00:13.3: irq 23, io mem 0xdbfe8c00
[   28.183703] ehci_hcd 0000:00:13.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   56.062860] usb 4-2: new high speed USB device using ehci_hcd and address 4
[  293.889704] usb 4-1: new high speed USB device using ehci_hcd and address 5
desktop:~$ sudo modprobe -r ehci_hcd
[sudo] password for james: 

**After**

> desktop:~$ dmesg | grep ehci
[   28.065203] ehci_hcd 0000:00:13.3: EHCI Host Controller
[   28.065283] ehci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   28.065320] ehci_hcd 0000:00:13.3: debug port 1
[   28.065336] ehci_hcd 0000:00:13.3: irq 23, io mem 0xdbfe8c00
[   28.183703] ehci_hcd 0000:00:13.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   56.062860] usb 4-2: new high speed USB device using ehci_hcd and address 4
[  293.889704] usb 4-1: new high speed USB device using ehci_hcd and address 5
[  966.292200] ehci_hcd 0000:00:13.3: remove, state 4
[  966.304993] ehci_hcd 0000:00:13.3: USB bus 4 deregistered
desktop:~$ 

Then I re-plugged the camera back into the 4 port hub and bobs your uncle, works fine.

Thanks for the info and I hope this will help others.:KS

---

