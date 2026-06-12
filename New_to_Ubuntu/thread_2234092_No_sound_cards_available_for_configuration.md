---
title: "No sound cards available for configuration"
date: 2014-07-12
forum: New to Ubuntu
---

### Post by Mina_Dursun on 2014-07-12
Hi I'm new in ubuntu. I have a notebook (Sony-VPCEH3P1E) and I installed kubuntu 14.04 on my notebook. At the beginning everything is okay, but for three days there is no sound. 
Here is my outputs:
```
~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce 410M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
07:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0d:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

```
```
~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
        Subsystem: Sony Corporation Device 908b
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d5300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
--
01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
        Subsystem: Sony Corporation Device 908b
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at d3000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


07:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Foxconn International, Inc. Device e037
```

And also when I was trying to reinstall alsa, it's okay but when I run this command "sudo alsa force-reload" I get this output:
```
~$ sudo alsa force-reload
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

~$ aplay -l
aplay: device_list:268: no soundcard found...

```

and etc.

I am getting crazy. What should I do? Please help me..

Note: Is my sound card supported by the Ubuntu sound system?  Here is the link [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) but I couldn't found mine...

---

### Post by alias2234 on 2014-07-13
You say "At the beginning everything is okay, but for three days there is no sound. ..."
Do you mean that you had sound in the beginning and that the sound has dissepaerd ?

if I run aplay -l I get this:
```
phil@1015PE:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I found this, maybe that helps you:
[http://helpdesk.objects.com.au/linux/no-sound-in-ubuntu-on-sony-vaio](http://helpdesk.objects.com.au/linux/no-sound-in-ubuntu-on-sony-vaio)

---

### Post by alias2234 on 2014-07-13
[URL="https://help.ubuntu.com/community/SoundTroubleshooting"]https://help.ubuntu.com/community/SoundTroubleshooting

[/URL][https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=2166214](http://ubuntuforums.org/showthread.php?t=2166214)

---

