---
title: "How can I add Intel Experimental Modesetting to Xorg??"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-11-19
I want to add the "Intel experimental modesetting" as my default graphics driver to Xorg.conf but I'm not sure how.

I'm using intrepid so I can't use "gksudo displayconfig-gtk" so please don't suggest that.

Anyone have an ideas??

Thanks!!

This is my xorg:
```


Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


```

---

### Post by starcannon on 2008-11-19
Heres an example of sorts:
```

Section "Device"
    Identifier    "Configured Video Device"
    Driver         "driver_name_here"
    Option       "Some_configurable_option_here"    "bool_here"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Modeline    "Modeline_name"    modeline data goes here
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Subsection "Display"
        Depth "24" # can be 8, 16, 24, 32. 24 is usually a good choice.
        Modes "Modeline_name"
        Virtual your_screen resolution
    EndSubsection
EndSection

```Anyway, this is only an example; as you can see, you can modify this xorg.con just like any other. You can even tell it what driver to use under the device section as well as any and all other xorg options you've used in the past.

GL and Keep it fun.

---

### Post by pluckypigeon on 2008-11-19
> **starcannon said:**
> Heres an example of sorts:
```

Section "Device"
    Identifier    "Configured Video Device"
    Driver         "driver_name_here"
    Option       "Some_configurable_option_here"    "bool_here"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Modeline    "Modeline_name"    modeline data goes here
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Subsection "Display"
        Depth "24" # can be 8, 16, 24, 32. 24 is usually a good choice.
        Modes "Modeline_name"
        Virtual your_screen resolution
    EndSubsection
EndSection

```Anyway, this is only an example; as you can see, you can modify this xorg.con just like any other. You can even tell it what driver to use under the device section as well as any and all other xorg options you've used in the past.

GL and Keep it fun.

Thanks for your quick reply but I'm a little confused :confused:

---

### Post by pluckypigeon on 2008-11-19
[QUOTE=starcannon]
Please if you could post in your thread the output of:
```

sudo lshw -C display

```
[/QUOTE]
```

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

I've been having problems with the default settings ever since I upgraded to Intrepid... especially with things like compiz... (I am aware that compiz have recently blacklisted my graphics card)

---

### Post by starcannon on 2008-11-20
Okay after reading a bit on bugs and other problems with the i810 driver and its associated chipsets in 8.10 intrepid, I would first like to recommend reverting back to 8.04; if however, this is not an option to exercise, then the next place to go forward is to start hacking at your xorg.conf, and perhaps use fusion-icon to force compiz to load (or hack the compiz config file either way).

If you decide to attempt compiz on the i810 it may require a bit of work, indeed it was enough of a problem child that it appears to have been blacklisted by the sounds of it; so, lets find out what modules(drivers) are currently loaded:
```
lsmod
```please post that output here.

---

### Post by PmDematagoda on 2008-11-20
By Intel Experimental Modesetting, do you mean Kernel-based ModeSetting? If so, then you will need to look at the kernel first before thinking of Xorg since you first need to make the modesetting occur at the kernel-level before being able to use it on X. And for that kind of stuff, you may need to ask the people involved in it themselves like Dave Airlie, etc. This may be more difficult since Intel ModeSetting still has a few problems and is the reason it was turned off by default on Fedora 10.

---

### Post by starcannon on 2008-11-20
PmDematagoda,

I'm interested in reading about this, where can I go to learn more? I'll google it, but if you have a good article or 2 I'd be interested in those as well.

@OP, yikes, sounds like 8.10 is gonna be a bit of a project :) keep it fun

---

### Post by pluckypigeon on 2008-11-20
> **starcannon said:**
> Okay after reading a bit on bugs and other problems with the i810 driver and its associated chipsets in 8.10 intrepid, I would first like to recommend reverting back to 8.04; if however, this is not an option to exercise, then the next place to go forward is to start hacking at your xorg.conf, and perhaps use fusion-icon to force compiz to load (or hack the compiz config file either way).

If you decide to attempt compiz on the i810 it may require a bit of work, indeed it was enough of a problem child that it appears to have been blacklisted by the sounds of it; so, lets find out what modules(drivers) are currently loaded:
```
lsmod
```please post that output here.

this is the output of lsmod

```

Module                  Size  Used by
ipv6                  263972  8 
i915                   38144  2 
af_packet              25728  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
vboxdrv                72472  0 
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
sbs                    19464  0 
container              11520  0 
video                  25104  0 
output                 11008  1 video
wmi                    14504  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
vfat                   18816  0 
fat                    57376  1 vfat
ac                     12292  0 
lp                     17156  0 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
evdev                  17696  7 
psmouse                45200  0 
serio_raw              13444  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm                83204  2 snd_intel8x0,snd_ac97_codec
snd_seq                57776  1 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  1 snd_seq
intel_rng              12672  0 
button                 14224  0 
intel_agp              33724  1 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
agpgart                42184  3 drm,intel_agp
snd                    63268  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_seq,snd_timer,snd_seq_device
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
ext3                  133384  3 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  7 
crc_t10dif              9984  1 sd_mod
pata_acpi              12160  0 
sg                     39732  0 
usb_storage            81728  0 
libusual               27156  1 usb_storage
ata_piix               24580  4 
ata_generic            12932  0 
libata                177312  3 pata_acpi,ata_piix,ata_generic
e100                   41356  0 
mii                    13440  1 e100
uhci_hcd               30736  0 
ehci_hcd               43404  0 
scsi_mod              155212  5 sr_mod,sd_mod,sg,usb_storage,libata
dock                   16656  1 libata
usbcore               149104  5 usb_storage,libusual,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

---

### Post by PmDematagoda on 2008-11-20
> **starcannon said:**
> PmDematagoda,

I'm interested in reading about this, where can I go to learn more? I'll google it, but if you have a good article or 2 I'd be interested in those as well.

@OP, yikes, sounds like 8.10 is gonna be a bit of a project :) keep it fun

I am not an expert on the subject, but in my opinion, these articles(one is just a wiki) are quite useful:-
[http://fedoraproject.org/wiki/Features/KernelModesetting](http://fedoraproject.org/wiki/Features/KernelModesetting)
[http://www.phoronix.com/scan.php?page=article&item=xorg_kms_2008&num=1](http://www.phoronix.com/scan.php?page=article&item=xorg_kms_2008&num=1)

---

