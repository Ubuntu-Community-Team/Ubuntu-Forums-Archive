---
title: "Use two monitors"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by dlw on 2013-01-15
Want to use two moniors with different screens.
Settings in display say setting must be 2048 square.
Meaning 1024 x *, I guess.
Also, suggest starting Ubuntu in 2d.

How is Ubuntu started in 2d?

dlw

---

### Post by dannyboy79 on 2013-01-15
do you have auto-login set or do you need to enter your username and password to log into your system? If you do NOT have auto-login, then click on options where you enter your password, and it should open a session manager box, choose Ubuntu 2D or whatever it's called, it definitely has 2D in the title.

if you have auto-login set, read this: [http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins](http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins)

What graphics card do you have? You may be able to install a better driver to get better capabilties from your graphics card. You can find out by issuing the following command within a terminal session
```
lspci
```

---

### Post by dlw on 2013-01-16
> **dannyboy79 said:**
> do you have auto-login set or do you need to enter your username and password to log into your system? If you do NOT have auto-login, then click on options where you enter your password, and it should open a session manager box, choose Ubuntu 2D or whatever it's called, it definitely has 2D in the title.

if you have auto-login set, read this: [http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins](http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins)

What graphics card do you have? You may be able to install a better driver to get better capabilties from your graphics card. You can find out by issuing the following command within a terminal session
```
lspci
```

Thank you for replying.

Graphics card is ATI RS482.
lightdm.conf is as follows;
[SeatDefaults]
autologin-guest=false
autologin-user=false
autologin-user-timeout=0
user-session=ubuntu-2d
greeter-session=unity-greeter

Changed from auto login to manual login.
Don't see anyway to set 2d.

Still can't get 2nd monitor working correctly.
Displays the same content as the main monitor.

Any help appreciated.
dlw

---

### Post by QIII on 2013-01-16
The RS482 chipset is associated with the Xpress 200 series GPUs, I believe.  These are no longer supported by AMD's drivers for X Server after about 2008 or early 2009.

How old is this machine?

---

### Post by dannyboy79 on 2013-01-16
the screen where it asks you to enter your password, there is an options pop out menu, if it doesn't say "options" it may just be a logo or something you click on. it's there I know it is.

---

### Post by dlw on 2013-01-17
After studying the screen carefully, I do not find what you say is there.

Here is what is there: Left side.
Don
Box to enter password
Virutal User
Guest
Remote Login

Here is what is in top right corner:
Turn off icon - looks like a little gear.
Time
Speaker
On line icon
Email alert.

Nothing else.

dlw

---

### Post by dlw on 2013-01-23
> **QIII said:**
> The RS482 chipset is associated with the Xpress 200 series GPUs, I believe.  These are no longer supported by AMD's drivers for X Server after about 2008 or early 2009.

How old is this machine?

The machine, an HP dc5750S is roughly 1 1/2 years old.
It is a referbished box so they probably put whatever
grafics card they had in it.

The only setting available to run two monitors is 1024x768.

Any ideas on solving this, and if a new card is required
any suggestions on one. The box requires half/height cards.

TIA
dlw

---

### Post by tgalati4 on 2013-01-23
Because of graphics card or video RAM limitations, you are constrained to a 2048x2048 superdesktop.  Therefore 1024x786 will work when both monitors are set to that.

Can you increase Video RAM in BIOS?  If so, then maximize it.

---

### Post by dlw on 2013-01-23
Video ram size in bios was 'automatic'
Changed to '512'.
Tried to change to several different screens.
Made no difference.
Still at 1024x768 4:3

Any more ideas?

dlw

---

### Post by tgalati4 on 2013-01-24
Try setting colors to 16-bit and reboot.  See if you can exceed the 2048 limitation.

It's possible that the open ati driver is hard-coded to 2048 by 2048 for multiple displays.  You would have to do some research on that.  What video driver are you currently using?

Open a terminal:

```
lsmod
```

---

### Post by dlw on 2013-01-24
[QUOTE=tgalati4;12471728]Try setting colors to 16-bit and reboot.  See if you can exceed the 2048 limitation.

It's possible that the open ati driver is hard-coded to 2048 by 2048 for multiple displays.  You would have to do some research on that.  What video driver are you currently using?

Is changing colors to 16-bit in bios?

Graphics = Gallium 0.4 on ATI RS480

don@don-HP:~$ lsmod
Module                  Size  Used by
hp_wmi                 13617  0 
sparse_keymap          13659  1 hp_wmi
snd_hda_codec_realtek    63496  1 
snd_hda_intel          32516  5 
snd_hda_codec         111548  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         105029  3 
snd_pcm                80235  5 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep              13273  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        24226  1 snd_usb_audio
snd_seq_midi           13133  0 
snd_seq_midi_event     14476  1 snd_seq_midi
snd_rawmidi            25383  2 snd_usbmidi_lib,snd_seq_midi
kvm_amd                54395  0 
kvm                   357807  1 kvm_amd
uvcvideo               71278  0 
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
snd_timer              24412  4 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62146  23 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                84878  0 
joydev                 17162  0 
sp5100_tco             13418  0 
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
i2c_piix4              12984  0 
serio_raw              13032  0 
k8temp                 12843  0 
radeon                820764  4 
ttm                    75535  1 radeon
drm_kms_helper         47304  1 radeon
drm                   238811  6 radeon,ttm,drm_kms_helper
i2c_algo_bit           13198  1 radeon
wmi                    18591  1 hp_wmi
rfcomm                 37277  0 
shpchp                 32190  0 
mac_hid                13038  0 
bnep                   17708  2 
bluetooth             183270  10 rfcomm,bnep
ati_agp                13178  0 
parport_pc             31969  1 
ppdev                  12818  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
binfmt_misc            17261  1 
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
floppy                 55445  0 
pata_atiixp            13000  0 
tg3                   130449  0 
usb_storage            39351  1 
don@don-HP:~$

---

### Post by tgalati4 on 2013-01-24
You are using the *radeon* open source module.  There might be some module switches that can tweak or some magic xorg.conf settings.

16-bit is set in xorg.conf.

```
man radeon
```

Let us know what you tried and if you were able to exceed the 2048 limitation.

---

### Post by dlw on 2013-01-25
I'm thinking about buying the graphics card below.
Will a 240 watt power supply run it?

dlw

[http://graphics-cards.findthebest.com/l/378/ASUS-EAH5450-SILENT-DI-1GD3-V2](http://graphics-cards.findthebest.com/l/378/ASUS-EAH5450-SILENT-DI-1GD3-V2)

---

### Post by tgalati4 on 2013-01-25
You should be OK.  If your machine has random lockups or if the voltages look low in BIOS Health Monitor, then you might change the power supply.  If it is a Bestec power supply, then replace it regardless.

---

### Post by dlw on 2013-01-25
I think that is what I will do.

Thanks for you help,
dlw

---

