---
title: "Touchpad not working"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by john_smith2 on 2013-10-23
My laptop's touchpad is not working. Usng Ubuntu Studio 12.04 64 bit

```
BIOS Information
    Vendor: Acer
    Version: V1.05
    Release Date: 08/24/2010
    ROM Size: 1536 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        8042 keyboard services are supported (int 9h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 5.240
```

---

### Post by varunendra on 2013-10-24
Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
uname -mr
lsb_release -d
xinput
lsmod | egrep 'hid|mouse|wmi'
cat /proc/bus/input/devices
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by john_smith2 on 2013-10-25
```
john@john-Aspire-5742:~$ uname -mr
3.2.0-54-lowlatency x86_64
john@john-Aspire-5742:~$ lsb_release -d
Description:    Ubuntu 12.04.3 LTS
john@john-Aspire-5742:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Genius 2.4G Wireless Mouse                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; 1.3M WebCam                                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=14    [slave  keyboard (3)]
john@john-Aspire-5742:~$ lsmod | egrep 'hid|mouse|wmi'
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                97519  0 
snd                    78957  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
mxm_wmi                13021  0 
wmi                    19256  2 acer_wmi,mxm_wmi
mac_hid                13253  0 
usbhid                 47238  0 
hid                    99636  1 usbhid
john@john-Aspire-5742:~$ cat /proc/bus/input/devices
```

---

### Post by varunendra on 2013-10-25
No output from "cat /proc/bus/input/devices" ?? Please post it back too. Along with it, please also post the output of -
```
find -L /sys/module/{psmouse,acer_wmi,mxm_wmi,mac_hid,usbhid}/ -maxdepth 7 -name name -printf %p\\t -exec cat "{}" \; 2>/dev/null
```

And in the meanwhile, please try these two -
```
xinput float "SynPS/2 Synaptics TouchPad"
xinput reattach "SynPS/2 Synaptics TouchPad" "Virtual core pointer"
```

Does it activate the touchpad? If not, then -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```

If they help, let me know. If not, the above asked outputs may help looking further.

---

### Post by john_smith2 on 2013-10-25
```
john@john-Aspire-5742:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

These don't work

And in the meanwhile, please try these two -
     Code:
     xinput float "SynPS/2 Synaptics TouchPad"
xinput reattach "SynPS/2 Synaptics TouchPad" "Virtual core pointer" 
Does it activate the touchpad? If not, then -
     Code:
     sudo modprobe -rv psmouse
sudo modprobe -v psmouse 
If they help, let me know. If not, the above asked outputs may help looking further.

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=10000 c020000000000 0 0 700f02000003 3803078f830f401 febfffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=0458 Product=00e3 Version=0100
N: Name="Genius 2.4G Wireless Mouse"
P: Phys=usb-0000:00:1d.0-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
U: Uniq=
H: Handlers=kbd mouse0 event5 
B: PROP=0
B: EV=2001f
B: KEY=4837fff072ff32d bf54444600000000 70001 20f908b17c000 677bfad941dfed 9ed68000004400 10000002
B: REL=1c3
B: ABS=100000000
B: MSC=10
B: LED=80

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=rfkill kbd event6 
B: PROP=0
B: EV=13
B: KEY=1600800000c00 8000000000300000 0 0
B: MSC=10

I: Bus=0003 Vendor=0402 Product=9665 Version=0009
N: Name="1.3M WebCam"
P: Phys=usb-0000:00:1a.0-1.1/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input12
U: Uniq=
H: Handlers=mouse1 event12 
B: PROP=9
B: EV=b
B: KEY=6420 30000 0 0 0 0
B: ABS=260800011000003
```

These don't work
     
```
Code:
xinput float "SynPS/2 Synaptics TouchPad"
xinput reattach "SynPS/2 Synaptics TouchPad" "Virtual core pointer" 
```
     
```
Code:
sudo modprobe -rv psmouse
sudo modprobe -v psmouse 
```

---

### Post by varunendra on 2013-10-25
It may be using a different driver. Please post the full output of -
```
lsmod
```

**EDIT:**
Also check its status in dconf. Open dconf Editor, and browse to **org > gnome > settings-daemon > peripherals > touchpad**. Make sure "**touchpad-enabled**" checkbox is checked.

---

### Post by john_smith2 on 2013-10-26
```
john@john-Aspire-5742:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
parport_pc             32866  0 
ppdev                  17113  0 
arc4                   12529  2 
snd_hda_intel          33719  2 
snd_hda_codec         123567  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17709  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ums_realtek            18248  0 
snd_seq_midi           13324  0 
bnep                   18281  2 
rfcomm                 47513  0 
bluetooth             179695  10 bnep,rfcomm
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17087  1 videodev
joydev                 17606  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17540  1 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 132388  0 
tg3                   152144  0 
mac80211              519204  1 ath9k
intel_ips              18174  0 
snd                    78957  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  482333  9 
ath9k_common           14053  1 ath9k
soundcore              15091  1 snd
ath9k_hw              411239  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                97519  0 
cfg80211              205774  3 ath9k,mac80211,ath
serio_raw              13211  0 
drm_kms_helper         46978  1 i915
mei                    41616  0 
drm                   241972  5 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
mxm_wmi                13021  0 
video                  19651  1 i915
wmi                    19256  2 acer_wmi,mxm_wmi
mac_hid                13253  0 
lp                     17799  0 
parport                46528  3 parport_pc,ppdev,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
usb_storage            49198  1 ums_realtek
```

Touchpad enabled.

---

### Post by varunendra on 2013-10-26
Couldn't see any other driver that I expected. Please post the outputs of -
```
synclient
```
..and regardless of what the above output says, try this 'twice' -
```
synclient touchpadoff=0
```

If there's no change, please also post the output of -
```
find -L /sys/module/{joydev,psmouse,acer_wmi,mxm_wmi,mac_hid,usbhid}/ -maxdepth 7 -name name -printf %p\\t -exec cat "{}" \; 2>/dev/null
```

**PS:**
This [wiki page]("https://wiki.ubuntu.com/DebuggingTouchpadDetection") seems to offer an in-depth guide for troubleshooting touchpad issues. Although I've never been to it before, but looks like probably won't be able to go beyond what it offers. Might have a solution for you too.

---

### Post by john_smith2 on 2013-10-26
```
synclientjohn@john-Aspire-5742:~$ synclient
Parameter settings:
    LeftEdge                = 1773
    RightEdge               = 5471
    TopEdge                 = 1665
    BottomEdge              = 4829
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 248
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 113
    HorizScrollDelta        = 113
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0353482
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 452
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 28
    VertHysteresis          = 28
    ClickPad                = 0

```

```
john@john-Aspire-5742:~$ find -L /sys/module/{joydev,psmouse,acer_wmi,mxm_wmi,mac_hid,usbhid}/ -maxdepth 7 -name name -printf %p\\t -exec cat "{}" \; 2>/dev/null
/sys/module/psmouse/drivers/serio:psmouse/serio1/input/input12/name    SynPS/2 Synaptics TouchPad
/sys/module/acer_wmi/drivers/platform:acer-wmi/acer-wmi/rfkill/rfkill0/name    acer-wireless
/sys/module/acer_wmi/drivers/platform:acer-wmi/acer-wmi/rfkill/rfkill1/name    acer-bluetooth
/sys/module/usbhid/drivers/usb:usbhid/2-1.2:1.0/input/input5/name    Genius 2.4G Wireless Mouse

```

---

### Post by varunendra on 2013-10-27
Hmm.. all the outputs so far look as they should be, no problem nowhere.

You might have already tried this, but if not, please try -
```
sudo modprobe -rv psmouse
[s]sudo modprobe -v proto=imps[/s]
sudo modprobe -v psmouse proto=imps
```

If still the same, please post the outputs of (the last places I can currently think of that may contain a hint) -
```
grep -R [[:alnum:]] /sys/module/psmouse/parameters
grep -i touchpad /var/log/Xorg.{failsafe,0}.log
```

---

### Post by john_smith2 on 2013-10-27
```
john@john-Aspire-5742:~$ sudo modprobe -v proto=imps
FATAL: Module proto=imps not found.

```

```
john@john-Aspire-5742:~$ grep -R [[:alnum:]] /sys/module/psmouse/parameters
grep: /sys/module/psmouse/parameters: No such file or directory
john@john-Aspire-5742:~$ grep -i touchpad /var/log/Xorg.{failsafe,0}.log
grep: /var/log/Xorg.failsafe.log: No such file or directory
/var/log/Xorg.0.log:[    25.526] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
/var/log/Xorg.0.log:[    25.526] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
/var/log/Xorg.0.log:[    25.526] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
/var/log/Xorg.0.log:[    25.527] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
/var/log/Xorg.0.log:[    25.527] (**) SynPS/2 Synaptics TouchPad: always reports core events
/var/log/Xorg.0.log:[    25.549] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
/var/log/Xorg.0.log:[    25.549] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5772
/var/log/Xorg.0.log:[    25.549] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5086
/var/log/Xorg.0.log:[    25.549] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
/var/log/Xorg.0.log:[    25.549] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
/var/log/Xorg.0.log:[    25.549] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
/var/log/Xorg.0.log:[    25.549] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
/var/log/Xorg.0.log:[    25.549] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
/var/log/Xorg.0.log:[    25.549] (**) SynPS/2 Synaptics TouchPad: always reports core events
/var/log/Xorg.0.log:[    25.593] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
/var/log/Xorg.0.log:[    25.593] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
/var/log/Xorg.0.log:[    25.593] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
/var/log/Xorg.0.log:[    25.593] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.035
/var/log/Xorg.0.log:[    25.593] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
/var/log/Xorg.0.log:[    25.593] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
/var/log/Xorg.0.log:[    25.593] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
/var/log/Xorg.0.log:[    25.593] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
/var/log/Xorg.0.log:[    25.593] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
/var/log/Xorg.0.log:[    25.593] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
/var/log/Xorg.0.log:[    25.593] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
/var/log/Xorg.0.log:[   514.903] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
/var/log/Xorg.0.log:[  1375.630] SynPS/2 Synaptics TouchPad: Read error No such device
/var/log/Xorg.0.log:[  1375.630] (II) config/udev: removing device SynPS/2 Synaptics TouchPad

```

---

### Post by varunendra on 2013-10-27
> **john_smith2 said:**
> ```
john@john-Aspire-5742:~$ sudo modprobe -v proto=imps
FATAL: **[COLOR="#FF0000"]Module proto=imps[/COLOR]** not found.

```#-o

Slip of mind again.., forgot "psmouse". The commands should be -

```
sudo modprobe -rv psmouse
sudo modprobe -v **psmouse** proto=imps
```

Please try that while I take a look at the logs you posted.

**EDIT:**
And please post back the output of -
```
grep -R [[:alnum:]] /sys/module/psmouse/parameters
```
again, after running the corrected command. There was no output because the module psmouse was removed, but not loaded again (thanks to my award-winning typos).

---

### Post by john_smith2 on 2013-10-28
```
john@john-Aspire-5742:~$ sudo modprobe -v psmouse proto=imps
insmod /lib/modules/3.2.0-54-lowlatency/kernel/drivers/input/mouse/psmouse.ko proto=imps
```

```

john@john-Aspire-5742:~$ grep -R [[:alnum:]] /sys/module/psmouse/parameters
/sys/module/psmouse/parameters/resync_time:0
/sys/module/psmouse/parameters/resetafter:5
/sys/module/psmouse/parameters/smartscroll:Y
/sys/module/psmouse/parameters/rate:100
/sys/module/psmouse/parameters/resolution:200
/sys/module/psmouse/parameters/proto:ImPS/2
/sys/module/psmouse/parameters/cy_read_timeout:200
/sys/module/psmouse/parameters/cy_debug:0

```

---

### Post by john_smith2 on 2014-01-02
Now on Ubuntu 13.10 64 BIT .Re did all the things you said me to do code below Touchpad still not working despite being enabled.

uname -mr
```
john@john-Aspire-5742:~$ uname -mr
3.11.0-14-generic x86_64
```

lsb_release -d
```
john@john-Aspire-5742:~$ lsb_release -d
Description:    Ubuntu 13.10
```

xinput
```
john@john-Aspire-5742:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Genius 2.4G Wireless Mouse                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; 1.3M WebCam                                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=14    [slave  keyboard (3)]
```

lsmod | egrep 'hid|mouse|wmi'
```
john@john-Aspire-5742:~$ lsmod | egrep 'hid|mouse|wmi'
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
psmouse                97626  0 
snd                    69141  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mac_hid                13205  0 
hid_generic            12548  0 
usbhid                 53014  0 
hid                   105818  2 hid_generic,usbhid
mxm_wmi                13021  0 
wmi                    19070  2 acer_wmi,mxm_wmi
video                  19318  2 i915,acer_wmi
```

cat /proc/bus/input/devices
```
john@john-Aspire-5742:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=10000 c020000000000 0 0 700f02000003 3803078f830f401 febfffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=0458 Product=00e3 Version=0100
N: Name="Genius 2.4G Wireless Mouse"
P: Phys=usb-0000:00:1d.0-1.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input5
U: Uniq=
H: Handlers=kbd mouse0 event5 
B: PROP=0
B: EV=2001f
B: KEY=4837fff072ff32d bf54444600000000 70001 20f908b17c000 677bfad941dfed 9ed68000004400 10000002
B: REL=1c3
B: ABS=100000000
B: MSC=10
B: LED=80

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel MID HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input7
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel MID Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel MID Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0003 Vendor=0402 Product=9665 Version=0009
N: Name="1.3M WebCam"
P: Phys=usb-0000:00:1a.0-1.1/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input11
U: Uniq=
H: Handlers=mouse1 event11 
B: PROP=9
B: EV=b
B: KEY=6420 30000 0 0 0 0
B: ABS=260800011000003

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input12
U: Uniq=
H: Handlers=rfkill kbd event12 
B: PROP=0
B: EV=13
B: KEY=1c0000 0 0 0 0 1600800000c00 300000 0 0
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Acer BMA150 accelerometer"
P: Phys=wmi/input1
S: Sysfs=/devices/virtual/input/input13
U: Uniq=
H: Handlers=event13 js0 
B: PROP=0
B: EV=9

B: ABS=7
```

find -L /sys/module/{psmouse,acer_wmi,mxm_wmi,mac_hid,usbhid}/ -maxdepth 7 -name name -printf %p\\t -exec cat "{}" \; 2>/dev/null

```
john@john-Aspire-5742:~$ find -L /sys/module/{psmouse,acer_wmi,mxm_wmi,mac_hid,usbhid}/ -maxdepth 7 -name name -printf %p\\t -exec cat "{}" \; 2>/dev/null
/sys/module/psmouse/drivers/serio:psmouse/serio1/input/input11/name    SynPS/2 Synaptics TouchPad
/sys/module/acer_wmi/drivers/platform:acer-wmi/acer-wmi/subsystem/devices/coretemp.0/name    coretemp
/sys/module/acer_wmi/drivers/platform:acer-wmi/acer-wmi/rfkill/rfkill1/name    acer-wireless
/sys/module/acer_wmi/drivers/platform:acer-wmi/acer-wmi/rfkill/rfkill2/name    acer-bluetooth
/sys/module/usbhid/drivers/usb:usbhid/2-1.1:1.0/input/input5/name    Genius 2.4G Wireless Mouse
```

xinput float "SynPS/2 Synaptics TouchPad"
```
john@john-Aspire-5742:~$ xinput float "SynPS/2 Synaptics TouchPad"
```

xinput reattach "SynPS/2 Synaptics TouchPad" "Virtual core pointer"
```
john@john-Aspire-5742:~$ xinput reattach "SynPS/2 Synaptics TouchPad" "Virtual core pointer"
```

 sudo modprobe -rv psmouse
```
john@john-Aspire-5742:~$ sudo modprobe -rv psmouse
[sudo] password for john: 
rmmod psmouse
```

 sudo modprobe -v psmouse
```
john@john-Aspire-5742:~$ sudo modprobe -v psmouse
insmod /lib/modules/3.11.0-14-generic/kernel/drivers/input/mouse/psmouse.ko
``` 

lsmod
```
john@john-Aspire-5742:~$ lsmod
Module                  Size  Used by
psmouse                97626  0 
btusb                  28267  0 
ath3k                  13318  0 
parport_pc             32701  0 
ppdev                  17671  0 
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
bnep                   19564  2 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
joydev                 17377  0 
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
rfcomm                 69070  12 
bluetooth             371880  23 bnep,ath3k,btusb,rfcomm
binfmt_misc            17468  1 
arc4                   12608  2 
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_realtek    55704  1 
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
ath9k                 151173  0 
ath9k_common           13859  1 ath9k
microcode              23518  0 
ath9k_hw              444645  2 ath9k_common,ath9k
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              596969  1 ath9k
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
serio_raw              13413  0 
intel_ips              18470  0 
lpc_ich                21080  0 
cfg80211              479757  3 ath,ath9k,mac80211
snd                    69141  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
mei_me                 18421  0 
mei                    77692  1 mei_me
ext2                   72832  1 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
mac_hid                13205  0 
xts                    12885  1 
gf128mul               14951  1 xts
dm_crypt               22728  2 
hid_generic            12548  0 
usbhid                 53014  0 
hid                   105818  2 hid_generic,usbhid
ums_realtek            18029  0 
usb_storage            62062  1 ums_realtek
i915                  655752  9 
i2c_algo_bit           13413  1 i915
drm_kms_helper         52651  1 i915
tg3                   162230  0 
drm                   296739  5 i915,drm_kms_helper
ptp                    18580  1 tg3
pps_core               19027  1 ptp
ahci                   25819  2 
libahci                31898  1 ahci
mxm_wmi                13021  0 
wmi                    19070  2 acer_wmi,mxm_wmi
video                  19318  2 i915,acer_wmi
```

synclient
```
john@john-Aspire-5742:~$ synclient
Parameter settings:
    LeftEdge                = 1773
    RightEdge               = 5471
    TopEdge                 = 1665
    BottomEdge              = 4829
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 248
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 113
    HorizScrollDelta        = 113
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0353482
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 28
    VertHysteresis          = 28
    ClickPad                = 0
```

synclient touchpadoff=0
```
john@john-Aspire-5742:~$ synclient touchpadoff=0
```

find -L /sys/module/{joydev,psmouse,acer_wmi,mxm_wmi,mac_hid,usbhid}/  -maxdepth 7 -name name -printf %p\\t -exec cat "{}" \; 2>/dev/null
```
john@john-Aspire-5742:~$ find -L /sys/module/{joydev,psmouse,acer_wmi,mxm_wmi,mac_hid,usbhid}/ -maxdepth 7 -name name -printf %p\\t -exec cat "{}" \; 2>/dev/null
/sys/module/psmouse/drivers/serio:psmouse/serio1/input/input14/name    SynPS/2 Synaptics TouchPad
/sys/module/acer_wmi/drivers/platform:acer-wmi/acer-wmi/subsystem/devices/coretemp.0/name    coretemp
/sys/module/acer_wmi/drivers/platform:acer-wmi/acer-wmi/rfkill/rfkill1/name    acer-wireless
/sys/module/acer_wmi/drivers/platform:acer-wmi/acer-wmi/rfkill/rfkill2/name    acer-bluetooth
/sys/module/usbhid/drivers/usb:usbhid/2-1.1:1.0/input/input5/name    Genius 2.4G Wireless Mouse
```

sudo modprobe -rv psmouse
```
john@john-Aspire-5742:~$ sudo modprobe -rv psmouse
rmmod psmouse
```

sudo modprobe -v psmouse proto=imps
```
john@john-Aspire-5742:~$ sudo modprobe -v psmouse proto=imps
insmod /lib/modules/3.11.0-14-generic/kernel/drivers/input/mouse/psmouse.ko proto=imps
```

grep -R [[:alnum:]] /sys/module/psmouse/parameters
```
john@john-Aspire-5742:~$ grep -R [[:alnum:]] /sys/module/psmouse/parameters
/sys/module/psmouse/parameters/resolution:200
/sys/module/psmouse/parameters/rate:100
/sys/module/psmouse/parameters/resync_time:0
/sys/module/psmouse/parameters/proto:ImPS/2
/sys/module/psmouse/parameters/smartscroll:Y
/sys/module/psmouse/parameters/resetafter:5
```

---

### Post by chkneater on 2014-01-02
did you check blacklist.conf to see if it was blacklisted?

---

### Post by varunendra on 2014-01-03
And does the **var/log/Xorg.0.log** file still show these errors? -
> **john_smith2 said:**
> ```

/var/log/Xorg.0.log:[    25.593] (**) SynPS/2 Synaptics TouchPad: [COLOR="#FF0000"]Ignoring device from InputClass "touchpad ignore duplicates"[/COLOR]
/var/log/Xorg.0.log:[   514.903] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
/var/log/Xorg.0.log:[  1375.630] [COLOR="#FF0000"]SynPS/2 Synaptics TouchPad: Read error No such device[/COLOR]
/var/log/Xorg.0.log:[  1375.630] (II) [COLOR="#FF0000"]config/udev: removing device SynPS/2 Synaptics TouchPad[/COLOR]

```

---

### Post by SWGraphics291 on 2014-01-03
Have you installed anything recently? (Programs can sometimes have an effect on the touch pad)

---

### Post by john_smith2 on 2014-01-03
> **SWGraphics291 said:**
> Have you installed anything recently? (Programs can sometimes have an effect on the touch pad)

Its a clean install of ubuntu 13.10

grep -i touchpad /var/log/Xorg.{failsafe,0}.log

```
john@john-Aspire-5742:~$ grep -i touchpad /var/log/Xorg.{failsafe,0}.log
grep: /var/log/Xorg.failsafe.log: No such file or directory
/var/log/Xorg.0.log:[    74.647] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event13)
/var/log/Xorg.0.log:[    74.647] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
/var/log/Xorg.0.log:[    74.647] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
/var/log/Xorg.0.log:[    74.647] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
/var/log/Xorg.0.log:[    74.648] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
/var/log/Xorg.0.log:[    74.648] (**) SynPS/2 Synaptics TouchPad: always reports core events
/var/log/Xorg.0.log:[    74.692] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
/var/log/Xorg.0.log:[    74.692] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5772 (res 69)
/var/log/Xorg.0.log:[    74.692] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5086 (res 118)
/var/log/Xorg.0.log:[    74.692] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
/var/log/Xorg.0.log:[    74.692] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
/var/log/Xorg.0.log:[    74.692] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
/var/log/Xorg.0.log:[    74.692] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
/var/log/Xorg.0.log:[    74.692] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
/var/log/Xorg.0.log:[    74.692] (**) SynPS/2 Synaptics TouchPad: always reports core events
/var/log/Xorg.0.log:[    74.716] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
/var/log/Xorg.0.log:[    74.716] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
/var/log/Xorg.0.log:[    74.716] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
/var/log/Xorg.0.log:[    74.716] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
/var/log/Xorg.0.log:[    74.716] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
/var/log/Xorg.0.log:[    74.716] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
/var/log/Xorg.0.log:[    74.716] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
/var/log/Xorg.0.log:[    74.716] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
/var/log/Xorg.0.log:[    74.716] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
/var/log/Xorg.0.log:[    74.716] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
/var/log/Xorg.0.log:[    74.716] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
```

---

### Post by SWGraphics291 on 2014-01-03
What about trying Fn+F7. It might be a different button for you though (check the symbols). Common mistake.

---

### Post by john_smith2 on 2014-01-04
> **SWGraphics291 said:**
> What about trying Fn+F7. It might be a different button for you though (check the symbols). Common mistake.

That fixed it but why?

---

### Post by varunendra on 2014-01-04
Wow ! What a case that was, thanks a lot for the precious input SWGraphics291 !
> That fixed it but why?
That combination acts as a hardware level switch to toggle the touchpad on/off, hence why. :)

*[Note to myself : Never ignore the obvious]*

---

### Post by SWGraphics291 on 2014-01-05
Fn+F7 is the way to disable the touchpad on laptops. You could of accidentally pressed Fn+F7. It could be something else that made it happen though, so don't blame it all on yourself.

If this happens again just try FN=F7 before going on the forums. LOL

---

