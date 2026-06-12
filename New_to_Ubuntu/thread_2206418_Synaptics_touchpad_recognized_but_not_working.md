---
title: "Synaptics touchpad recognized but not working"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by tylerberg45 on 2014-02-19
I tried following other tutorials on making my touchpad work but have been unable to transfer the correct commands in my computer. Probably because i'm unaware of why it isn't working completely. I read something about blacklisting a module of some sort but haven't been able to figure it out. I could use some help as I am new to linux (: thanks

---

### Post by varunendra on 2014-02-19
Hello tylerberg45, Welcome to Ubuntu Forums!

Posting in response to your PM although I'm not an expert in such issues. The **[thread]("http://ubuntuforums.org/showthread.php?t=2176544")** that you mentioned, did you try the suggested "xinput" or "modprobe.." commands (in post #6 and #8)? Please post in detail whatever you have tried so far, with links to the posts/guides if you have them.

Along with the description, please also post the output of the following commands -
```
xinput
cat /proc/bus/input/devices
lsmod
grep -i touchpad /var/log/Xorg.0.log
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

**PS:**
I'm facing serious connectivity problem (again..) so may or may not be able to reply back soon.
For reference for **others who may possibly help**, installing/reinstalling ***xserver-xorg-input-synaptic*** package also seems to help, as verified in this post : [http://ubuntuforums.org/showthread.php?t=2205291](http://ubuntuforums.org/showthread.php?t=2205291)

---

### Post by tylerberg45 on 2014-02-19
I have tried installing synaptiks, making sure that touchpad is enabled in the system settings, and making sure my function toggle combination of fn + f5 isn't stopping it from working. I did try the steps in post 6 but couldn't figure out what information i needed to substitute for post number 8. for people besides varunendra. we are refuring to [http://ubuntuforums.org/showthread.php?t=2176544](http://ubuntuforums.org/showthread.php?t=2176544)
```
xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:101b    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD                     id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Toshiba input device           

```
```
cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Toshiba input device"
P: Phys=toshiba_acpi/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=rfkill kbd event4 
B: PROP=0
B: EV=13
B: KEY=40000 10000 1c00000000 0 0 1501f00002000 3809604001 2000000000000 0
B: MSC=10

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=660800011000003

I: Bus=0003 Vendor=04f2 Product=b307 Version=6030
N: Name="TOSHIBA Web Camera - HD"
P: Phys=usb-0000:00:1a.0-1.4/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0003 Vendor=046d Product=c52b Version=0111
N: Name="Logitech Unifying Device. Wireless PID:101b"
P: Phys=usb-0000:00:14.0-1:1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.2/0003:046D:C52B.0003/input/input11
U: Uniq=
H: Handlers=mouse1 event11 
B: PROP=0
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=143
B: MSC=10


```
```
lsmod
Module                  Size  Used by
ums_realtek            18029  0 
usb_storage            62062  1 ums_realtek
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19704  2 
rfcomm                 69130  0 
bluetooth             372041  10 bnep,rfcomm
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431720  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_realtek    56405  1 
joydev                 17377  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
arc4                   12608  2 
iwldvm                237391  0 
mac80211              597268  1 iwldvm
snd_hda_intel          52267  6 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
i915                  661339  3 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
toshiba_acpi           22901  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
iwlwifi               165636  1 iwldvm
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
microcode              23656  0 
sparse_keymap          13948  1 toshiba_acpi
snd_timer              29433  2 snd_pcm,snd_seq
wmi                    19070  1 toshiba_acpi
drm_kms_helper         52710  1 i915
cfg80211              480503  3 iwlwifi,mac80211,iwldvm
drm                   297056  4 i915,drm_kms_helper
psmouse                97655  0 
snd                    69141  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
mei_me                 18421  0 
i2c_algo_bit           13413  1 i915
lpc_ich                21080  0 
mei                    77782  1 mei_me
mac_hid                13205  0 
serio_raw              13413  0 
video                  19318  1 i915
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_logitech_dj        18581  0 
usbhid                 53014  0 
hid                   101762  3 usbhid,hid_logitech_dj
ahci                   25819  3 
r8169                  67581  0 
libahci                32009  1 ahci
mii                    13934  1 r8169


```
```
 grep -i touchpad /var/log/Xorg.0.log
[    23.640] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    23.640] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    23.640] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    23.640] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    23.709] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    23.709] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    23.764] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    23.764] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5680 (res 46)
[    23.764] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4728 (res 62)
[    23.764] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    23.764] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    23.764] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    23.764] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    23.764] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    23.764] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    23.804] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    23.804] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    23.804] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    23.804] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[    23.804] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    23.804] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    23.804] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    23.804] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    23.804] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    23.804] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    23.804] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"


```

---

### Post by varunendra on 2014-02-20
> **tylerberg45 said:**
> 
```
xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   **&#8627; SynPS/2 Synaptics TouchPad                  id=11**    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:101b    id=13    [slave  pointer  (2)]

```
Please try -
```
xinput float "SynPS/2 Synaptics TouchPad"
xinput reattach "SynPS/2 Synaptics TouchPad" "Virtual core pointer"
```

If the above doesn't help, try reloading the driver -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```

If the above also fails, try the same with a parameter -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=imps
```

If you have already tried installing the xserver-xorg-xinput-synaptic driver (after "Updating" the system), then I am out of ideas after this.
Have you tried a live CD/DVD of an alternate version? That is, 13.10 if you have 12.04 installed, or vice-versa.

---

