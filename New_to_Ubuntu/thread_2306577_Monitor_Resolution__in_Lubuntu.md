---
title: "Monitor Resolution  in Lubuntu"
date: 2015-12-16
forum: New to Ubuntu
---

### Post by angelo16 on 2015-12-16
I tried everything I could find on Google, but without success.

I installed Lubuntu and my monitor has native resolution of 1680x1050. 

In a terminal window,I can set that resolution after rebooting the machine, but for some reason if I turn the computer off today, tomorrow it returns to 1024x768 resolution.
It seems that on the latest Lubuntu version the configuration files are not in the same place as before or it does not use them anymore.

Can someone help me to make the 1680x1050 resolution permanent in the lastest Lubuntu version  ?

---

### Post by sandyd on 2015-12-16
Hi, could you post the output of the following commands:

```

lspci
lsmod
xrandr -q
```

This will allow us to determine what video card you have, what video drivers you have loaded, and what resolutions the computer thinks you can run at.

---

### Post by angelo16 on 2015-12-17
```
l1410@l1410:~$ lspci
00:00.0 RAM memory: NVIDIA Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: NVIDIA Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP67 SMBus (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB controller: NVIDIA Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB controller: NVIDIA Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: NVIDIA Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: NVIDIA Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: NVIDIA Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: NVIDIA Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: NVIDIA Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: NVIDIA Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: NVIDIA Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: NVIDIA Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: NVIDIA Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
```

```
l1410@l1410:~$ lsmod
Module                  Size  Used by
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci
vmw_vsock_vmci_transport    28672  0
vsock                  36864  1 vmw_vsock_vmci_transport
vmw_vmci               65536  1 vmw_vsock_vmci_transport
snd_hda_codec_hdmi     49152  1
asix                   40960  0
pl2303                 20480  0
usbnet                 40960  1 asix
usbserial              53248  1 pl2303
mii                    16384  2 asix,usbnet
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
kvm_amd                65536  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
kvm                   512000  1 kvm_amd
snd_timer              32768  2 snd_pcm,snd_seq
input_leds             16384  0
edac_core              53248  0
edac_mce_amd           24576  0
serio_raw              16384  0
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
k8temp                 16384  0
8250_fintek            16384  0
soundcore              16384  1 snd
shpchp                 36864  0
i2c_nforce2            16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
pata_acpi              16384  0
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
nouveau              1388544  5
mxm_wmi                16384  1 nouveau
video                  36864  1 nouveau
i2c_algo_bit           16384  1 nouveau
ttm                    94208  1 nouveau
drm_kms_helper        126976  1 nouveau
firewire_ohci          40960  0
drm                   356352  8 ttm,drm_kms_helper,nouveau
ahci                   36864  2
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core
libahci                32768  1 ahci
forcedeth              69632  0
pata_amd               20480  0
floppy                 73728  0
wmi                    20480  2 mxm_wmi,nouveau
```

```
l1410@l1410:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080     60.00 +
   1680x1050     59.95  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1280x800      59.81  
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       60.00    59.94  
HDMI-1 disconnected (normal left inverted right x axis y axis)
TV-1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by timotheus3 on 2016-01-14
try installing xdiagnose 
```
sudo apt-get install xdiagnose
```
i had problems with my video driver not loading properly and by ticking the 'disable bootloader graphics' box under 'workarounds' fixed this problem, or try seeing if any of the other workarounds change anything.. possibly a quickfix, i would recommend looking further into it though

---

### Post by mörgæs on 2016-01-14
Nvidia 6xxx and 7xxx often work better with closed-source drivers. Have you tried that?

---

