---
title: "Toshiba A200-13X - Webcam issue"
date: 2007-10-16
forum: Philippine Team
---

### Post by rjmdomingo2003 on 2007-10-16
Kumusta sa inyo! Napagana ko na yung sound & webcam (thru luvcview) sa lappy kong 'to pwera na lang sa wireless ko. Pero priority ko now is mapagana yung webcam with kopete or gyachi. Green frame lang yung nakikita ko while running in kopete.
Nag-search na ako sa related threads & google pero no luck. Nasubukan ko na ring install yung ibang drivers (spca & camsoft) pero ni hindi nag-switch on yung webcam. Tulong po.
Thanks. Mabuhay po tayo.

---

### Post by loell on 2007-10-16
ganon po talaga kapagka uvc base driver ang webcam, built in po ba ito?

kung attach via usb, can you do ```
lsusb
``` and if its built in can you do ```
lspci
``` , then paste the two output here.

para malaman natin kung anong vendor id  at device id nya.


idlip lang muna ako ;)

---

### Post by rjmdomingo2003 on 2007-10-17
Sige loell, mamya ko na i-post yung mga output (nasa trabaho pa ko eh). 

Built-in USB webcam 'to na Chicony Electronics Co. ang manufacturer. Di ko lang kabisado yung bus/serial #.

Later dude.:neutral:

---

### Post by rjmdomingo2003 on 2007-10-17
Eto output ng:
$lsusb
```

Bus 005 Device 004: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c51a Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 1110:9031 Analog Devices Canada, Ltd (Allied Telesyn) 
Bus 002 Device 001: ID 0000:0000
```

$lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 110M / GeForce Go 7300 (rev a1)
04:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

Pasensya na boss loell medyo ginabi na 'ko. Salamat nang marami.

---

### Post by loell on 2007-10-17
can you also do a **lsmod** , then paste the output here?

my initial find is,
chicony webcams are rumored to work in gutsy a little bit well than fiesty ;)

however, i found this too [http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg115469.html]("http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg115469.html")

since, different webcam apps  uses different API's some used new once and others still old once.


i know gyachi uses an older implementation :(  
im not sure with kopete.

can you also try this applications?  ekiga and amsn.

---

### Post by rjmdomingo2003 on 2007-10-18
[FONT="Trebuchet MS"][/FONT]Mamya ko na ibibigay ang output ng $lsmod, as usual, nasa trabaho pa 'ko eh.

Yan din ang nakita ko sa mga threads dito na sa gutsy, magwo-work much better ang webcam na 'to. Pero di ko pa nasubukan mag-upgrade ng gutsy kernel from feisty's para patunayan 'tong claim na 'to. Well, I guess I have to take the plunge now.

Meron din pala akong Logitech Orbit/Sphere webcam. Palagay mo mas "madali" paganahin 'to? Thanks bossing!

---

### Post by rjmdomingo2003 on 2007-10-18
[FONT="Trebuchet MS"][/FONT]BTW, nasubukan ko na rin ang ekiga pero wala ring vid output (bouncing ball lang). Di ko pa sinubukan ang amsn kasi interested lang ako sa YM.

---

### Post by loell on 2007-10-18
> **rjmdomingo2003 said:**
> BTW, nasubukan ko na rin ang ekiga pero wala ring vid output (bouncing ball lang). Di ko pa sinubukan ang amsn kasi interested lang ako sa YM.

heheh, pareho pala tayo, maka YM kasi tayong manga pinoy eh, or atleast karamihan sa atin.

---

### Post by rjmdomingo2003 on 2007-10-18
> **loell said:**
> can you also do a **lsmod**

Here it is:

$lsmod

```
Module                  Size  Used by
ppp_deflate             6912  0 
zlib_deflate           20504  1 ppp_deflate
bsd_comp                7040  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
pppoatm                 6656  1 
ppp_generic            29076  7 ppp_deflate,bsd_comp,pppoatm
slhc                    7680  1 ppp_generic
ipv6                  268960  12 
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_conservative     8200  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
dev_acpi               12292  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
container               5248  0 
sbs                    15652  0 
dock                   10268  0 
i2c_ec                  6016  1 sbs
ac                      6020  0 
video                  16388  0 
asus_acpi              17308  0 
button                  8720  0 
battery                10756  0 
backlight               7040  1 asus_acpi
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_hda_intel         262552  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
joydev                 10816  0 
snd_seq_oss            35072  0 
pcmcia                 39212  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54000  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
ueagle_atm             26792  0 
xpad                    9988  0 
usbatm                 20224  2 ueagle_atm
uvcvideo               42500  0 
sdhci                  18700  0 
nvidia               6837140  22 
usbhid                 26592  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
snd                    56324  8 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
hid                    27392  1 usbhid
videodev               28160  1 uvcvideo
v4l1_compat            15236  2 uvcvideo,videodev
v4l2_common            25216  2 uvcvideo,videodev
af_packet              23816  4 
mmc_core               26756  1 sdhci
tifm_7xx1               8704  0 
tifm_core              11140  1 tifm_7xx1
psmouse                38920  0 
iTCO_wdt               11812  0 
i2c_core               22656  2 i2c_ec,nvidia
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               7940  0 
intel_agp              26140  1 
agpgart                35400  2 nvidia,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  6 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
r8169                  32392  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
uhci_hcd               25360  0 
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
usbcore               134280  8 ueagle_atm,xpad,usbatm,uvcvideo,usbhid,uhci_hcd,ehci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
melski@lapdanz:~$ lsmod
Module                  Size  Used by
ppp_deflate             6912  0 
zlib_deflate           20504  1 ppp_deflate
bsd_comp                7040  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
pppoatm                 6656  1 
ppp_generic            29076  7 ppp_deflate,bsd_comp,pppoatm
slhc                    7680  1 ppp_generic
ipv6                  268960  12 
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_conservative     8200  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
dev_acpi               12292  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
container               5248  0 
sbs                    15652  0 
dock                   10268  0 
i2c_ec                  6016  1 sbs
ac                      6020  0 
video                  16388  0 
asus_acpi              17308  0 
button                  8720  0 
battery                10756  0 
backlight               7040  1 asus_acpi
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_hda_intel         262552  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
joydev                 10816  0 
snd_seq_oss            35072  0 
pcmcia                 39212  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54000  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
ueagle_atm             26792  0 
xpad                    9988  0 
usbatm                 20224  2 ueagle_atm
uvcvideo               42500  0 
sdhci                  18700  0 
nvidia               6837140  22 
usbhid                 26592  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
snd                    56324  8 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
hid                    27392  1 usbhid
videodev               28160  1 uvcvideo
v4l1_compat            15236  2 uvcvideo,videodev
v4l2_common            25216  2 uvcvideo,videodev
af_packet              23816  4 
mmc_core               26756  1 sdhci
tifm_7xx1               8704  0 
tifm_core              11140  1 tifm_7xx1
psmouse                38920  0 
iTCO_wdt               11812  0 
i2c_core               22656  2 i2c_ec,nvidia
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               7940  0 
intel_agp              26140  1 
agpgart                35400  2 nvidia,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  6 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
r8169                  32392  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
uhci_hcd               25360  0 
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
usbcore               134280  8 ueagle_atm,xpad,usbatm,uvcvideo,usbhid,uhci_hcd,ehci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
```

---

### Post by loell on 2007-10-18
```
videodev               28160  1 uvcvideo
v4l1_compat            15236  2 uvcvideo,videodev
v4l2_common            25216  2 uvcvideo,videodev
```

so it is using a **uvc driver**, sigh*. 

i guess , there's not much we can do for now with that webcam,

since meron ka na mang **logitech** webcam which has better compaitbility with linux. sa ngayon, yun na lang muna ang gamitin mo. ;)

until such time na may mag implement nang ,  **"webcam using  gstreamer API"**

it shouldn't be that long wait.

---

### Post by kopinux on 2007-10-19
wag niyo rin kalimutan i-evaluate [http://webmessenger.yahoo.com/](http://webmessenger.yahoo.com/)
beta test niyo sa linux yung yahoo webmessenger.

tapos bigyan niyo ng good feedback na ginagamit niyo sa linux at paganihin na yung voice at webcam feature ng flash.

---

### Post by rjmdomingo2003 on 2007-10-19
> **loell said:**
> 

so it is using a **uvc driver**, sigh*. 

i guess , there's not much we can do for now with that webcam,

since meron ka na mang **logitech** webcam which has better compaitbility with linux. sa ngayon, yun na lang muna ang gamitin mo. ;)

until such time na may mag implement nang ,  **"webcam using  gstreamer API"**

it shouldn't be that long wait.Ano pong driver ang gagamitin ko para sa logitech orbit/sphere ko? I mean, suitable para sa kopete, gyachi..

---

### Post by rjmdomingo2003 on 2007-10-19
> **kopinux said:**
> wag niyo rin kalimutan i-evaluate [http://webmessenger.yahoo.com/](http://webmessenger.yahoo.com/)
beta test niyo sa linux yung yahoo webmessenger.

tapos bigyan niyo ng good feedback na ginagamit niyo sa linux at paganihin na yung voice at webcam feature ng flash.
Susubukan ko po. I'll see kung gagana ang webcam ko. Thanks!

---

### Post by kopinux on 2007-10-19
yung feedback a, pinakaimportante yun para hindi isnabin ng yahoo ang mga ubuntu users.

---

### Post by loell on 2007-10-19
> **rjmdomingo2003 said:**
> Ano pong driver ang gagamitin ko para sa logitech orbit/sphere ko? I mean, suitable para sa kopete, gyachi..

**spca5xx ** ang driver na gagamitin nya, which is installed by default in ubuntu , if you plug it, usually, ubuntu will  automatically detect the webcam.

---

### Post by rjmdomingo2003 on 2007-10-19
> **loell said:**
> **spca5xx ** ang driver na gagamitin nya, which is installed by default in ubuntu , if you plug it, usually, ubuntu will  automatically detect the webcam.

Maraming salamat loell. Susubukan ko 'tong driver na 'to. Susubukan ko na rin yung built-in webcam sa gutsy. Na-download ko na yung .iso nya :popcorn: Inform na lang kung working fine.

---

### Post by kopinux on 2007-10-24
ako naman boss!
[B]
$ lsusb[/B]
> Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:d001 Logitech, Inc. QuickCam Pro
Bus 001 Device 001: ID 0000:0000

[B]
$ lsmod[/B]
> Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
video                  18060  0 
sbs                    19592  0 
container               5504  0 
dock                   10656  0 
button                  8976  0 
ac                      6148  0 
battery                11012  0 
lp                     12580  0 
loop                   19076  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
nvidia               6221648  24 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_sis96x              6404  0 
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
psmouse                39952  0 
serio_raw               8068  0 
i2c_core               26112  2 nvidia,i2c_sis96x
sis_agp                10116  1 
agpgart                35016  2 nvidia,sis_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
evdev                  11136  4 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  5 
floppy                 60004  0 
sis900                 24960  0 
mii                     6528  1 sis900
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  3 ehci_hcd,ohci_hcd
pata_sis               15236  4 
ata_generic             8452  0 
libata                125168  2 pata_sis,ata_generic
scsi_mod              147084  3 sg,sd_mod,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor

compatible ba yung logitech quickcam ko? luman na yung webcam ko.

---

### Post by loell on 2007-10-24
ang webcam mo ay

[Logitech QuickCam Pro (dark focus ring)]("http://www.qbik.ch/usb/devices/showdev.php?id=307") 

luckily the driver is, 

[http://nw802.sourceforge.net/news.html]("http://nw802.sourceforge.net/news.html")

---

### Post by kopinux on 2007-10-25
na download ko na yung .tar.bz ano gagawin ko dito boss?

---

### Post by rjmdomingo2003 on 2007-10-25
> **kopinux said:**
> wag niyo rin kalimutan i-evaluate [http://webmessenger.yahoo.com/](http://webmessenger.yahoo.com/)
beta test niyo sa linux yung yahoo webmessenger.

tapos bigyan niyo ng good feedback na ginagamit niyo sa linux at paganihin na yung voice at webcam feature ng flash.
kopi, may idea ka ba kung kelan magkakaroon ng webcam feature 'to?

Buti ka pa posible magamit yung webcam mo, mine not possible sa feisty.

Best of luck sa pag-compile ng na-download mong driver.

---

### Post by loell on 2007-10-25
> **kopinux said:**
> na download ko na yung .tar.bz ano gagawin ko dito boss?

extract, then compile, baka kailangan mo rin mag install nang kernel source header.

---

### Post by kopinux on 2007-10-25
> **rjmdomingo2003 said:**
> kopi, may idea ka ba kung kelan magkakaroon ng webcam feature 'to?

Buti ka pa posible magamit yung webcam mo, mine not possible sa feisty.


hindi ko pa alam kung kailan, beta pa, detected yung mic, at tv-tuner ko, yung webcam hindi, pero ginagamit ko din dati yung tv-tuner para webcam gamit video-in rca wireless cctv.

kailangan ko talaga ng goodluck, nainstall ko na yung build-essential, kaso nag ka problema sa error: /usr/src/linux/include/linux/**modversions.h**: No such file or directory

hinanap ko wala doon yung modversion.h

teka marunong ka ba gumamit ng checkinstall? naguguluhan ako, pero sabi masmaganda daw ito kesa sa makeinstall?. gusto ko kasi gumawa ng .deb file muna.

---

### Post by loell on 2007-10-25
like what is suspected kailangan mo nang kernel headers paramag compile nang driver,  install the kernel headers by

```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r`
```

---

