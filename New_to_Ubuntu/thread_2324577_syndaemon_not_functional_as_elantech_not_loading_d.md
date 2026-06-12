---
title: "syndaemon not functional as elantech not loading driver"
date: 2016-05-14
forum: New to Ubuntu
---

### Post by yazdzik-k on 2016-05-14
Dear Friends,

there is no way to disable touchpad via syndaemon,  and it may have to do with the modules loaded for the touchpad listed as 12 

```


uname -a
Linux deblap2 4.2.0-36-generic #41-Ubuntu SMP Mon Apr 18 15:49:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux



```

```


&#9121; Virtual core pointer                        id=2    [master pointer  (3)]&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USBest Technology SiS HID Touch Controller    id=10    [slave  pointer  (2)]
&#9116;   &#8627; ELAN1000:00 04F3:0401                       id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                        id=11    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]

```

```

Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
bnep                   20480  2
bbswitch               16384  0
snd_hrtimer            16384  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
joydev                 20480  0
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
btusb                  45056  0
videobuf2_core         49152  1 uvcvideo
btrtl                  16384  1 btusb
v4l2_common            16384  1 videobuf2_core
btbcm                  16384  1 btusb
hid_multitouch         20480  0
btintel                16384  1 btusb
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
bluetooth             516096  9 bnep,btbcm,btrtl,btusb,btintel
media                  24576  2 uvcvideo,videodev
usbhid                 49152  0
hid_generic            16384  0
arc4                   16384  2
asus_nb_wmi            24576  0
i2c_designware_platform    16384  0
asus_wmi               28672  1 asus_nb_wmi
i2c_designware_core    20480  1 i2c_designware_platform
mxm_wmi                16384  0
sparse_keymap          16384  1 asus_wmi
nls_iso8859_1          16384  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
iwlmvm                294912  0
coretemp               16384  0
nvidia               8646656  41
mac80211              745472  1 iwlmvm
kvm_intel             167936  0
snd_hda_intel          36864  3
kvm                   516096  1 kvm_intel
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
iwlwifi               204800  1 iwlmvm
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
crct10dif_pclmul       16384  0
cfg80211              557056  3 iwlwifi,mac80211,iwlmvm
crc32_pclmul           16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
cdc_ether              16384  0
aesni_intel           167936  2
usbnet                 40960  1 cdc_ether
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
snd_seq                69632  3 snd_seq_midi_event,snd_seq_midi
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  3 snd_hrtimer,snd_pcm,snd_seq
input_leds             16384  0
serio_raw              16384  0
r8152                  49152  0
snd                    81920  18 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mii                    16384  2 r8152,usbnet
soundcore              16384  1 snd
idma64                 20480  0
mei_me                 36864  0
virt_dma               16384  1 idma64
processor_thermal_device    16384  0
mei                    98304  1 mei_me
shpchp                 36864  0
intel_lpss_pci         16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
int3403_thermal        16384  0
wmi                    20480  2 mxm_wmi,asus_wmi
intel_lpss_acpi        16384  0
int3402_thermal        16384  0
acpi_pad               20480  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
int340x_thermal_zone    16384  3 int3402_thermal,processor_thermal_device,int3403_thermal
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
tpm_crb                16384  0
mac_hid                16384  0
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
i915                 1134592  3
i2c_algo_bit           16384  1 i915
drm_kms_helper        131072  1 i915
ahci                   36864  0
nvme                   57344  4
drm                   356352  8 i915,drm_kms_helper,nvidia
libahci                32768  1 ahci
i2c_hid                20480  0
hid                   118784  4 i2c_hid,hid_multitouch,hid_generic,usbhid
pinctrl_sunrisepoint    28672  0
video                  40960  2 i915,asus_wmi
pinctrl_intel          20480  1 pinctrl_sunrisepoint


```

there is,  I am sure,  some easy way to repair this,  so the normal syndaemon command would work,  to wit,  using the synaptics input for the touchpad.

obviously,  the gui settings do not even include disable touchpad while typing.  

running 15.10 because everything, except this,  works,  unity because there is as of yet no HIDPI for mate, and 16.04 had dreadful install issue

in the live mate 16.04,  the elan_i2c module loads.  Is there a way to blacklist something in my modules, in my current version,   force the elan  to load,  and enable the disable while typing thing from the gui.

I am dreadfully afraid of upgrading to 16.04,  unless there is a sure-fire way of blacklisting bbswitch,  as that has become in all distros a real issue.

It has taken weeks to get this mission critical laptop working really well, and I would prefer just to be able to upgrade to 16.04 if there would be no issues.

At any rate,  if someone has a solution,  it would be deeply appreciated.

best,

M

---

### Post by yazdzik-k on 2016-05-25
Dear Friends,

Whilst trying not to duplicate [http://ubuntuforums.org/showthread.php?t=2324577](http://ubuntuforums.org/showthread.php?t=2324577),  I still cannot see why I cannot disable touchpad while typing.

This is not a gui issue,  an issue of some arcane module,  but there being insufficient documentation.

simply put:

in trying live versions:

16.04 Unity --  no way
16.04 mate -   disable touchpad while typing works perfectly

I have unity on 15.10 because the system itself,  other than the issue at hand,  and leaving aside all personal preferences,  functions OTOB.

I cannot use Mate at present because of lack of hidpi support.

I do not care about any fancy scrolling or tablet like effects,  whatsoever.  I type.  A lot.

Therefore I need a solution.

I have tried loading elan_i2c at boot,  no effect,  likewise  synaptics_i2c.

Obviously,  no matter what I do,  synclient will not work, as the master driver, as we can see from 

```

  *-usb:2
                   description: Human interface device
                   product: SiS HID Touch Controller
                   vendor: USBest Technology
                   physical id: c
                   bus info: usb@1:c
                   version: 5.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s

```

and 
```

Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USBest Technology SiS HID Touch Controller	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Elan Touchpad                           	id=12	[slave  pointer  (2)]


```

controls access to the touchpad over i2c.

Experimentally, having tired both the 16.04 versions live,  there should be no reason, other than the UI,  why I cannot disable,  via CLI,  touchpad while typing,  except that I do not know how.  And risking having a set of key controls to use xinput disable and enable is insane in the middle of a mission critical document.

Furthermore,  since I do not care at all about modern effects,  I would be happy to use any driver,  since I do not tap, or edge scroll,  or anything other than type,  but,  need the appropriate xorg.conf paramters.

[FONT=Arial]Section "InputClass"[/FONT]
[FONT=Arial]Identifier "Ignore mouse devs"[/FONT]
[FONT=Arial]MatchDevicePath "/dev/input/mouse*"[/FONT]
[FONT=Arial]Option "Ignore" "true"[/FONT]
[FONT=Arial]EndSection[/FONT]

seems a bit drastic,  and would only work if the appropriate drivers were loaded.

If I were certain that the following would work with the synaptic_i2c driver,

then I could add:
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# [http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html](http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html)
      MatchDevicePath "/dev/input/event*"
EndSection6



and

Section "InputClass"
        Identifier "touchpad ignore duplicates"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/mouse*"
        Option "Ignore" "on"
EndSection


I realise this is not the "which button do I click to disable touchpad"  or even simple,  but since it works in one DE,  it is not impossible to make work in all DEs.

I have reams of output,  if anyone wants to look.  None of it seems relevant. 

I hope. ;)

Best,
M

---

### Post by wildmanne39 on 2016-05-25
Please do not post duplicates, it dilutes community effort. Threads merged
After 12 hours you can bump your thread!

---

