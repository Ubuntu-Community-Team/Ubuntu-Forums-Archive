---
title: "Required kernel toshiba support not enabled"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by tonyk9495 on 2013-08-29
[COLOR=#000000]I am trying desperately to make Ubuntu work on my laptop. I want to use windows as little as possible. The fan on my Toshiba laptop never comes on. Once I get into processor heavy stuff my laptop overheats and shuts itself off. I have look at a bunch of old forums but all the links are broken or [/COLOR] not detailed enough[COLOR=#000000]. i have tryed other forums and it still will not come on. i have tried the terminal command also and it gave me the issue  "[/COLOR]Required kernel toshiba support not enabled". i have also look on forums for that issue and the same problem links are broken or not detailed enough.

---

### Post by cariboo on 2013-08-30
The graphics driver should control the fan, what graphics chipset does your system use?

---

### Post by Pako Pako on 2013-08-30
I use a few Toshiba laptops, all pre-2005, and all have at least one fan NOT attached to the motherboard -- it really is just a stand-alone with a heat-sensor. But they should have something that works with ACPItool.
```
acpitool -F 1
```
Out of curiosity, which model(s) notebook PC do you have? (Portege S809, Satellite 430, Tecra M7, etc.)
It really shouldn't get so hot it shuts itself off. It's not a 90's DELL.

---

### Post by tonyk9495 on 2013-08-31
> **Pako Pako said:**
> I use a few Toshiba laptops, all pre-2005, and all have at least one fan NOT attached to the motherboard -- it really is just a stand-alone with a heat-sensor. But they should have something that works with ACPItool.
```
acpitool -F 1
```
Out of curiosity, which model(s) notebook PC do you have? (Portege S809, Satellite 430, Tecra M7, etc.)
It really shouldn't get so hot it shuts itself off. It's not a 90's DELL.

[http://forums.linuxmint.com/viewtopic.php?f=90&t=143755](http://forums.linuxmint.com/viewtopic.php?f=90&t=143755) has more information of the problem i have been having my user on it is DarkAbyss. 
[INDENT]-Computer-
Processor     : 2x AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57
Memory     : 1934MB (534MB used)
Operating System     : Linux Mint 14 Nadia
User Name     : janet (Janet)
Date/Time     : Fri 30 Aug 2013 01:37:58 PM EDT
-Display-
Resolution     : 1280x800 pixels
OpenGL Renderer     : Gallium 0.4 on ATI RS690
X11 Vendor     : The X.Org Foundation
-Multimedia-
Audio Adapter     : HDA-Intel - HDA ATI SB
-Input Devices-
Lid Switch
Power Button
Power Button
AT Translated Set 2 keyboard
Toshiba input device
Video Bus
PS/2 Mouse
AlpsPS/2 ALPS GlidePoint
HDA ATI SB Mic
HDA ATI SB Front Headphone 

-Cooling Fans-
-Temperatures-
Core0 Temp     : 45.00°C
Core0 Temp     : 45.00°C
Core1 Temp     : 45.00°C
Core1 Temp     : 45.00°C
-Voltage Values-

-Loaded Modules-
qcaux
usbserial     : USB Serial Driver core
cdc_acm     : USB Abstract Control Model driver for USB modems and ISDN adapters
bnep     : Bluetooth BNEP ver 1.3
rfcomm     : Bluetooth RFCOMM ver 1.11
parport_pc     : PC-style parallel port driver
bluetooth     : Bluetooth Core ver 2.16
ppdev
arc4     : ARC4 Cipher Algorithm
snd_hda_codec_realtek     : Realtek HD-audio codec
snd_hda_intel     : Intel HDA driver
snd_hda_codec     : HDA codec core
joydev     : Joystick device interfaces
ath5k     : Support for 5xxx series of Atheros 802.11 wireless LAN cards.
ath     : Shared library for Atheros wireless LAN cards.
snd_hwdep     : Hardware dependent layer
snd_pcm     : Midlevel PCM code for ALSA.
mac80211     : IEEE 802.11 subsystem
tifm_7xx1     : TI FlashMedia host driver
tifm_core     : TI FlashMedia core driver
snd_seq_midi     : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi     : Midlevel RawMidi code for ALSA.
snd_seq_midi_event     : MIDI byte &lt;-&gt; sequencer event coder
snd_seq     : Advanced Linux Sound Architecture sequencer.
snd_timer     : ALSA timer interface
cfg80211     : wireless configuration support
snd_seq_device     : ALSA sequencer device management
radeon     : ATI Radeon
pcmcia     : PCMCIA Driver Services
ttm     : TTM memory manager subsystem (for DRM device)
video     : ACPI Video Driver
snd     : Advanced Linux Sound Architecture driver for soundcards.
kvm_amd
kvm
drm_kms_helper     : DRM KMS helper
drm     : DRM shared core routines
lp
soundcore     : Core sound module
snd_page_alloc     : Memory allocator for ALSA system.
sp5100_tco     : TCO timer driver for SP5100 chipset
psmouse     : PS/2 mouse driver
serio_raw     : Raw serio driver
i2c_algo_bit     : I2C-Bus bit-banging algorithm
i2c_piix4     : PIIX4 SMBus driver
yenta_socket
mac_hid
toshiba_acpi     : Toshiba Laptop ACPI Extras Driver
sparse_keymap     : Generic support for sparse keymaps
pcmcia_rsrc
pcmcia_core     : Linux Kernel Card Services
shpchp     : Standard Hot Plug PCI Controller Driver
parport
wmi     : ACPI-WMI Mapping Driver
ati_agp
k8temp     : AMD K8 core temperature monitor
binfmt_misc
sdhci_pci     : Secure Digital Host Controller Interface PCI driver
sdhci     : Secure Digital Host Controller Interface core driver
firewire_ohci     : Driver for PCI OHCI IEEE1394 controllers
pata_atiixp     : low-level driver for ATI IXP200/300/400
firewire_core     : Core IEEE1394 transaction logic
crc_itu_t     : CRC ITU-T V.41 calculations
r8169     : RealTek RTL-8169 Gigabit Ethernet driver
[/INDENT]

[COLOR=#333333][FONT=Lucida Grande]My model is toshiba Satellite A215-S5839. Could any of this information help? It's a laptop it turns it self off after about maybe 10 minutes of use.[/FONT][/COLOR]

---

### Post by Pako Pako on 2013-09-03
This... could be a hardware issue?

Does Windows also crash after an hour or so, or just Linux?
Did the suggestion on the Mint forums (to modify the BIOS settings) work out?
Have you tried changing the video drivers? (Between ACPI and proprietary -- whatever specialized AMD/ATi drivers has for its Radeon X1200  line)
Can you control the speed of the CPU? (Get a governor to "on demand" or "powersave" so it won't be revving at maximum speed all the time)

This doesn't sound like just a fan-going-on issue, but rather something is causing a component (usually CPU or video card) to work really extra hard, leading to extra heat, causing shut down.

---

### Post by tonyk9495 on 2013-09-03
> **Pako Pako said:**
> This... could be a hardware issue?

Does Windows also crash after an hour or so, or just Linux?
Did the suggestion on the Mint forums (to modify the BIOS settings) work out?
Have you tried changing the video drivers? (Between ACPI and proprietary -- whatever specialized AMD/ATi drivers has for its Radeon X1200  line)
Can you control the speed of the CPU? (Get a governor to "on demand" or "powersave" so it won't be revving at maximum speed all the time)

This doesn't sound like just a fan-going-on issue, but rather something is causing a component (usually CPU or video card) to work really extra hard, leading to extra heat, causing shut down.

I had someone on the other forum say > "[COLOR=#333333][FONT=Lucida Grande]This is an old post, but updated just this month [/FONT][/COLOR][https://bugs.launchpad.net/ubuntu/+sour ... bug/644898]("https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/644898")
[COLOR=#333333][FONT=Lucida Grande]It is clear that the toshset app has been abandoned and this is one of many sites citing problems with it and the kernel module. But, getting any definitive answers is like trying to nail Jello to the wall [/FONT][/COLOR][IMG]http://forums.linuxmint.com/images/smilies/icon_confused.gif[/IMG]"  And no it doesn't do it with windows. Only linux. i tryed to turn off ACPI and still doesn't work. How would i change the video drivers? i pull up the set of drivers and it lists nothing. I put in the term command and this came up. > janet@Luke ~ $ sudo lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series]
janet@Luke ~ $ sudo lsmod | grep radeon
radeon                820703  2 
ttm                    75534  1 radeon
drm_kms_helper         45271  1 radeon
drm                   230463  4 radeon,tt

---

### Post by Mark Phelps on 2013-09-04
You can't change video drivers.  AMD dropped restricted Linux driver support for the X1200-series years ago.

---

### Post by Pako Pako on 2013-09-04
> **Mark Phelps said:**
> You can't change video drivers.  AMD dropped restricted Linux driver support for the X1200-series years ago.

Oh. Crap. Uhm. Is it possible to use the old drivers, the last ones they put out?

---

### Post by Bucky Ball on 2013-09-04
Are you using a current and supported version of Ubuntu? I don't see which release you are using. Sorry if I missed that.

PS: Hmm. Just spotted Linux Mint 14. Have you also tried the Mint forums?

---

