---
title: "Unable to mount Kodak Co. CX6230"
date: 2008-12-25
forum: Philippine Team
---

### Post by killer_d76 on 2008-12-25
any idea on how to fix this?...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97517&d=1230188829[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97518&d=1230188829[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97519&d=1230188829[/IMG]

---

### Post by loell on 2008-12-25
some older still cameras have this problem too, try reading its content from **gtkcam**.

---

### Post by killer_d76 on 2008-12-25
:KS Merry Christmas bro :KS, thanks for the quick reply loell, as always ;)..hhmmm, but this camera was working properly with Hardy?.. :confused:

---

### Post by loell on 2008-12-25
Merry Christmas :)

hmm,. thats odd, how about mounting it with sudo?

ie: launch nautilus in super user mode.

---

### Post by killer_d76 on 2008-12-25
will try that later... but do you think i may have erased something important from the system, because i tried running "sudo apt-get autoremove" a few days ago to free up some unnecessary files, since this is the first time i plugged this camera on Ibex do you think running "autoremove" must have deleted some necessary files to make this working?

---

### Post by loell on 2008-12-25
unlikely, but in any case, the mounting of still cameras if i'm not mistaken, depends on  **libgphoto2-2**.

if you still have a copy of hardy installed/ or a livecd , maybe we could get the modules loaded when it is plugged, then compare it to the loaded module when the camera is also plugged in intrepid.

---

### Post by killer_d76 on 2008-12-25
will try that later bro.. thanks again! ;)

.. by the way how can i check the modules used on hardy or ibex when the camera is plugged in?.

---

### Post by killer_d76 on 2008-12-30
here's what happened if i plugged my Kodak CX6230 on Hardy Heron... it automatically detected my camera!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=98079&d=1230643989[/IMG]

---

### Post by loell on 2008-12-30
can you post the

```
lsmod
```

---

### Post by killer_d76 on 2008-12-30
okey.. i'll boot this thing up again ;)

---

### Post by killer_d76 on 2008-12-30
okey here's the result for **lsmod** result on hardy when i have the camera connected..



```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4992  0 
vfat                   14464  0 
fat                    54556  1 vfat
usb_storage            73664  0 
libusual               19108  1 usb_storage
ipv6                  267780  8 
i915                   32512  2 
drm                    82580  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
rfkill_input            5504  0 
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
pcmcia                 40876  0 
snd_mixer_oss          17920  1 snd_pcm_oss
b43                   115104  0 
rfkill                  8592  15 rfkill_input,b43
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
mac80211              165652  1 b43
snd_hwdep              10500  1 snd_hda_intel
cfg80211               15112  1 mac80211
led_class               6020  1 b43
snd_seq_dummy           4868  0 
input_polldev           5896  1 b43
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27276  1 
sdhci                  19076  0 
video                  19856  0 
rsrc_nonstatic         13696  1 yenta_socket
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      6916  0 
battery                14212  0 
intel_agp              25492  1 
output                  4736  1 video
button                  9232  0 
serio_raw               7940  0 
shpchp                 34452  0 
mmc_core               51460  1 sdhci
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt               13092  0 
evdev                  13056  19 
pcspkr                  4224  0 
agpgart                34760  3 drm,intel_agp
pci_hotplug            30880  1 shpchp
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
psmouse                40336  0 
squashfs               49160  1 
loop                   18948  2 
unionfs                76752  1 
nls_cp437               6656  1 
isofs                  36388  1 
ext3                  136712  0 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 31872  0 
hid                    38784  1 usbhid
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  0 
ata_piix               19588  1 
pata_acpi               8320  0 
ata_generic             8324  0 
libata                159344  3 ata_piix,pata_acpi,ata_generic
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
r8169                  32900  0 
ssb                    32260  1 b43
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
ubuntu@ubuntu:~$ 

```

 and i've also got **lsusb** result from hardy..

```
ubuntu@ubuntu:~$ lsusb
Bus 005 Device 005: ID 0b27:0165 Ritek Corp. 
Bus 005 Device 003: ID 0c45:624f Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 040a:0573 Kodak Co. CX6230
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
ubuntu@ubuntu:~$ 
```







and here's the **lsmod** result on **Ibex** that i am currently using on my laptop..

```
arvin@arvin-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  0 
nls_cp437              13696  0 
vfat                   18816  0 
fat                    57376  1 vfat
usb_storage            81728  0 
libusual               27156  1 usb_storage
ipv6                  263972  10 
michael_mic            10496  2 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
af_packet              25728  4 
i915                   38144  3 
drm                    86056  4 i915
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
vboxdrv                72472  0 
ppdev                  15620  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace      11396  0 
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
pci_slot               12552  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
pcmcia                 43052  0 
evdev                  17696  12 
microdia              130584  0 
videodev               41344  1 microdia
v4l1_compat            22404  1 videodev
serio_raw              13444  0 
psmouse                45200  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
mmc_core               58268  1 sdhci
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_hda_intel         381488  3 
ieee80211_crypt_tkip    17024  0 
wl                   1076372  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
battery                18436  0 
ac                     12292  0 
video                  25104  0 
output                 11008  1 video
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
pcspkr                 10624  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  2 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  1 
ata_generic            12932  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
pata_acpi              12160  0 
libata                177312  3 ata_piix,ata_generic,pata_acpi
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               149104  7 usb_storage,libusual,microdia,usbhid,ehci_hcd,uhci_hcd
r8169                  35972  0 
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
arvin@arvin-laptop:~$ 

```

and lsusb as well..

```
arvin@arvin-laptop:~$ lsusb
Bus 005 Device 003: ID 0c45:624f Microdia PC Camera (SN9C201)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 040a:0573 Kodak Co. CX6230
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
arvin@arvin-laptop:~$ 

```

thanks in advance for the help loell.. ;)

---

### Post by loell on 2008-12-30
i couldn't find a module that relates to the device.. :(

because of this, my suspicion grows that this is a libgphoto2 regression, or could check if gphoto2 is even installed?

when installed try t mount the camera

```
gphoto2 -P --camera \"Kodak CX6330\" --port usb:
```

and

```
gphoto2 -D --camera \"Kodak CX6330\" --port usb:
```

---

### Post by killer_d76 on 2008-12-31
thanks for the help loell... when i typed the command you have provided it mentioned that i need to install gphoto2.. so i did sudo apt-get install and install gphoto2..

then i type the command above and here's what i got..

```
arvin@arvin-laptop:~$ gphoto2 -P --camera \"Kodak CX6230\" --port usb:
                                                                               
*** Error ***              
PTP I/O error

*** Error ***              
An error occurred in the io-library ('Unspecified error'): No error description available
*** Error (-1: 'Unspecified error') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt -P --camera ""Kodak" "CX6230"" --port "usb:"

Please make sure there is sufficient quoting around the arguments.

arvin@arvin-laptop:~$ gphoto2 -D --camera \"Kodak CX6230\" --port usb:
                                                                               
*** Error ***              
PTP I/O error

*** Error ***              
An error occurred in the io-library ('Unspecified error'): No error description available
*** Error (-1: 'Unspecified error') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt -D --camera ""Kodak" "CX6230"" --port "usb:"

Please make sure there is sufficient quoting around the arguments.

arvin@arvin-laptop:~$ 

```

by the way loell.. does it really have to be CX6330?.. because my camera is CX6230.. thanks.

---

### Post by loell on 2008-12-31
oh.. my bad, yeah you should cx230.

---

### Post by killer_d76 on 2008-12-31
got error bossing.. ;).. by the way.. Happy New Year! hehehe..

```
arvin@arvin-laptop:~$ arvin@arvin-laptop:~$ gphoto2 -P --camera \"Kodak CX6230\" --port usb:
bash: arvin@arvin-laptop:~$: command not found
arvin@arvin-laptop:~$                                                                                
arvin@arvin-laptop:~$ *** Error ***              
bash: chat log 2: command not found
arvin@arvin-laptop:~$ An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x40a, product 0x573). Make sure this device is connected to the computer.
bash: syntax error near unexpected token `('
arvin@arvin-laptop:~$ *** Error (-2: 'Bad parameters') ***       
bash: syntax error near unexpected token `('
arvin@arvin-laptop:~$ 
arvin@arvin-laptop:~$ For debugging messages, please use the --debug option.
bash: For: command not found
arvin@arvin-laptop:~$ Debugging messages may help finding a solution to your problem.
bash: Debugging: command not found
arvin@arvin-laptop:~$ If you intend to send any error or debug messages to the gphoto
bash: If: command not found
arvin@arvin-laptop:~$ developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
bash: gphoto-devel@lists.sourceforge.net: No such file or directory
arvin@arvin-laptop:~$ gphoto2 as follows:
*** Error (-1: 'Unspecified error') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt "as" "follows:"

Please make sure there is sufficient quoting around the arguments.

arvin@arvin-laptop:~$ 
arvin@arvin-laptop:~$     env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt -P --camera ""Kodak" "CX6230"" --port "usb:"
                                                                               
*** Error ***              
PTP I/O error

*** Error ***              
An error occurred in the io-library ('Unspecified error'): No error description available
*** Error (-1: 'Unspecified error') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --debug --debug-logfile=my-logfile.txt -P --camera "Kodak CX6230" --port "usb:"

Please make sure there is sufficient quoting around the arguments.

arvin@arvin-laptop:~$ 
arvin@arvin-laptop:~$ Please make sure there is sufficient quoting around the arguments.
bash: Please: command not found
arvin@arvin-laptop:~$ 
arvin@arvin-laptop:~$ arvin@arvin-laptop:~$ 


```

---

### Post by killer_d76 on 2008-12-31
....but Windows on VBox was able to detect the camera? :confused:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=98251&d=1230746804[/IMG]

---

### Post by loell on 2008-12-31
like I said, this could most likely mean that this is a gphoto **regression** a regression means a change or changes in the code that would have cause things not to work properly.

or a **deprecation**, that would mean they deliberately pull off the compatibility for the particular device for some reason.

in either  cases, you might find better answers at [gphoto's mailing list]("http://www.gphoto.org/")

you could ask why intrepid's libgphoto V-2.4.2 couldn't detect your camera.

---

### Post by killer_d76 on 2009-01-01
is there another way of mounting this camera other than using libgphoto?

---

### Post by loell on 2009-01-01
> **killer_d76 said:**
> is there another way of mounting this camera other than using libgphoto?

none

---

