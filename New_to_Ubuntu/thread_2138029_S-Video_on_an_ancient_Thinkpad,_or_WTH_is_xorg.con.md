---
title: "S-Video on an ancient Thinkpad, or WTH is xorg.conf?"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by macinpidey on 2013-04-22
I'm a total n00b to linux, running Xubuntu 12.04 on an IBM R51 2883 Thinkpad with an intel 855 graphics chipset.  With XP my s-video hooked up with nary a glitch, but now it's not even being detected.  I've read posts telling me to edit the xorg.conf file, but I have no idea where the friggin file is.  Supposedly my system has xorg installed, but I can't for the life of me figure my way around the system.

Any advice for a long-time mac user and GUI girl who's somewhat intimidated by terminal commands?

Please, Thank You and a huge Kiss on the Cheek to the one who can help me get this working.

---

### Post by Col936 on 2013-04-22
I can't provide a DIRECT answer, but I suggest poking around in the root( File System) directory in your file browser application. Basically just look in the different directories for folders that seem relevant. And if you get to know the OS, you'll find that it's not TOO different from Mac, as well as the fact that you're going to have to use the terminal a bit for certain things. I had to freaking Google commands all the time when I was a beginner. Nice computer by the way :)

---

### Post by macinpidey on 2013-04-22
I've poked through all the folders but, as far as I can tell, there's no xorg.conf file.  Anybody know if there's some kind of search I can use on the internal file system?

---

### Post by steeldriver on 2013-04-22
The xorg.conf file would be located in the /etc/X11 directory HOWEVER most of the current xserver-xorg implementations (at least the open source ones) probe the hardware at runtime and don't use an xorg.conf file at all

That being said, if the file exists it should get read in addition to the hardware probe, so you should be able to create one and put any custom configs in there - for example on this machine I have:

```
$ cat /etc/X11/xorg.conf
Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
Option "NoLogo" "True"
# Option "UseVBios" 0
EndSection

```

which suppresses the proprietary Nvidia banner.

[Sorry I can't help with the specifics - I *do* have an old Thinkpad X30 with IBM graphics but I never tried to get S-Video out of it]

---

### Post by macinpidey on 2013-04-22
So in other words, if I don't have one I can just put one there and the system will recognize it?  Scary yet cool!  ::begins evil machinations of learning code and hacking this machine until it begs for mercy::

---

### Post by papibe on 2013-04-22
Hi macinpidey.

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [pastebin.ubuntu.com]("http://pastebin.ubuntu.com/"), and then post back the link.

Regards,

---

### Post by macinpidey on 2013-04-22
OK, the content is pasted at:
[pastebin.ubuntu.com/5594247/]("http://ubuntuforums.org/pastebin.ubuntu.com/5594247/")

---

### Post by papibe on 2013-04-22
Thanks.

There's no reference to the S-Video output. Are you sure you boot your computer with the cable connected and the TV turned on?

Could you post the result of this command?
```
xrandr
```
Regards.

---

### Post by tgalati4 on 2013-04-22
I have a T43p built around the same time as an R51.  I did get S-video to work under linux, but as I recall, I had to plug it into a TV to wake it up, then hit the Fn-F8 key to cycle through the displays.  No xorg.conf fiddling was needed.  That was running Jaunty with open radeon (ati) drivers.  I don't know how the Intel graphics chip (in your case 855) responds to S-video.  You will have to do more searching.

Open a terminal:

```
lsmod
modinfo i915
```

tgalati4@Mint14-Extensa ~ $ modinfo i915
filename:       /lib/modules/3.5.0-27-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Tungsten Graphics, Inc.
license:        GPL and additional rights
srcversion:     692E5F708611008E1674B76
alias:          pci:v00008086d00000155sv*sd*bc03sc*i*
alias:          pci:v00008086d00000157sv*sd*bc03sc*i*
alias:          pci:v00008086d00000F30sv*sd*bc03sc*i*
alias:          pci:v00008086d0000016Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000015Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000162sv*sd*bc03sc*i*
alias:          pci:v00008086d00000152sv*sd*bc03sc*i*
alias:          pci:v00008086d00000166sv*sd*bc03sc*i*
alias:          pci:v00008086d00000156sv*sd*bc03sc*i*
alias:          pci:v00008086d0000010Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000126sv*sd*bc03sc*i*
alias:          pci:v00008086d00000116sv*sd*bc03sc*i*
alias:          pci:v00008086d00000106sv*sd*bc03sc*i*
alias:          pci:v00008086d00000122sv*sd*bc03sc*i*
alias:          pci:v00008086d00000112sv*sd*bc03sc*i*
alias:          pci:v00008086d00000102sv*sd*bc03sc*i*
alias:          pci:v00008086d00000046sv*sd*bc03sc*i*
alias:          pci:v00008086d00000042sv*sd*bc03sc*i*
alias:          pci:v00008086d0000A011sv*sd*bc03sc*i*
alias:          pci:v00008086d0000A001sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E92sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E42sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E32sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E22sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E12sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E02sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A42sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A12sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A02sv*sd*bc03sc*i*
alias:          pci:v00008086d000029D2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029C2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029B2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029A2sv*sd*bc03sc*i*
alias:          pci:v00008086d00002992sv*sd*bc03sc*i*
alias:          pci:v00008086d00002982sv*sd*bc03sc*i*
alias:          pci:v00008086d00002972sv*sd*bc03sc*i*
alias:          pci:v00008086d000027AEsv*sd*bc03sc*i*
alias:          pci:v00008086d000027A2sv*sd*bc03sc*i*
alias:          pci:v00008086d00002772sv*sd*bc03sc*i*
alias:          pci:v00008086d00002592sv*sd*bc03sc*i*
alias:          pci:v00008086d0000258Asv*sd*bc03sc*i*
alias:          pci:v00008086d00002582sv*sd*bc03sc*i*
alias:          pci:v00008086d00002572sv*sd*bc03sc*i*
alias:          pci:v00008086d0000358Esv*sd*bc03sc*i*
alias:          pci:v00008086d00003582sv*sd*bc03sc*i*
alias:          pci:v00008086d00002562sv*sd*bc03sc*i*
alias:          pci:v00008086d00003577sv*sd*bc03sc*i*
depends:        drm,drm_kms_helper,video,i2c-algo-bit
intree:         Y
vermagic:       3.5.0-27-generic SMP mod_unload modversions 
parm:           invert_brightness:Invert backlight brightness (-1 force normal, 0 machine defaults, 1 force inversion), please report PCI device ID, subsystem vendor and subsystem device ID to [email]dri-devel@lists.freedesktop.org[/email], if your machine needs it. It will then be included in an upcoming module version. (int)
parm:           modeset:Use kernel modesetting [KMS] (0=DRM_I915_KMS from .config, 1=on, -1=force vga console preference [default]) (int)
parm:           fbpercrtc:int

You are probably running a different Intel driver such as i810:

tgalati4@Mint14-Extensa ~ $ modinfo i810
filename:       /lib/modules/3.5.0-27-generic/kernel/drivers/gpu/drm/i810/i810.ko
license:        GPL and additional rights
description:    Intel i810
author:         VA Linux Systems Inc.
srcversion:     89374CACC51639B5B32918A
depends:        drm
intree:         Y
vermagic:       3.5.0-27-generic SMP mod_unload modversions

Modinfo gives you the switches that you can play with directly when loading the module.  Xorg.conf allows additional configuration, but you will have to search for the switches specific to the video driver that you are running.

---

### Post by macinpidey on 2013-04-23
pabibe - 

When I enter xrandr I get:

pidey@pidey-ThinkPad-R51:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 32767 x 32767
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)


The machine is freshly rebooted with the s-video cable attached, but the damn thing just plain isn't showing up.  Grrrrrrr.


tgalati4 -

For those two commands I get:

pidey@pidey-ThinkPad-R51:~$ lsmod
Module                  Size  Used by
rfcomm                 38139  4 
michael_mic            12540  4 
arc4                   12473  2 
lib80211_crypt_tkip    17240  1 
lib80211_crypt_ccmp    12789  1 
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
thinkpad_acpi          73942  1 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
pcmcia                 39826  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                96718  0 
snd                    62218  16 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  423514  2 
ipw2200               146210  0 
nsc_ircc               23240  0 
libipw                 46732  1 ipw2200
serio_raw              13027  0 
nvram                  14029  1 thinkpad_acpi
cfg80211              178877  2 ipw2200,libipw
soundcore              14635  1 snd
irda                  185517  1 nsc_ircc
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
dm_multipath           22747  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
lib80211               14040  4 lib80211_crypt_tkip,lib80211_crypt_ccmp,ipw2200,libipw
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
crc_ccitt              12627  1 irda
parport_pc             32114  1 
ppdev                  12849  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
binfmt_misc            17292  1 
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
shpchp                 32265  0 
i2c_algo_bit           13199  1 i915
mac_hid                13077  0 
video                  19115  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
e100                   36289  0 
floppy                 60184  0 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16100  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
pidey@pidey-ThinkPad-R51:~$ modinfo i95
ERROR: modinfo: could not find module i95

---

### Post by tgalati4 on 2013-04-23
You are running i915 video driver for the Intel i915 series video chipsets--and others that are similar:

**i915** 423514 2
drm_kms_helper 45466 1 **i915**
drm 197641 3 **i915**,drm_kms_helper

There is no i95 video module.  Eye Nine One Five

```
modinfo i915
```

---

