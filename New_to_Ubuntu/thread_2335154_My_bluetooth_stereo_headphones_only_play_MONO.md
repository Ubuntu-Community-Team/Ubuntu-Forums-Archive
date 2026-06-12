---
title: "My bluetooth stereo headphones only play MONO"
date: 2016-08-25
forum: New to Ubuntu
---

### Post by kate.t on 2016-08-25
Hi!

I'm new to Linux, so I hope the info I give here will be helpful.

On my last (recently deceased) laptop, I was running Ubuntu 14.04, and  on that system my bluetooth Sony MDR-ZX770BT stereo headphones worked  beautifully.

Now I have a brand new Lenovo G50-70 64-bit notebook with Ubuntu  16.04 preinstalled.

The audio device is Haswell-ULT HD Audio Controller  by Intel.

The headphones work now, but only in mono. When I look at sound settings and check sound there, it tells me the sound is mono. Mono sound is coming through both sides of the headphone. I also think the built-in speakers are putting out mono, the sound is not good at all.

I've installed both blueman and pulseaudio controller. While pulseaudio will allow me to try both modes (headset and a2dp_sink), blueman tells me that only headset mode will work, and the error message I get in blueman is "failed to change profile to a2dp_sink".

I've googled and haven't found anything concerning this specific problem. It doesn't help that I'm ignorant of audio matters! I brought up alsamixer in the terminal, but don't understand what I'm looking at.

I'll be happy to post any logs once I know how to get to them.

Thank you in advance for any help you can give.

Kathleen

---

### Post by #&amp;thj^% on 2016-08-26
What dose the contents of this show
```
gedit /etc/bluetooth/audio.conf
```
Paste back here

---

### Post by kate.t on 2016-08-26
Hello again!

In an effort to be more helpful with my question, I want to tell you what I've tried since my first post.

I figured out how to get to the "sliders" in the Alsamixer program, and set all the sliders to OO (unmuted the ones that were muted). That didn't help.

I also kept googling and found that people with sound problems were often advised to run the alsa-info-script and post the resulting link to [www.alsa-project.org](www.alsa-project.org).

I ran the script and here's the link:

[http://www.alsa-project.org/db/?f=c5ff81a6136a78d8d0cf093d9a542ca7f117abf0](http://www.alsa-project.org/db/?f=c5ff81a6136a78d8d0cf093d9a542ca7f117abf0)

I don't understand the output, but hope this will enable someone to help me!

Thanks again in advance!

Kathleen

---

### Post by #&amp;thj^% on 2016-08-26
Please return the info I requested in my above post.

---

### Post by kate.t on 2016-08-26
Hello, 1fallen,

Thanks for your response. I went into the gedit program and typed 
/etc/bluetooth/audio.conf

and the response was "no results".  This is the first time I've used the text editor. 
So I checked in the file manager, and there is no such file there. 
Could that be the problem, a missing file?

---

### Post by #&amp;thj^% on 2016-08-26
Yes indeed..:)
See if you can follow this: [https://ceworkbench.wordpress.com/2011/03/21/configuring-linux-as-an-a2dp-audio-sink/](https://ceworkbench.wordpress.com/2011/03/21/configuring-linux-as-an-a2dp-audio-sink/)
I will try and hang in here with you for as long as i can today.

---

### Post by kate.t on 2016-08-26
Thank you, 1fallen.

When I go to the link you provided, I followed the links the author said to read first. I don't understand them. I'm sorry to be such a noob!:(

So I looked at the directions given right there.

I know I have Blueman bluetoothe manager installed, and pulseaudio volume control. I installed them.

But I don't know how to tell if I have BlueZ Bluetooth protocol stack or Pulseaudio audio server installed. Is it something I query in the terminal?

In addition, the instructions say to edit  the file /etc/bluetooth/audio.conf, but that's the file I'm missing.

So I'm sorry to say I don't know how to proceed.

Kathleen

---

### Post by #&amp;thj^% on 2016-08-26
No Worries...this can be a learning process.
Lets double check we have all the tools needed to succeed.
Open a terminal and paste in these commands.
```
sudo apt-get install pulseaudio-module-bluetooth
 pactl load-module module-bluetooth-discover
```
You may have some already installed but lets be sure something small dose not trip us up here.:)

---

### Post by kate.t on 2016-08-26
Thanks!

The first command tells me I have the latest version, so nothing was changed.

For the second command, the result is "Failure: Module initialization failed".

Kathleen

---

### Post by #&amp;thj^% on 2016-08-26
Oh sure we get a stubborn one...lol
Lets see if your device show up at all...from the terminal again input
```
pacmd list-sinks
```
If you do not know how to copy from the terminal, Take your mouse and highlight all showing there in the terminal and right click with you mouse and select copy and paste back here using code tags
to help read the output.

---

### Post by kate.t on 2016-08-26
Here's the output, 1fallen:

```
2 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_00_03.0.hdmi-stereo-extra1>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9950
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_00_03.0>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 1"
        alsa.id = "HDMI 1"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "7"
        alsa.card = "0"
        alsa.card_name = "HDA Intel HDMI"
        alsa.long_card_name = "HDA Intel HDMI at 0xc0610000 irq 48"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:03.0"
        sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0a0c"
        device.product.name = "Haswell-ULT HD Audio Controller"
        device.form_factor = "internal"
        device.string = "hdmi:0,1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo-extra1"
        device.profile.description = "Digital Stereo (HDMI 2)"
        device.description = "Built-in Audio Digital Stereo (HDMI 2)"
        alsa.mixer_name = "Intel Haswell HDMI"
        alsa.components = "HDA:80862807,80860101,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-1>
  * index: 1
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 1
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 7
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "CX20751/2 Analog"
        alsa.id = "CX20751/2 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xc0614000 irq 47"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9c20"
        device.product.name = "8 Series HD Audio Controller"
        device.form_factor = "internal"
        device.string = "front:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Conexant CX20751/2"
        alsa.components = "HDA:14f1510f,17aa3801,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output-speaker>

```

Kathleen

---

### Post by #&amp;thj^% on 2016-08-26
Have you rebooted your computer yet?

---

### Post by kate.t on 2016-08-26
Yes, I rebooted, but the situation is still the same. :-(

---

### Post by #&amp;thj^% on 2016-08-26
Lets see if we have a file yet
```
gedit /etc/bluetooth/audio.conf
```
Again copy all and paste back here with code tags:)

---

### Post by kate.t on 2016-08-26
Sadly, there's still no such file there. :-(

---

### Post by #&amp;thj^% on 2016-08-26
Well Yuck...Open Pusle Audio Volume and under the configuration Tab, See if you can find your head set.

---

### Post by kate.t on 2016-08-26
Yes, Pulse Audio Volume sees my headphones just fine, calling it "Headset", and on the configuration tab, the setting is Headset Head Unit (HSP/HFP).

Hope this is somehow good news!

---

### Post by #&amp;thj^% on 2016-08-26
can you set it to Analog Stereo Duplex from there?

---

### Post by kate.t on 2016-08-26
No. :-(

---

### Post by #&amp;thj^% on 2016-08-26
Can you take a screen shot of the Blue Tooth Manger showing the head set paired in it.
Using the paper clip in the Advanced settings for Forums Tools
and Attach it here.

---

### Post by kate.t on 2016-08-26
I hope this works properly.

---

### Post by #&amp;thj^% on 2016-08-26
Ok great give me some time to see if I can come up with something for you here.
I have to leave for the rest of the evening but will return tomorrow...:)
Kind Regards

---

### Post by kate.t on 2016-08-26
Thank you, 1fallen! You are very kind to help like this, much appreciated.

Kathleen

---

### Post by #&amp;thj^% on 2016-08-26
Think nothing of it...that's we are here for to help each other..Right???
Besides I like the challenge.:)
See you tomorrow same bat time same bat chanel. (Oh Brother.:smile:)
Cheers

---

### Post by kate.t on 2016-08-27
Hello, 1fallen!

If I'm remembering correctly, I think this is approximately the same bat time, same bat channel (24 hours from when we first started talking), so I'm around now and will keep checking here.

Kathleen

Here's some more information of relevance, I think.

I was able to set up the bluetooth pairing with my tower stereo speakers today. Here's the mystery: the speakers work in stereo, as they should! 

I should also report that, contrary to my original post, the built-in speakers DO work in stereo (they just sound awful, very tinny).

So now the only thing not working is my Sony stereo headphones, which are stubbornly mono. Mysterious, eh?

Kathleen

---

### Post by #&amp;thj^% on 2016-08-28
> **kate.t said:**
> Here's some more information of relevance, I think.

I was able to set up the bluetooth pairing with my tower stereo speakers today. Here's the mystery: the speakers work in stereo, as they should! 

I should also report that, contrary to my original post, the built-in speakers DO work in stereo (they just sound awful, very tinny).

So now the only thing not working is my Sony stereo headphones, which are stubbornly mono. Mysterious, eh?

Kathleen

Hi kate t sorry for my delay here, had some Life prioritys to deal with.;)
I have finally come to a possible solution for you. (Hopefuly)
Spent a couple of days on this and finally a workable hack.
Now bear in mind I do not have your specific head set But I was able to get my hands on a set of Bose Bluetooth headset.
Now my sound card is also different than yours, but I was able to achieve a setting for Analog Stereo Duplex for the sound card only...when I paired the headset with Bluezman I was taken to a segfaulted pulseaudio. (I can not tell you how big of a fan I am of the author of this and systemd...total sarcasm here of course.:tongue:)
On with the show..I created a "audio.conf" file and tested it thoroughly for a couple of days with no Ill effects to my system
(albeit your mileage may vary...I doubt it though).
But your computer came Pre-Installed with Xenial, and could make a difference...but again I feel you should be Ok.

I have compressed this file into a tarball, so you will need to extract to to /etc/bluetooth as root or Administrator.
To do this quick and easy open your terminal and enter
```
sudo -H nautilus
```
...then navigate to </etc/bluetooth>
and save the file there, Now close nautilus and reboot your machine.
The Contents of the file read as below...and should be named "audio.conf".

```
# Configuration file for the audio service

# This section contains options which are not specific to any
# particular interface
[General]

# Switch to master role for incoming connections (defaults to true)
#Master=true

# If we want to disable support for specific services
# Defaults to supporting all implemented services
#Disable=Gateway,Source,Socket

# SCO routing. Either PCM or HCI (in which case audio is routed to/from ALSA)
# Defaults to HCI
#SCORouting=PCM

# Automatically connect both A2DP and HFP/HSP profiles for incoming
# connections. Some headsets that support both profiles will only connect the
# other one automatically so the default setting of true is usually a good
# idea.
#AutoConnect=true

# Headset interface specific options (i.e. options which affect how the audio
# service interacts with remote headset devices)
[Headset]

# Set to true to support HFP, false means only HSP is supported
# Defaults to true
HFP=true

# Maximum number of connected HSP/HFP devices per adapter. Defaults to 1
MaxConnected=1

# Set to true to enable use of fast connectable mode (faster page scanning)
# for HFP when incoming call starts. Default settings are restored after
# call is answered or rejected. Page scan interval is much shorter and page
# scan type changed to interlaced. Such allows faster connection initiated
# by a headset.
FastConnectable=false

# Just an example of potential config options for the other interfaces
#[A2DP]
#SBCSources=1
#MPEG12Sources=0
```

So hopefully you now will have the option for Stereo Mode for your headset.
Fingers Crossed.

---

### Post by kate.t on 2016-08-28
Hi again, 1fallen!

No worries, life is like that, and it can't be helped.

I ran your command, and methinks something went awry. Here is the output I got on the terminal:

```
(nautilus:10482): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (nautilus:10482): CRITICAL **: Another desktop manager in use; desktop window won't be created
```


Any ideas on what to do next?

Kathleen

---

### Post by #&amp;thj^% on 2016-08-28
What is the output of this from the terminal
```
apt-cache policy gksu
```

---

### Post by kate.t on 2016-08-28
Here's the reply in the terminal:

```
gksu:
  Installed: 2.0.2-9ubuntu1
  Candidate: 2.0.2-9ubuntu1
  Version table:
 *** 2.0.2-9ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
```

Kathleen

---

### Post by #&amp;thj^% on 2016-08-28
Well lets see if you are fully updated then.
Run these one line at a time
```
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
```
And if you are now fully updated we can try this one
```
gksudo nautilus
```
and proceed with my instructions from my previous post.

---

### Post by kate.t on 2016-08-28
In the meantime, i coped and pasted your code into gedit, but gedit wouldn't save the file to the bluetooth location.

The error message said I didn't have the right permissions to save the file.  

Can't find where to look to give myself the necessary permission.

Kathleen

---

### Post by #&amp;thj^% on 2016-08-28
Sorry the forums are acting up a bit today on my end.
Lets see if you are fully updated.
Run these one line at a time
```
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
```
And if needed reboot your machine.
Then we can use this command instead of "sudo -H nautilus"
```
gksudo nautilus
```
and proceed with my instructions in my previous post.

---

### Post by kate.t on 2016-08-28
In the meantime, i coped and pasted your code into gedit, but gedit wouldn't save the file to the bluetooth location.

The error message said I didn't have the right permissions to save the file.  

Can't find where to look to give myself the necessary permission.



Kathleen

---

### Post by jeremy31 on 2016-08-28
kate.t 
Please use code tags around terminal output to preserve formatting and prevent smilies, this can be done in advanced reply by pressing the # above the reply window or you can just type [noparse]```
 before the output and 
``` after the output[/noparse]

I think the use of /etc/bluetooth/audio.conf might be deprecated and that is why it no longer exists.  I am able to use my bluetooth headphones in Ubuntu 16.04 in A2DP mode without it

---

### Post by kate.t on 2016-08-28
1fallen,

I did what you asked. But once again, an error message tells me I don't have permission to save the file.

Kathleen

Jeremy31,

Thanks for your advice about the code tags!

What does the word deprecated mean?

My headphones refuse to go into A2DP mode.

Kathleen

---

### Post by jeremy31 on 2016-08-28
Something else replaced the audio.conf or the bluetooth developers decided it was not needed and removed it.

What happens when you right click on your headet in Blueman, take a screenshot and post it but I hope it shows an "audio profile" option that you can select A2DP from

---

### Post by kate.t on 2016-08-28
Jeremy,

I posted a screenshot in msg #21.

When I try to switch the mode to A2DP, I get this error message: Failed to change profile to a2dp_sink

Kathleen

1fallen,

I finally got permission to add the audio.conf file. (Yay!)

But I still don't have stereo in the headset. (Boo!)

Any ideas?

Kathleen

---

### Post by jeremy31 on 2016-08-28
What is the result of ```
lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'; pactl list short
```

---

### Post by kate.t on 2016-08-28
Here it is, Jeremy:

```
lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'; pactl list short
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:380a]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo RTL8723BE PCIe Wireless Network Adapter [17aa:b736]
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 5986:055d Acer, Inc 
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 002: ID 045e:07fd Microsoft Corp. Nano Transceiver 1.1
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 10:08:B1:FB:EE:92  ACL MTU: 820:8  SCO MTU: 255:16
    UP RUNNING PSCAN 
    RX bytes:1399 acl:0 sco:0 events:151 errors:0
    TX bytes:27813 acl:0 sco:0 commands:151 errors:0
    Features: 0xff 0xff 0xff 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'kathleen-Lenovo-G50-70'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0xe2f
    LMP Version: 4.0 (0x6)  Subversion: 0x9f73
    Manufacturer: Realtek Semiconductor Corporation (93)

[    0.188302] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.965793] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x594f03)
[    2.439359] usb 2-7: Product: Bluetooth Radio 
[   14.131985] Bluetooth: Core ver 2.21
[   14.132006] Bluetooth: HCI device and connection manager initialized
[   14.132009] Bluetooth: HCI socket layer initialized
[   14.132011] Bluetooth: L2CAP socket layer initialized
[   14.132016] Bluetooth: SCO socket layer initialized
[   14.485491] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   14.485495] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   14.937502] Bluetooth: hci0: rom_version status=0 version=1
[   15.967685] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   31.585573] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.585576] Bluetooth: BNEP filters: protocol multicast
[   31.585579] Bluetooth: BNEP socket layer initialized
[   47.114459] Bluetooth: RFCOMM TTY layer initialized
[   47.114468] Bluetooth: RFCOMM socket layer initialized
[   47.114473] Bluetooth: RFCOMM ver 1.11
0    module-device-restore        
1    module-stream-restore        
2    module-card-restore        
3    module-augment-properties        
4    module-switch-on-port-available        
5    module-udev-detect        
6    module-alsa-card    device_id="0" name="pci-0000_00_03.0" card_name="alsa_card.pci-0000_00_03.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"    
7    module-alsa-card    device_id="1" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"    
8    module-bluetooth-policy        
9    module-bluetooth-discover        
10    module-bluez5-discover        
11    module-native-protocol-unix        
12    module-default-device-restore        
13    module-rescue-streams        
14    module-always-sink        
15    module-intended-roles        
16    module-suspend-on-idle        
17    module-systemd-login        
18    module-position-event-sounds        
19    module-filter-heuristics        
20    module-filter-apply        
21    module-x11-publish    display=:0    
22    module-x11-bell    display=:0 sample=bell.ogg    
23    module-x11-cork-request    display=:0    
24    module-x11-xsmp    display=:0 session_manager=local/kathleen-Lenovo-G50-70:@/tmp/.ICE-unix/3234,unix/kathleen-Lenovo-G50-70:/tmp/.ICE-unix/3234    
0    alsa_output.pci-0000_00_03.0.hdmi-stereo-extra1    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
1    alsa_output.pci-0000_00_1b.0.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
0    alsa_output.pci-0000_00_03.0.hdmi-stereo-extra1.monitor    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
1    alsa_output.pci-0000_00_1b.0.analog-stereo.monitor    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
2    alsa_input.pci-0000_00_1b.0.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
0    module-systemd-login.c    (null)
1    protocol-native.c    indicator-sound-service
3    protocol-native.c    unity-settings-daemon
4    protocol-native.c    indicator-sound-service
8    module-x11-xsmp.c    (null)
9    protocol-native.c    firefox
10    protocol-native.c    pactl
0    alsa_card.pci-0000_00_03.0    module-alsa-card.c
1    alsa_card.pci-0000_00_1b.0    module-alsa-card.c

```

Kathleen

---

### Post by jeremy31 on 2016-08-28
Well kate.t, I hope 1fallen has some experience with the rtl8723be bluetooth as I thought they were all broken as this is the first I have seen one that could actually pair with another device in a while

We used to have people install drivers from lwfingers github site along with troy tan's bluetooth module but that was all integrated into the kernel a while back

I would recommend filing a bug report against linux, see [the bug report guide](https://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by kate.t on 2016-08-28
Thanks for the advice and link, Jeremy.

But I do have one question before filing a bug report:

Can there be a logical explanation for why my bluetooth tower stereo speakers work fine (in stereo, in a2dp mode), but my headphones won't switch to a2dp and only play in mono? 

It doesn't seem logical to me. Does this sound like a real bug to you?

Thanks for all your help!

Kathleen

---

### Post by jeremy31 on 2016-08-29
Was your result for ```
pacmd list-sinks
``` done with the bluetooth headset connected?
You can get more info about the headset after connecting with
```
bluetoothctl
```
It should list the MAC of the controller and the headset
Then use ```
info AC:9B:0A:6C:EA:FF
```
And see what it says

---

### Post by kate.t on 2016-08-29
Jeremy,

The output of pacmd list-sinks with the headphones connected is:

```
3 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_00_03.0.hdmi-stereo-extra1>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9950
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_00_03.0>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 1"
        alsa.id = "HDMI 1"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "7"
        alsa.card = "0"
        alsa.card_name = "HDA Intel HDMI"
        alsa.long_card_name = "HDA Intel HDMI at 0xc0610000 irq 48"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:03.0"
        sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0a0c"
        device.product.name = "Haswell-ULT HD Audio Controller"
        device.form_factor = "internal"
        device.string = "hdmi:0,1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo-extra1"
        device.profile.description = "Digital Stereo (HDMI 2)"
        device.description = "Built-in Audio Digital Stereo (HDMI 2)"
        alsa.mixer_name = "Intel Haswell HDMI"
        alsa.components = "HDA:80862807,80860101,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-1>
    index: 1
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: front-left: 33000 /  50% / -17.88 dB,   front-right: 33000 /  50% / -17.88 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 1
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 126.00 .. 371.52 ms
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 7
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "CX20751/2 Analog"
        alsa.id = "CX20751/2 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xc0614000 irq 47"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9c20"
        device.product.name = "8 Series HD Audio Controller"
        device.form_factor = "internal"
        device.string = "front:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Conexant CX20751/2"
        alsa.components = "HDA:14f1510f,17aa3801,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output-speaker>
  * index: 3
    name: <bluez_sink.AC_9B_0A_6C_EA_FF>
    driver: <module-bluez5-device.c>
    flags: HARDWARE HW_VOLUME_CTRL LATENCY 
    state: RUNNING
    suspend cause: 
    priority: 9030
    volume: mono: 30584 /  47%
            balance 0.00
    base volume: 65536 / 100%
    volume steps: 16
    muted: no
    current latency: 29.30 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 5
    sample spec: s16le 1ch 8000Hz
    channel map: mono
                 Mono
    used by: 1
    linked by: 1
    fixed latency: 128.00 ms
    card: 3 <bluez_card.AC_9B_0A_6C_EA_FF>
    module: 26
    properties:
        bluetooth.protocol = "headset_head_unit"
        device.intended_roles = "phone"
        device.description = "MDR-ZX770BT"
        device.string = "AC:9B:0A:6C:EA:FF"
        device.api = "bluez"
        device.class = "sound"
        device.bus = "bluetooth"
        device.form_factor = "headset"
        bluez.path = "/org/bluez/hci0/dev_AC_9B_0A_6C_EA_FF"
        bluez.class = "0x240404"
        bluez.alias = "MDR-ZX770BT"
        device.icon_name = "audio-headset-bluetooth"
    ports:
        headset-output: Headset (priority 0, latency offset 0 usec, available: unknown)
            properties:
                
    active port: <headset-output>

```

Using bluetoothctl, I got this information:

```
# info AC:9B:0A:6C:EA:FF
Device AC:9B:0A:6C:EA:FF
    Name: MDR-ZX770BT
    Alias: MDR-ZX770BT
    Class: 0x240404
    Icon: audio-card
    Paired: yes
    Trusted: yes
    Blocked: no
    Connected: yes
    LegacyPairing: no
    UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
    UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: Handsfree                 (0000111e-0000-1000-8000-00805f9b34fb)
```

Are these results good news or bad news? :confused:

Thanks for asking, I hope this helps! :)

Kathleen

---

### Post by #&amp;thj^% on 2016-08-29
> **jeremy31 said:**
> 
I think the use of /etc/bluetooth/audio.conf might be deprecated and that is why it no longer exists.  I am able to use my bluetooth headphones in Ubuntu 16.04 in A2DP mode without it

> **jeremy31 said:**
> Well kate.t, _**I hope 1fallen has some experience with the rtl8723be bluetooth**_ as I thought they were all broken as this is the first I have seen one that could actually pair with another device in a while

We used to have people install drivers from lwfingers github site along with troy tan's bluetooth module but that was all integrated into the kernel a while back

I would recommend filing a bug report against linux, see [the bug report guide]("https://ubuntuforums.org/showthread.php?t=1011078")
Not since Trusty...Thanks for the tip jeremy31 , but as I said earlier I tested this on Xenial for 2 days on a fresh install with all updates including kernel upgrades with no negative results.
But I could not get my hands on her specific headset so I was more or less shooting in the dark here, and trying not to hose her system.:P

> **kate.t said:**
> Thanks for the advice and link, Jeremy.

But I do have one question before filing a bug report:

Can there be a logical explanation for why my bluetooth tower stereo speakers work fine (in stereo, in a2dp mode), but my headphones won't switch to a2dp and only play in mono? 

It doesn't seem logical to me. Does this sound like a real bug to you?

Thanks for all your help!

Kathleen
I feel a bug report should be filed kate t. However I also feel nothing will come of it. (Don't shoot the messenger ;))
But I also feel you are in very capable hands with jeremy31 for now... this is an area he is very good in.

---

### Post by kate.t on 2016-08-29
1fallen,

Thanks for your new post, I won't shoot, even if the message is an unhappy one. :wink:

I took Jeremy's advice and filed a bug report yesterday evening. Being such a noob, I hope I wrote it OK. Where it asked for the package name, I put in blueman, since that was the app that gave me the error message, "failed to change profile to a2dp_sink". I hope that was right, since I couldn't think of any other package. So now my report is sitting in 2 queues, one for Blueman, and the other for general Ubuntu bugs.

I hope the terminal outputs I posted for Jeremy this morning will help him help me!!

I'm grateful to you BOTH!

Kathleen

---

### Post by jeremy31 on 2016-08-29
With the headset connected ```
pacmd list-cards
```

---

### Post by kate.t on 2016-08-29
Here you go:

```
4 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_03.0>
    driver: <module-alsa-card.c>
    owner module: 6
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel HDMI"
        alsa.long_card_name = "HDA Intel HDMI at 0xc0610000 irq 48"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:03.0"
        sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0a0c"
        device.product.name = "Haswell-ULT HD Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400, available: unknown)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300, available: unknown)
        output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (priority 300, available: unknown)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5200, available: unknown)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 100, available: unknown)
        output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 100, available: unknown)
        output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5200, available: unknown)
        output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Output (priority 100, available: unknown)
        output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Output (priority 100, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:hdmi-stereo-extra1>
    sinks:
        alsa_output.pci-0000_00_03.0.hdmi-stereo-extra1/#0: Built-in Audio Digital Stereo (HDMI 2)
    sources:
        alsa_output.pci-0000_00_03.0.hdmi-stereo-extra1.monitor/#0: Monitor of Built-in Audio Digital Stereo (HDMI 2)
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    index: 1
    name: <alsa_card.pci-0000_00_1b.0>
    driver: <module-alsa-card.c>
    owner module: 7
    properties:
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xc0614000 irq 47"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9c20"
        device.product.name = "8 Series HD Audio Controller"
        device.form_factor = "internal"
        device.string = "1"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        input:analog-stereo: Analog Stereo Input (priority 60, available: unknown)
        output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:analog-stereo+input:analog-stereo>
    sinks:
        alsa_output.pci-0000_00_1b.0.analog-stereo/#1: Built-in Audio Analog Stereo
    sources:
        alsa_output.pci-0000_00_1b.0.analog-stereo.monitor/#1: Monitor of Built-in Audio Analog Stereo
        alsa_input.pci-0000_00_1b.0.analog-stereo/#2: Built-in Audio Analog Stereo
    ports:
        analog-input-internal-mic: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
    index: 3
    name: <bluez_card.AC_9B_0A_6C_EA_FF>
    driver: <module-bluez5-device.c>
    owner module: 26
    properties:
        device.description = "MDR-ZX770BT"
        device.string = "AC:9B:0A:6C:EA:FF"
        device.api = "bluez"
        device.class = "sound"
        device.bus = "bluetooth"
        device.form_factor = "headset"
        bluez.path = "/org/bluez/hci0/dev_AC_9B_0A_6C_EA_FF"
        bluez.class = "0x240404"
        bluez.alias = "MDR-ZX770BT"
        device.icon_name = "audio-headset-bluetooth"
        device.intended_roles = "phone"
    profiles:
        headset_head_unit: Headset Head Unit (HSP/HFP) (priority 20, available: no)
        a2dp_sink: High Fidelity Playback (A2DP Sink) (priority 10, available: no)
        off: Off (priority 0, available: yes)
    active profile: <off>
    ports:
        headset-output: Headset (priority 0, latency offset 0 usec, available: no)
            properties:
                
        headset-input: Headset (priority 0, latency offset 0 usec, available: no)
            properties:
                
    index: 5
    name: <bluez_card.AC_9B_0A_6C_EA_FF.2>
    driver: <module-bluez5-device.c>
    owner module: 29
    properties:
        device.description = "MDR-ZX770BT"
        device.string = "AC:9B:0A:6C:EA:FF"
        device.api = "bluez"
        device.class = "sound"
        device.bus = "bluetooth"
        device.form_factor = "headset"
        bluez.path = "/org/bluez/hci0/dev_AC_9B_0A_6C_EA_FF"
        bluez.class = "0x240404"
        bluez.alias = "MDR-ZX770BT"
        device.icon_name = "audio-headset-bluetooth"
        device.intended_roles = "phone"
    profiles:
        headset_head_unit: Headset Head Unit (HSP/HFP) (priority 20, available: unknown)
        a2dp_sink: High Fidelity Playback (A2DP Sink) (priority 10, available: no)
        off: Off (priority 0, available: yes)
    active profile: <headset_head_unit>
    sinks:
        bluez_sink.AC_9B_0A_6C_EA_FF/#5: MDR-ZX770BT
    sources:
        bluez_sink.AC_9B_0A_6C_EA_FF.monitor/#9: Monitor of MDR-ZX770BT
        bluez_source.AC_9B_0A_6C_EA_FF/#10: MDR-ZX770BT
    ports:
        headset-output: Headset (priority 0, latency offset 0 usec, available: unknown)
            properties:
                
        headset-input: Headset (priority 0, latency offset 0 usec, available: unknown)
            properties:
                

```

---

### Post by jeremy31 on 2016-08-29
See if ```
pacmd set-card-profile 3 a2dp_sink
```
Works as it should

---

### Post by kate.t on 2016-08-29
Nothing was fixed.

Instead, a message popped up:

"Sorry, Ubuntu 16.04 has experienced an internal error."

When I clicked on "Show details", I got a long list of information, which unfortunately won't let me copy and paste it. 

However, the problem type was a "crash" and the crash was described as being "pulseaudio crashed with SIGSEVG in main_arena()".

Let me know if you want more info from those details and I'll manually copy it.

Kathleen

---

### Post by jeremy31 on 2016-08-29
I would right click on the headphones in Blueman and select "refresh services" and then see if A2DP audio is available

---

### Post by kate.t on 2016-08-29
I can't find any option called "refresh services". I right-clicked on the headphones listing and there were three choices for disconnect (headset, hands free, and audio sink), audio profile (stubbornly stuck to Headset Head Unit HSF/HSP). Send a file, Browse, and Pair are greyed out. Then there's Trust, Setup, Rename Device, Remove, and Disconnect. Nothing called "refresh services".

What am I doing wrong?

---

### Post by kate.t on 2016-08-29
Here's a new wrinkle. (oh, goodie!) :(

I just lost all sound from the headphones, I can't even hear mono. A little box had popped up asking if I wanted to authenticate the headphones and I clicked on "authenticate always." Then it happened.

When I clicked on a video, there was a slight crackling sound in the headphones, then nothing happened. Even worse, the video was frozen.

I tried this with several videos. All frozen videos with no sound. :confused:

Kathleen

---

### Post by #&amp;thj^% on 2016-08-29
> **kate.t said:**
> I can't find any option called "refresh services". I right-clicked on the headphones listing and there were three choices for disconnect (headset, hands free, and audio sink), audio profile (stubbornly stuck to Headset Head Unit HSF/HSP). Send a file, Browse, and Pair are greyed out. Then there's Trust, Setup, Rename Device, Remove, and Disconnect. Nothing called "refresh services".

What am I doing wrong?

Hey kate.t I have just talked to jeremy31 and a friend of mine contacted me just about 45 mins ago...he claims he got his working using the information found here: [http://askubuntu.com/questions/763539/bluetooth-speaker-no-sound-in-ubuntu-16-04/817926](http://askubuntu.com/questions/763539/bluetooth-speaker-no-sound-in-ubuntu-16-04/817926)
He also said he had to try it a couple of times to get it to work.
Also please take your time and read all the information on that page...kind of a cheesy work around but if works might be worth the effort.
Also I am signing off for the evening so I will check back tomorrow to see if he is accurate in his advice.
Best of luck and thanks for your patience here.:)

---

### Post by jeremy31 on 2016-08-29
Do a shut down and then boot up the computer

---

### Post by kate.t on 2016-08-29
More info on the new wrinkle:

The box labeled "Sorry, Ubuntu has experienced an internal error" popped up again.

Blueman had a crash. The description is "blueman-manager crashed with SIGSEGV in ffi_call_unix64()"

Does this info help?

Kathleen

---

### Post by kate.t on 2016-08-29
We cross-posted. Will shut down now.

---

### Post by kate.t on 2016-08-29
Well, thank goodness. (And thank you!)

At least I got my mono sound back, and videos are playing.

This is important because I need good headphones for my work. From home I do closed-captioning for the hearing-impaired for movies and videos.

Kathleen

---

### Post by kate.t on 2016-08-29
1fallen,

No, I thank YOU for YOUR patience and efforts, both you and jeremy31!!!

I tried the work-around a few times. No dice. What was especially funny was that I had tried this *before *I even started posting here, and forgot that until I read some of the comments on that page. Still, I tried it again a few times, and no such luck.

One of the things I find interesting is that RTL8723BE is the name/number of both the wifi and bluetooth.

I had terrible problems with wifi dropping out intermittently, even when I sat directly in front of the device. So, after much googling while on Ethernet, I found a page that took me step-by-step through updating the driver for that chipset. 

However, the problem with the headphones was exactly the same before and after updating the driver.  Sigh.

Kathleen

---

### Post by #&amp;thj^% on 2016-08-30
kate.t it is people like you that make the effort worth it...some bring a frustration level that make it harder to stay motivated to even continue trying to help. (I guess we should have a magic wand that cures all.)
I am saddened to hear that you still have the same problem though.
jeremy31 and myself are just at a loss here...by what you have shown us..this headset should work as expected.
But I also find it very interesting that both the WiFi and Bluetooth have the same Name/Numbering...so I am now thinking your Specific Hardware might be the fly in the soup. (At least for Ubuntu or Linux)
I just wish I could have the same setup as you have to properly trouble shoot and not risk breaking what you have now.
And kudos to you for your efforts with helping in the closed-captioning for the hearing-impaired. 
Keep up the good fight.
Best Regards

---

### Post by jeremy31 on 2016-08-30
1fallen, I actually went and read the first post again and I no longer think this is a bluetooth issue but a sound issue as kate.t stated that the sound coming from the speakers on the computer sounds like mono and bad

kate.t can you post a screenshot of the sound settings or just tell us if it offers a balance slider for right and left, and I would also post ```
lspci -nnk | grep -iA2 audio
``` so we can see what chipset is involved

---

### Post by kate.t on 2016-08-30
1fallen,

You are so kind, I appreciate your words very much.

I have some good news!!!

With a great amount of finagling, I am able to get my headphones to play in stereo. Of course, every time I turn them off I have to go through a big rigamarole again in trying to get the stereo back on. Blueman is acting hinky, too, even though I uninstalled it and reinstalled it.

I wouldn't say that this situation is resolved, exactly, because the process is still so iffy and takes up a lot of time, but I now have hope. There MUST be an answer, since the headphones CAN play in stereo.

I want to tell you and jeremy31 all the gory details in the undying hope that at some point this will be a much easier way.

However, I'm up to my neck in a project from one of my other freelance jobs, a writing project that's coming due soon.

When I get the chance to take a break, I'll concentrate on this again and retrace my steps here on how I jigger this audio mess to get the headphones temporarily working.

Thanks again to you and jeremy31!!!

Kathleen

---

### Post by jeremy31 on 2016-08-30
I would love to see your solution on this one

---

### Post by kate.t on 2016-08-31
jeremy31 & 1fallen,

Here's what I have to do to make sure the headphones produce stereo sound:

I go into blueman, but not the normal way. Blueman has suddenly and inexplicably gone hinky on me. When I click on devices, nothing opens. The little whirling circle indicator seems to suggest it's *trying* to do something, but eventually the whirling circle indicator just disappears. The normal box showing the devices paired and connected does not show up.

So instead, what I do is I click on Setup New Device. That box, the Bluetooth Device Setup Assistant, does come up, and I go through the setup process, choose my headphones, and then when I get to the part that says "Connect to:" I don't click on "Headset", I click on "Audio Sink" instead. When I click Next, I'm told that the device was added  and connected successfully.

*Then *what I have to do is open up Sound Settings and change the setting from HSP/HFP to A2DP Sink. Then to make sure the setting has "taken", I need to click on "Test Sound" to verify that the sound test is the stero test, not the mono test.

I have to go through this annoying procedure every time. However, I'm so pleased to finally have stero!!!

It's also true that when I turn on my headphones the Sound Settings do not switch automatically from "Speakers Built-in-Audio" to "Headset", I have to make that switch manually every time. Is that the default behavior? Is there any way to make the sound setting switch to "Headset" when I turn on my headphones? Or should I just count my blessings at this point?

Thanks for hanging in there with me!

Kathleen

---

### Post by kate.t on 2016-08-31
Sorry I missed your post about  lspci -nnk | grep -iA2 audio, jeremy31.

Here's the terminal output:

```
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
    Subsystem: Lenovo Haswell-ULT HD Audio Controller [17aa:3978]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
--
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
    Subsystem: Lenovo 8 Series HD Audio Controller [17aa:3978]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
```

And I should also mention that in a post subsequent to my first post, I corrected my own misperception. It turns out that the in-built speakers were (and are) putting out stereo sound, I just mistook it for mono because it sounded so lousy. (Sorry about the confusion!)

Also, in sound settings there is no balance slider for right and left. I wish there were!

Kathleen

---

### Post by kate.t on 2016-08-31
It turns out I spoke way too soon. The stereo was nice while I had it.

Now I can't get anything over my headphones, not stereo, not mono. I rebooted the computer, went through the procedure described above, and nothing.

I'm too tired to do any more tonight.

Tomorrow is another day.

Kathleen

---

### Post by #&amp;thj^% on 2016-08-31
kate.t I wish there were more folks like yourself...but alas I guess that makes the world go round.
What a treat you have been through all of this..and the pleasure has been all mine to have met someone like you.:KS
After reading through all your latest posts I was taken back to a similar problem while helping another poster.
And this is just a thought...But have your tried when the sound disappears to manually removing the headphone while Bluez is still running and then re-plugging them back in, and again this might take a couple of tries.
And by the way I have not given up on this..until I hear you say it is solved. (My thoughts are leaning towards a Low Latency Kernel)
More to come if I feel this is relevant.
Kind Regards

---

### Post by kate.t on 2016-08-31
Thanks for your kindness, 1fallen, I am very glad to have found in you an "ubuntu friend" here, too!!!

I tried turning the headphones off and on (rather than unplugging them...they are wireless), and that didn't help.

I now have a new problem (and started another thread for it), my battery won't charge past 21%!! I can't imagine how this could be related to sound problems, but thought I should mention it here, just in case.

I don't know what "Low Latency Kernel" means, but it sounds serious! :?

Kathleen

---

### Post by #&amp;thj^% on 2016-08-31
> **kate.t said:**
> Thanks for your kindness, 1fallen, I am very glad to have found in you an "ubuntu friend" here, too!!!

I tried turning the headphones off and on (rather than unplugging them...they are wireless), and that didn't help.

Kathleen
Yes that won't work you will need to manually remove the device while Bluez is running and reconnect them, and just to remind again it might take a couple tries if it works at all.
It was just a method that has worked before, so I was curious to see if you also had such luck. And no I have not forgotten they are wireless.;)
> **kate.t said:**
> 
I don't know what _**"Low Latency Kernel"**_ means, but it sounds serious!
Kathleen
Just sounds serious...but kind of tough to explain.
Have a look here if you have some free time: [https://sevencapitalsins.wordpress.com/2007/08/10/low-latency-kernel-wtf/](https://sevencapitalsins.wordpress.com/2007/08/10/low-latency-kernel-wtf/)
I almost exclusively run low lat kernels.
Yes I saw your battery issue also...all I can say there is Lenovo Bios can be a handful at times. Having owned a couple myself.:D
[http://www.bing.com/search?q=lenovo+laptop+bios+buggy&form=OSDSRC](http://www.bing.com/search?q=lenovo+laptop+bios+buggy&form=OSDSRC)
Off topic for this thread but I would the first chance you get is to totally discharge the battery once, and remove it, and then put it back in and power on with the cord plugged in.
Maybe??...or Maybe not??

---

### Post by kate.t on 2016-08-31
1fallen,

Well, what do you know? Removing the headphones and  reconnecting them a couple of times worked! These things are such a  mystery...is there any alchemy involved? Are there Linux gods who need to be propitiated? :wink:

It would be really, really bliss if I could get these headphones to work reliably, the way they're supposed to. I'm not giving up hope! It's not so much the patience of Job as it is my being *downright stubborn.* I don't want this to defeat me!

On the topic of the battery indicator, I'll post a question for you in the other thread I started for that purpose. Don't wanna be off-topic. :-)

Kathleen

---

### Post by #&amp;thj^% on 2016-08-31
> **kate.t said:**
> 1fallen,

Well, what do you know? Removing the headphones and  reconnecting them a couple of times worked! These things are such a  mystery...is there any alchemy involved? _**Are there Linux gods who need to be propitiated? :wink:**_

It would be really, really bliss if I could get these headphones to work reliably, the way they're supposed to. I'm not giving up hope! It's not so much the patience of Job as it is my being *downright stubborn.* I don't want this to defeat me!

On the topic of the battery indicator, I'll post a question for you in the other thread I started for that purpose. Don't wanna be off-topic. :-)

Kathleen

He he...Good sense of humor, I like it.
Give me a couple of days to be sure on this kate.t, I have to test my theory first...I don't want to break your system.
I can be a bit wild, i have a lack of fear being a tester, I love to break things and put them back together. :o 
It would be nice (quicker and more exact) if I was working with your same hardware, but I am not.
I will keep this thread updated. Okey Dokey? :smile:

---

### Post by kate.t on 2016-09-01
Okey Dokey, Pokey! So you're a bit wild, eh? ;)

Not breaking my system nonetheless sounds like a brilliant idea. I will wait patiently, no hurry. :)

Kathleen

---

### Post by jeremy31 on 2016-09-02
I used this as an excuse to buy a nice bluetooth headset and found they are finicky.  The first pairing worked great and allowed me to use A2DP right away, however after disconnecting and reconnecting A2DP wouldn't work.  I did find that if I disconnected from the headset in the bluetooth GUI, then reconnected and pressed the volume buttons on the headset then the sound settings would allow me to switch to A2DP

The headset is a lot nicer than my Philips SHB4000 but the Philips had no issues using A2DP ever however I did find a lot of SCO errors in the /var/log/kern.log that I haven't seen before ```
Sep  2 18:13:27 jeremy-Lenovo-G710 kernel: [ 2324.344980] Bluetooth: hci0 SCO packet for unknown connection handle 6
```

---

### Post by #&amp;thj^% on 2016-09-03
> **jeremy31 said:**
> I used this as an excuse to buy a nice bluetooth headset and found they are finicky.  The first pairing worked great and allowed me to use A2DP right away, however after disconnecting and reconnecting A2DP wouldn't work.  I did find that if I disconnected from the headset in the bluetooth GUI, then reconnected and pressed the volume buttons on the headset then the sound settings would allow me to switch to A2DP

The headset is a lot nicer than my Philips SHB4000 but the Philips had no issues using A2DP ever however I did find a lot of SCO errors in the /var/log/kern.log that I haven't seen before ```
Sep  2 18:13:27 jeremy-Lenovo-G710 kernel: [ 2324.344980] Bluetooth: hci0 SCO packet for unknown connection handle 6
```

Thanks jeremy31 I appreciate your input here.... pulling my hair out ATM.:)
I am having better results with a "Low Lat" kernel though.... But far from perfect. 
> [ 2324.344980] Bluetooth: hci0 SCO packet for unknown connection handle 6
I am seeing similar???

---

### Post by kate.t on 2016-09-03
I don't imagine it matters if I don't understand what either one of you is talking about...right? I would dearly love to understand, but if it would take you a lot of effort to explain, I'll just keep being patient.

I am grateful that you're both still thinking about this!

In the meantime, I'm using a ratty ancient cheap plug-in headset which hurts my ears, but at least I can get some videos closed-captioned.

Thanks!

Kathleen

---

### Post by kate.t on 2016-09-04
Here's something I just noticed this weekend. I decided to check out Alsamixer. Almost every time I look there, i find the headphones muted. I unmute them, but that doesn't "stick".

Not long thereafter, I check Alsamixer again and the headphones are muted again. This also happens after rebooting the computer.

The original problem of the Sony stereo headphones playing in mono is no longer occurring. I can finally get the setting for A2DP to show up both in Blueman and PulseAudio Control. But that's not helping me.

Now I can't get sound out of the headphones at all. At least, it won't work about 19 out of 20 times I fiddle with the settings. Once in a blue moon the headphones suddenly work, but I'm unaware of doing anything different with the settings, and I can't get the headphones to work twice in a row.

Hope this new info inspires someone to think of an idea that works.

Thanks very much in advance!!

Kathleen

---

### Post by kate.t on 2016-09-06
This is an update for anyone interested or still mulling this over.

I was about to announce that I had found a reliable workaround, when suddenly I find it's borked again.

The workaround: I found that if I methodically used blueman to connect first to Headset HSP/HFP, then disconnect, and then connect to audio sink (sometimes twice), it let me then switch the mode to A2DP, and finally it worked (after adjusting the sound settings each time).  Hooray! It was highly annoying, but seemed reliable. I used the headphones for work for two days.

Now, all of a sudden, today, the headphones won't even connect. When I turn them on, blueman won't light up in the notification bar, and nothing I do will make it connect with bluetooth.  

So it's two steps forward, three steps back.

Any suggestions?

Kathleen

---

### Post by #&amp;thj^% on 2016-09-07
> **kate.t said:**
> This is an update for anyone interested or still mulling this over.

I was about to announce that I had found a reliable workaround, when suddenly I find it's borked again.

The workaround: I found that if I methodically used blueman to connect first to Headset HSP/HFP, then disconnect, and then connect to audio sink (sometimes twice), it let me then switch the mode to A2DP, and finally it worked (after adjusting the sound settings each time).  Hooray! It was highly annoying, but seemed reliable. I used the headphones for work for two days.

Now, all of a sudden, today, the headphones won't even connect. When I turn them on, blueman won't light up in the notification bar, and nothing I do will make it connect with bluetooth.  

So it's two steps forward, three steps back.

Any suggestions?

Kathleen
Hi kate.t I have not forgot or lost interest.
I just can not get a reliable workaround.
I find that pulseaudio is very unreliable and blue-man needs work.
However on Arch and kernel 4.7.2-1 works reliably...but this doses not work on Ubuntu??
I would like you to try disabling blue-man from starting with the OS in Startup Applications and un-tick Bluez...and rebooting. (but do not disconnect your Buletooth device for your headphones)
Then try getting your headphones to sink with blue-man manager.

---

### Post by kate.t on 2016-09-08
Thanks for getting back to me!

I found that rebooting brought me back to where I could use my own previous workaround described above. Disabling blue-man first did not seem to make any difference, I still need to do that song-and-dance routine each time before getting the headphones to play properly.

You had once earlier mentioned the phrase "low latency kernel." I tried reading about that, but most of it was over my head. Were you suggesting that that might be the kind of kernel I have, or were you suggesting it might be the kind of kernel I want to have?

I typed in uname -a at the terminal, and found that I have the generic kernel.

I wonder if this is something I can pester the Linux vendor with. They say they have a tech help phone number...Or is this something likely considered extraneous to more basic questions of system operations?

Thanks for sticking with this for so long!!:)

Kathleen

---

### Post by #&amp;thj^% on 2016-09-08
> **kate.t said:**
> Thanks for getting back to me!

I found that rebooting brought me back to where I could use my own previous workaround described above. Disabling blue-man first did not seem to make any difference, I still need to do that song-and-dance routine each time before getting the headphones to play properly.

You had once earlier mentioned the phrase "low latency kernel." I tried reading about that, but most of it was over my head. Were you suggesting that that might be the kind of kernel I have, or were you suggesting it might be the kind of kernel I want to have?

I typed in uname -a at the terminal, and found that I have the generic kernel.

I wonder if this is something I can pester the Linux vendor with. They say they have a tech help phone number...Or is this something likely considered extraneous to more basic questions of system operations?

Thanks for sticking with this for so long!!:)

Kathleen
Hey that is good to hear that restarting your laptop works...at least to get your work done.:)
As for the Low Latency Kernel, that never amounted to anything.
But yes if you have support with the purchase of your computer, that might be a good place for additional help.
I know it works with Linux, the bluetooth headphones I borrowed work flawlessly on Arch...but not so well on Ubuntu:(
But all that "could" change with updates that will come in with time.
So far I feel that Pulseaudio and Blueman and possibly the kernel that is being used for Xenial ATM are the fly in the soup.
Keep this thread updated.
Kind Regards

---

### Post by #&amp;thj^% on 2016-09-10
kate.t Do not give up hope here...I think i am now getting some where with all of this mess.
I need to see what the return of this entered in the terminal
```
ps aux | grep pulse
```
And this also please
```
apt-cache policy lightdm
```
Paste back the return here...in code tags.

---

### Post by kate.t on 2016-09-10
1fallen,

Not to worry, hope springs eternal!!!

Here's the first output to ps aux | grep pulse:

```
kathleen  3536  0.5  0.1 594076  8448 ?        S<l  Sep07  25:26 /usr/bin/pulseaudio --start --log-target=syslog
kathleen  9746  0.0  0.0  21292   932 pts/18   S+   11:41   0:00 grep --color=auto pulse

```

And here's the second, to apt-cache policy lightdm:

```
lightdm:
  Installed: 1.18.2-0ubuntu2
  Candidate: 1.18.2-0ubuntu2
  Version table:
 *** 1.18.2-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.18.1-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

I don't know what it means, but I hope that helps.:)

Kathleen

---

### Post by #&amp;thj^% on 2016-09-10
I am seeing what i thought i would...here is mine from Arch
```
ps aux | grep pulse
me        6141  0.0  0.1 498092 12216 ?        S<sl 06:59   0:00 /usr/bin/pulseaudio --daemonize=no
me        6147  0.0  0.4 545256 33764 ?        Sl   07:00   0:00 /usr/lib/xfce4/panel/wrapper-2.0 /usr/lib/xfce4/panel/plugins/libpulseaudio-plugin.so 3 16777254 pulseaudio PulseAudio Plugin Adjust the audio volume of the PulseAudio sound system
me       12645  0.0  0.0  10760  2264 pts/0    S+   14:05   0:00 grep pulse


```
I should have some good news here (Fingers Crossed;)).
This also common of course for other debian related OS's.
Check back I should have something to test here...and by the way, Do you still have the text file "audio.conf" we made this at the beginning of this thread.

---

### Post by kate.t on 2016-09-10
i just this second emailed my huge writing assignment, and I glance back here, and there you are! Sounds ever more hopeful! :)

Hmmm, your file looks a lot different than mine. I imagine that means something.

Yes, I still have audio.conf. I figured it wasn't bothering anybody, so I left it alone.;)

I'll be around this evening, and so will check back from time to time.  Thanks so much!!!

Kathleen

---

### Post by daniii10 on 2016-09-10
I have read this thread and I also had this exact problem with my bluetooth headphones before and this is my solution try it and see if it's also work for you.

First open blueman and turn on your bluetooth headphones.
Connect your headphones via blueman by right-click on your headphones on the list and click 'headset'.
Now give it a few seconds to connect then right-click on your headphones model and > audo profile > off (set it off)
[[IMG]https://s21.postimg.org/thr5gb2kj/blueman.jpg[/IMG]]("https://postimg.org/image/thr5gb2kj/")
Now turn off your headphones and turn them on again it will ask you to connect click 'deny' (wait a few seconds until it's completely disconnected) go to blueman right-click on your headphones then click headset and give it a few seconds to connect.
Finlay right-click on your headphones model then click on audio profile > High Fidelity Playback (A2DP Sink).

Final step go to ubuntu settings and sound make sure output is set to your headphones. This is always work for me.

Now for the future, every time when you disconnect your headphones before you just turn them off go to blueman and right-click on your headphones model > audio profile > and set it off. Now turn off your bluetooth headphones.

I know it's maybe not a very comfortable solution but it works for me.

---

### Post by kate.t on 2016-09-11
Thanks, daniii10, for your suggestion! :)

ATM, the workaround I described earlier is letting me get stereo sound. It is, however, a big rigamarole.

I just want these stereo headphones to work simply, the way they did for me on ubuntu 14.04. With that system, I just turned on the headphones, and they worked. Didn't even have to go into sound settings each time make sure that was set up correctly.

I will, of course, keep an eye on your own workaround in the event my own malfunctions again.

Kathleen

---

### Post by daniii10 on 2016-09-11
I'm happy to know it works for now. My solution worked for me so far with two types of bluetooth headphones. I think for some reason the computer having hard time connecting straight to A2DP profile and when you first set it off it connect in 'off' mode then it allows you to connect to the profile you want. Maybe someone can write a script that forces blueman first to connect in 'off' mode then connect to A2DP mode. I'm not a programmer but I think it is possible. Maybe one of the more experienced member in the forum can shed light on it (I'm also kind of a noob ;)).

---

### Post by #&amp;thj^% on 2016-09-11
Hi kate.t this has been working great for a couple of days now.:)
Please read this very carefully and double check for typeO's
What I did:

1. First we will copy the files I edited
I used nano for the editor here as you had problems with "sudo -H gedit" in the beginning.
But feel free to use it instead of nano if you are more comfortable with gedit

 ```
   sudo cp /etc/bluetooth/audio.conf /etc/bluetooth/audio.conf_tmp
    sudo cp /etc/pulse/default.pa /etc/pulse/default.pa_tmp
    sudo cp /usr/bin/start-pulseaudio-x11 /usr/bin/start-pulseaudio-x11_tmp
```

2. Edit /etc/bluetooth/audio.conf

```
    sudo nano /etc/bluetooth/audio.conf
## or use sudo -H gedit /etc/bluetooth/audio.conf
```

I had also made a couple of changes here also...so copy and paste the content into yours replacing everything.
This is in my audio.conf
```

  # Configuration file for the audio service

# This section contains options which are not specific to any
# particular interface
[General]

# Switch to master role for incoming connections (defaults to true)
#Master=true

# If we want to disable support for specific services
# Defaults to supporting all implemented services
#Disable=Gateway,Source,Socket

# SCO routing. Either PCM or HCI (in which case audio is routed to/from ALSA)
# Defaults to HCI
#SCORouting=PCM

# Automatically connect both A2DP and HFP/HSP profiles for incoming
# connections. Some headsets that support both profiles will only connect the
# other one automatically so the default setting of true is usually a good
# idea.
#AutoConnect=true

# Headset interface specific options (i.e. options which affect how the audio
# service interacts with remote headset devices)
[Headset]

# Set to true to support HFP, false means only HSP is supported
# Defaults to true
HFP=true

# Maximum number of connected HSP/HFP devices per adapter. Defaults to 1
MaxConnected=2

# Set to true to enable use of fast connectable mode (faster page scanning)
# for HFP when incoming call starts. Default settings are restored after
# call is answered or rejected. Page scan interval is much shorter and page
# scan type changed to interlaced. Such allows faster connection initiated
# by a headset.
FastConnectable=true

# Just an example of potential config options for the other interfaces
#[A2DP]
#SBCSources=1
#MPEG12Sources=0
```

#Edit /etc/pulse/default.pa

   ```
 sudo nano /etc/pulse/default.pa
```

comment out (with an # at the beginning of the line) the following line
So it would now look like this.

```
#load-module module-bluetooth-discover
```

now edit /usr/bin/start-pulseaudio-x11

   ```
 sudo nano /usr/bin/start-pulseaudio-x11
```

and after the lines

   ```
 if [ x&#8221;$SESSION_MANAGER&#8221; != x ] ; then
            /usr/bin/pactl load-module module-x11-xsmp &#8220;display=$DISPLAY session_manager=$SESSION_MANAGER&#8221; > /dev/null
    fi

```
add the following

   ```
 /usr/bin/pactl load-module module-bluetooth-discover

```
This way the Pulse audio&#8217;s Bluetooth modules will not be started at boot time but after x11 is started.
#Restart and I was finally able to switch to A2DP with a couple of bluetooth headsets
Hope it works for you too.
My Specs for this are below
```
$ inxi -Fxz
System:    Host: me-Aspire-5750 Kernel: 4.4.0-36-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: MATE 1.12.1 (Gtk 3.18.9-1ubuntu3.1)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Acer (portable) product: Aspire 5750 v: V1.14
           Mobo: Acer model: JE50_HR Bios: Acer v: V1.14 date: 09/07/2011
CPU:       Dual core Intel Core i3-2330M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 8780
           clock speeds: max: 2200 MHz 1: 1256 MHz 2: 942 MHz 3: 1168 MHz
           4: 1296 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-36-generic
Network:   Card-1: Broadcom NetLink BCM57785 Gigabit Ethernet PCIe
           driver: tg3 v: 3.137 bus-ID: 02:00.0
           IF: enp2s0f0 state: down mac: <filter>
           Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak]
           driver: iwlwifi bus-ID: 03:00.0
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 192.1GB (10.9% used)
           ID-1: /dev/sda model: Hitachi_HTS54161 size: 160.0GB
           ID-2: USB /dev/sdb model: Ultra size: 32.0GB
Partition: ID-1: / size: 143G used: 5.1G (4%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.14GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 199 Uptime: 11 min Memory: 394.6/3804.8MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.2.35 


```

---

### Post by #&amp;thj^% on 2016-09-11
I see you are online now... and I will be here for you for about an hour.
Then I won't be able to play no more.:lolflag:

---

### Post by kate.t on 2016-09-11
1fallen,

I hate to be the bearer of bad news, but sadly...nope.

I did everything the way you described, but no dice. My workaround (jiggling between HSF/HSP and A2DP sink a couple times) still works. I have to do it in blueman, it doesn't work in the bluetooth control in the regular settings.

The only difference now is that blueman is not automatically on my notification bar, I have to start the program manually.

Should I be trying to figure out how to go backwards and remove everything I did, or should I just leave well enough alone?

Thank you for all your work!!!

Kathleen

---

### Post by #&amp;thj^% on 2016-09-11
Just to be sure... you have rebooted right?

---

### Post by kate.t on 2016-09-11
Yes, multiple times.

---

### Post by #&amp;thj^% on 2016-09-11
Let me see this file
```
gedit /usr/bin/start-pulseaudio-x11

```

---

### Post by kate.t on 2016-09-11
Here it is!

```
#!/bin/sh

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

set -e

if [ x"$DISPLAY" != x ] ; then

    /usr/bin/pactl load-module module-x11-publish "display=$DISPLAY" > /dev/null
    /usr/bin/pactl load-module module-x11-bell "display=$DISPLAY" "sample=bell.ogg" > /dev/null
    /usr/bin/pactl load-module module-x11-cork-request "display=$DISPLAY" > /dev/null

    if [ x"$KDE_FULL_SESSION" = x"true" ]; then
       /usr/bin/pactl load-module module-device-manager "do_routing=1" > /dev/null
    fi

    if [ x"$SESSION_MANAGER" != x ] ; then
    /usr/bin/pactl load-module module-x11-xsmp "display=$DISPLAY session_manager=$SESSION_MANAGER" > /dev/null
    fi
/usr/bin/pactl load-module module-bluetooth-discover
fi
```

---

### Post by #&amp;thj^% on 2016-09-11
Other than the spacing I see nothing wrong there.
IE:
```

/usr/bin/pactl load-module module-x11-publish "display=$DISPLAY" > /dev/null
    /usr/bin/pactl load-module module-x11-bell "display=$DISPLAY" "sample=bell.ogg" > /dev/null
    /usr/bin/pactl load-module module-x11-cork-request "display=$DISPLAY" > /dev/null

    if [ x"$KDE_FULL_SESSION" = x"true" ]; then
       /usr/bin/pactl load-module module-device-manager "do_routing=1" > /dev/null
    fi

    if [ x"$SESSION_MANAGER" != x ] ; then
    /usr/bin/pactl load-module module-x11-xsmp "display=$DISPLAY session_manager=$SESSION_MANAGER" > /dev/null
    fi
    /usr/bin/pactl load-module module-bluetooth-discover
fi

```
Lets look at all of them just to be sure
```
gedit /etc/pulse/default.pa
```
And
```
gedit /usr/bin/start-pulseaudio-x11
```
And let me see your audio.conf
```
gedit /etc/bluetooth/audio.conf
```
But yes we can undo all that we did here if needed.

---

### Post by kate.t on 2016-09-11
gedit /etc/pulse/default.pa :

```
#load-module module-bluetooth-discover
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/freedesktop/stereo/bell.oga
#load-sample-lazy pulse-hotplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-coldplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-access /usr/share/sounds/freedesktop/stereo/message.oga

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Should be after module-*-restore but before module-*-detect
load-module module-switch-on-port-available

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif

.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music/video streams when a phone stream is active
#load-module module-role-cork

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

gedit /usr/bin/start-pulseaudio-x11 :

```
#!/bin/sh

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

set -e

if [ x"$DISPLAY" != x ] ; then

    /usr/bin/pactl load-module module-x11-publish "display=$DISPLAY" > /dev/null
    /usr/bin/pactl load-module module-x11-bell "display=$DISPLAY" "sample=bell.ogg" > /dev/null
    /usr/bin/pactl load-module module-x11-cork-request "display=$DISPLAY" > /dev/null

    if [ x"$KDE_FULL_SESSION" = x"true" ]; then
       /usr/bin/pactl load-module module-device-manager "do_routing=1" > /dev/null
    fi

    if [ x"$SESSION_MANAGER" != x ] ; then
    /usr/bin/pactl load-module module-x11-xsmp "display=$DISPLAY session_manager=$SESSION_MANAGER" > /dev/null
    fi
/usr/bin/pactl load-module module-bluetooth-discover
fi
```

gedit /etc/bluetooth/audio.conf

```
# Configuration file for the audio service

# This section contains options which are not specific to any
# particular interface
[General]

# Switch to master role for incoming connections (defaults to true)
Master=true

# If we want to disable support for specific services
# Defaults to supporting all implemented services
Disable=Gateway,Source,Socket

# SCO routing. Either PCM or HCI (in which case audio is routed to/from ALSA)
# Defaults to HCI
SCORouting=PCM

# Automatically connect both A2DP and HFP/HSP profiles for incoming
# connections. Some headsets that support both profiles will only connect the
# other one automatically so the default setting of true is usually a good
# idea.
AutoConnect=true

# Headset interface specific options (i.e. options which affect how the audio
# service interacts with remote headset devices)
[Headset]

# Set to true to support HFP, false means only HSP is supported
# Defaults to true
HFP=true

# Maximum number of connected HSP/HFP devices per adapter. Defaults to 1
MaxConnected=1

# Set to true to enable use of fast connectable mode (faster page scanning)
# for HFP when incoming call starts. Default settings are restored after
# call is answered or rejected. Page scan interval is much shorter and page
# scan type changed to interlaced. Such allows faster connection initiated
# by a headset.
FastConnectable=false

# Just an example of potential config options for the other interfaces
#[A2DP]
#SBCSources=1
#MPEG12Sources=0


```

---

### Post by #&amp;thj^% on 2016-09-11
Well here is one error...your reads
```
.ifexists module-bluetooth-discover.so
_**load-module module-bluetooth-discover**_
.endif
```
Should Read
```
# load-module module-bluetooth-discover
```
Notice the hash in front.
And this also in audio.conf
```
# Automatically connect both A2DP and HFP/HSP profiles for incoming
# connections. Some headsets that support both profiles will only connect the
# other one automatically so the default setting of true is usually a good
# idea.
#AutoConnect=true
```
The Hash in front of "**AutoConnect=true**" needs to be there..:P
In fact just copy and paste mine from above into yours...replacing all.
If you are unsure just ask me.

[/CODE]

---

### Post by kate.t on 2016-09-11
OK, I fixed it up (sorry for the errors), and will reboot now.

---

### Post by kate.t on 2016-09-11
Sadly, no. No change.

At least my fiddling workaround still works.

---

### Post by #&amp;thj^% on 2016-09-11
I'm still not convinced....but we can look at this again tomorrow.
My Wife is about to skin me alive right about now...but no worries I run way faster than her. Ha!;)
Maybe go back and reread and compare yours to what I have.
We will either fix this or return it back to the way it was...but I know this works.
That's my story and I'm sticking to it.:wink:
Kind Regards kiddoo.

---

### Post by kate.t on 2016-09-11
Run like the wind! ;)

I'll be here. Ain't goin' nowhere! :)

Thanks for everything!

Kathleen

---

### Post by kate.t on 2016-09-12
I'm not finding differences, although I must say looking at this stuff makes me cross-eyed.8-[

I copied and pasted your audio.conf file, deleting the original one, so there shouldn't be any errors there.

The mystery continues...

Kathleen

---

### Post by #&amp;thj^% on 2016-09-13
> **kate.t said:**
> I'm not finding differences, although I must say looking at this stuff makes me cross-eyed.8-[

I copied and pasted your audio.conf file, deleting the original one, so there shouldn't be any errors there.

The mystery continues...

Kathleen

Well Ok then...but before we undo all of my efforts here... try one more thing for me if you would.
After shutting down for the day...pull your receiver to the headphone out, and leave it out while booting fresh, then plug in the receiver back in after it has booted up.
Then tell me if that gets them discovered by blueman with the option to connect to A2DP.
**EDIT**: I keep forgetting to ask, but are you using suspend or hibernation when you are done for the day? (I suspect Not but could be important if you are.)

---

### Post by kate.t on 2016-09-13
Sorry for the delay in response, I've been up to my eyeballs in work, rush jobs.

I did what you requested. I had to bring up blueman manually (because after the changes I made it doesn't show up on start-up). The headphones are discovered just fine, and connected, and the option to connect to A2DP is there. However, as usual, it gives me the failure message for getting in A2DP mode. Then I fiddle, turning off audio sink, turning it on again, switching to HSF/HPF mode, then switching back to A2DP. Switching a couple of times works.

In other words, my workaround is still working.

When I'm done work with my computer for the day, I just leave it on with my browsers' tabs still up. I don't intentionally hibernate or suspend.

Thanks for your questions!!!

Kathleen

---

### Post by #&amp;thj^% on 2016-09-14
> **kate.t said:**
> Sorry for the delay in response, I've been up to my eyeballs in work, rush jobs.

I did what you requested. I had to bring up blueman manually (because after the changes I made it doesn't show up on start-up). The headphones are discovered just fine, 
No worries on the delay I get the time priorities.:) Life is very busy as of late for both of us.
> **kate.t said:**
> 
the option to connect to A2DP is there. However, as usual, it gives me the failure message for getting in A2DP mode. 

This is the most puzzling to me...the hack, or change I made has been working flawlessly 100% of the time for me and a friend. **But **with some newer Bose bluetooth Headphones. (Bose QuietComfort 25 Acoustic Noise Cancelling Headphones for Apple devices) off topic... but boy are these things a bit spendy :o
> **kate.t said:**
> When I'm done work with my computer for the day, I just leave it on with my browsers' tabs still up. I don't intentionally hibernate or suspend.

With the Lid to the laptop Up....or Down?
I'm going to wait till we are both on-line together.

---

### Post by kate.t on 2016-09-14
Hi again!

Occasionally the lid is closed, but usually it's up. Does that matter?

Kathleen

---

### Post by #&amp;thj^% on 2016-09-14
Yes it could..
When it is down and then opened, are you prompted to enter a password?

---

### Post by kate.t on 2016-09-14
No, I turned that off.

---

### Post by #&amp;thj^% on 2016-09-14
And after you open the lid are the headphones still connected with stereo?

---

### Post by kate.t on 2016-09-14
I'll have to try that. I normally have the headphones off when I close the lid. Will try it now.

---

### Post by kate.t on 2016-09-14
No, after I shut the lid, after a few seconds the headphones turned themselves off. When I opened the lid and restarted the headphones, I had to go back to using my workaround to get the headphones back in stereo.

---

### Post by #&amp;thj^% on 2016-09-14
That is what I thought...humm?
Are you ok with leaving things the way we have them for now? (Answer honestly)
There is some kind of interrupt or intercept going on here...but I need to get my head around this for a bit.(Think about it more):-k
And I need to see if this happens with my buddy's also.
EDIT: and just to be sure we are checking things together you will need this setting.
Click the icon at the very right of the menu bar and select System Settings.
    In the Hardware section, click Power.
    Set the drop-down menus next to When the lid is closed to Do nothing.
Let me know Ok?

---

### Post by kate.t on 2016-09-14
Things can stay the way they are for now because I am able to get the headphones to work with stereo if I just do my workaround rigamarole. 

I changed the power setting to now "do nothing" when closing the lid.

Happy thinking!!! :KS

Thank you so much for your effort!! =d>

Kathleen

---

### Post by #&amp;thj^% on 2016-09-14
Ok now that you changed the setting see if stays closing the lid pause a bit and reopen...now check if they are connected in stereo mode.
kate you are very welcome :D..and thanks for being my tester on this.
Pretty soon you will be active in the[SIZE=3] Forum: Ubuntu Development Version....You never know.:grin:
[SIZE=2]Cheers[/SIZE]
[/SIZE]

---

### Post by kate.t on 2016-09-14
OK, so I turned on the headphones, went through the magical workaround, then closed the lid...took several sips of the tasty coffee sitting on the table...opened the lid, and hooray! Still in stereo.

> Pretty soon you will be active in the[SIZE=3] Forum: Ubuntu Development Version....You never know.:grin:[/SIZE]

You almost made me spit out my coffee with that thought!

Glad to be your guinea pig. :D

Do you still think it possible that some day I may not need to go through the magical workaround?

Kathleen

---

### Post by #&amp;thj^% on 2016-09-14
> **kate.t said:**
> 
You almost made me spit out my coffee with that thought!

Kathleen

:o Careful there girlfriend you could stain your lappy...:lolflag:
You are such a treat.
But I am a optimist...where there is a will there is a way...I "try" to stay on the high road...there is less traffic there.:D
Let me know if anything changes (with the new setting in power) while I melt my brain down some more.:o (Not that I had a lot left to melt in the first place)

---

### Post by #&amp;thj^% on 2016-09-15
kate.t could you give me the out put of this from the terminal
```
bt-device -l
```
And this also
```
apt-cache policy pulseaudio-module-bluetooth
```

---

### Post by kate.t on 2016-09-15
Hello, 1fallen!

bt-device -l

```
Added devices:
MDR-ZX770BT (AC:9B:0A:6C:EA:FF)

```

apt-cache policy pulseaudio-module-bluetooth

```
pulseaudio-module-bluetooth:
  Installed: 1:8.0-0ubuntu3
  Candidate: 1:8.0-0ubuntu3
  Version table:
 *** 1:8.0-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

Hope this helps!!

Kathleen

---

### Post by #&amp;thj^% on 2016-09-15
Ok Thanks!
Tell me what [s]happens or[/s] just paste back the output of this in terminal
```
bt-adapter -d

```

---

### Post by kate.t on 2016-09-15
A mysterious result:

"bt-adapter -d" produces this:

```
 Searching... 
```

and that's it. It sits there searching for what looks to be forever. It's been almost 10 minutes now and nothing is happening. What on earth does this mean?

Kathleen

---

### Post by #&amp;thj^% on 2016-09-15
That is the mystery...right there!!! That will or should tell me that it is paired...even though you see it in blueman.
Hummm?? Well that blows my work around out the water. Something is not configured right or installed.
I need this to work before I can do anything else.  
I need to get a hold of the Bluez maintainer to see if he can shed some light on this and I hope he can help because I just won't talk to the pulseaudio guy.:P
I have all my notes and modifications made here.
Stay tuned..

---

### Post by jeremy31 on 2016-09-15
1fallen
I get the same results as kate.t with that command even with the headset working in A2DP.  I have tried a few old tricks to disable HFP/HSP and they don't seem to be working.  I have spent some time looking for my micro USB bluetooth adapter, a GBU521 that I know didn't support HSP/HFP without loading the firmware in 14.04

There must be something happening specific to the headphones as I see the same issue with Intel, Atheros, and an older Broadcom USB bluetooth dongle

---

### Post by kate.t on 2016-09-15
Am tuned in... :)

Kathleen

---

### Post by #&amp;thj^% on 2016-09-15
> **jeremy31 said:**
> 1fallen
I get the same results as kate.t with that command _**even with the headset working in A2DP.**_  I have tried a few old tricks to disable HFP/HSP and they don't seem to be working.  I have spent some time looking for my micro USB bluetooth adapter, a GBU521 that I know didn't support HSP/HFP without loading the firmware in 14.04

There must be something happening specific to the headphones as I see the same issue with Intel, Atheros, and an older Broadcom USB bluetooth dongle

Thanks jeremy31....[s]do you also see it with your known working headset??[/s]
Check that I **see now** that it dose...I've been in touch with dlech and waiting for a reply
This is all I got back for now...
> BlueZ 5 dropped support for alsa [1], so the solution for now (until someone updates some bluez-alsa project for BlueZ 5) is to use PulseAudio.

PulseAudio 5 only supports the A2DP profile and not HSP/HFP [2] (although it his under development [3]).
I will spend some time with him...going over what has happened here.

> **jeremy31 said:**
> 1fallen
There must be something happening specific to the headphones as I see  the same issue with Intel, Atheros, and an older Broadcom USB bluetooth  dongle
That is what I was going to control (Or try to) by forcing the specific Device and address to use  the A2DP profile....but if this is not in pristine working order... could bring her system to a bad state.
And I have not seen what would actually happen with the change...so cooler heads prevail.

---

### Post by #&amp;thj^% on 2016-09-16
(fiendish chuckle):rolleyes:Ok are you ready to get wild...:lol:
But we move very slowly at first...what dose this show from the terminal
```
apt-cache policy bluez
```

---

### Post by kate.t on 2016-09-16
Woooo hoooo!!! Ready to go wild!!!:guitar: But I'll take it slow...


```
bluez:
  Installed: 5.37-0ubuntu5
  Candidate: 5.37-0ubuntu5
  Version table:
 *** 5.37-0ubuntu5 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

Kathleen

---

### Post by #&amp;thj^% on 2016-09-16
> **kate.t said:**
> Woooo hoooo!!! Ready to go wild!!!:guitar: But I'll take it slow...

Kathleen
That's my girl ;) And that is the version I wanted to see.
I'm going to re-write a few files here... so show me these files with all the content that shows in them.
```
gedit /etc/pulse/default.pa
```
And there should not be anything in this one.. but show me anyway.
```
gedit /etc/udev/rules.d/10-local.rules

```

---

### Post by kate.t on 2016-09-16
OK, here is gedit /etc/pulse/default.pa:

```
#load-module module-bluetooth-discover
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/freedesktop/stereo/bell.oga
#load-sample-lazy pulse-hotplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-coldplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-access /usr/share/sounds/freedesktop/stereo/message.oga

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Should be after module-*-restore but before module-*-detect
load-module module-switch-on-port-available

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif

.ifexists module-bluetooth-discover.so
#load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music/video streams when a phone stream is active
#load-module module-role-cork

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input 
```

And 
gedit /etc/udev/rules.d/10-local.rules 

was blank, nothing there.

---

### Post by #&amp;thj^% on 2016-09-16
> **kate.t said:**
> OK, here is gedit /etc/pulse/default.pa:

And 
gedit /etc/udev/rules.d/10-local.rules 

was blank, nothing there.
Ok perfect and as i thought that should have been blank...but seeing how I did not install your system I needed to check that "/etc/udev/rules.d/10-local.rules"
Just to take any chance out of it.
I'm testing this now to be sure nothing catastrophic happens here.... So give me a couple hours here..please:D

---

### Post by kate.t on 2016-09-16
>   So give me a couple hours here..please:grin: 				 			  			   		 			 				 			 			 				

Take whatever you need!

Bless you for all your efforts!!!:KS

Kathleen

---

### Post by #&amp;thj^% on 2016-09-16
> **kate.t said:**
> Take whatever you need!

Bless you for all your efforts!!!:KS

Kathleen

I am very much a sound man...got to have it just perfect or I am not a happy guy...:(
See you in a bit.

---

### Post by #&amp;thj^% on 2016-09-16
[COLOR=#ff0000][SIZE=4]EDIT kate.t Wait to do this until I say proceed. 
[/SIZE][/COLOR][SIZE=4][SIZE=2]jeremy31 just tried this with his set-up and it is failing to start pulse-daemon[/SIZE][/SIZE]
<Snip Removed code>
Next we are going to make the file "/etc/udev/rules.d/10-local.rules"
With this command
```
sudo -H gedit /etc/udev/rules.d/10-local.rules
```
Now add the following and save it
```
# Set bluetooth power up
ACTION=="add", SUBSYSTEM=="bluetooth", KERNEL=="hci[0-9]*", RUN+="/usr/bin/hciconfig %k up"
```

[s]Reboot[/s] This time completely power off... wait about 30 to 40 seconds and Power on your laptop. 
With some luck this will be all we need to have the headset in stereo.

If not I still have a couple of hacks we can add.

---

### Post by #&amp;thj^% on 2016-09-16
@jeremy will you try this in "/etc/pulse/default.pa"
```

#load-module module-bluetooth-discover
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/freedesktop/stereo/bell.oga
#load-sample-lazy pulse-hotplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-coldplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-access /usr/share/sounds/freedesktop/stereo/message.oga

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Should be after module-*-restore but before module-*-detect
load-module module-switch-on-port-available

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif

.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2  rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music/video streams when a phone stream is active
#load-module module-role-cork

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```
This is the "/etc/pulse/default.pa"
Let me know and thanks bud.

---

### Post by jeremy31 on 2016-09-16
I had some time to work on this recently and it might be caused by a couple of things
1  The Sony headset has volume controls
2  The Sony headset has a microphone built in

I have another bt headset and I have the same issues with it now as the Sony and it is a Philips SHB4000 and it has a mic and volume controls, however my cheap bt speaker with no mic or volume controls connects in A2DP with left/right stereo controls every time I connect.

I am thinking this is an issue with pulse more than bluetooth as I also have a Logitech  headset that has it's own dongle.  It uses bluetooth but is seen as an USB headset, it has a microphone and volume controls but audio doesn't work in 16.04 either as in no sound through them...this is driving me crazy as the Logitech and Philips headsets worked in Ubuntu 15.10

---

### Post by jeremy31 on 2016-09-16
> **1fallen said:**
> @jeremy will you try this in "/etc/pulse/default.pa"
```

#load-module module-bluetooth-discover
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/freedesktop/stereo/bell.oga
#load-sample-lazy pulse-hotplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-coldplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-access /usr/share/sounds/freedesktop/stereo/message.oga

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Should be after module-*-restore but before module-*-detect
load-module module-switch-on-port-available

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif

.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2  rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music/video streams when a phone stream is active
#load-module module-role-cork

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```
This is the "/etc/pulse/default.pa"
Let me know and thanks bud.

same thing with this one also

---

### Post by #&amp;thj^% on 2016-09-16
> **jeremy31 said:**
> 
_**I am thinking this is an issue with pulse more than bluetooth **_as I also have a Logitech  headset that has it's own dongle.  It uses bluetooth but is seen as an USB headset, it has a microphone and volume controls but audio doesn't work in 16.04 either as in no sound through them...this is driving me crazy as the Logitech and Philips headsets worked in Ubuntu 15.10
Me Too!!:D

> **jeremy31 said:**
> same thing with this one also
Well Crap...My head is just mush right now...need to step away from it for a spell..and regroup.LOL
More to come...And a Big Thanks jeremy for helping out.:KS

---

### Post by kate.t on 2016-09-16
I'm still here. I may not know what's going on:confused:, but I'm still checking back to see. 

Thanks, guys!!! :)

---

### Post by #&amp;thj^% on 2016-09-16
> **kate.t said:**
> I'm still here. I may not know what's going on:confused:, but I'm still checking back to see. 

Thanks, guys!!! :)
Hehe I am glad you waited...jeremey31 took the bullet for you.:)
I just can not believe that this is just not a quick fix. ](*,)
I'm going to have to shoot the author of pulseaudio though.:smile:
Err I mean shoot him a line...LOL:-\"

---

### Post by kate.t on 2016-09-16
All this talk of bullets makes me want to duck, LOL!!

>  I just can not believe that this is just not a quick fix. ](*,)

I know. I'm kind of surprised we're into page 14 of this discussion...

Oh, well...what did Scarlett O'Hara say? "Tomorrow is another day!"

Kathleen

---

### Post by jeremy31 on 2016-09-17
Found a code snippet on askubuntu [http://askubuntu.com/questions/765233/pulseaudio-fails-to-set-card-profile-to-a2dp-sink-how-can-i-see-the-logs-and](http://askubuntu.com/questions/765233/pulseaudio-fails-to-set-card-profile-to-a2dp-sink-how-can-i-see-the-logs-and)
```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect AC:9B:0A:6C:EA:FF\n quit"|bluetoothctl;sleep 5; echo -e "connect AC:9B:0A:6C:EA:FF\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
```

It works when my Sony headset is stuck in HFP/HSP.  I did change the MAC to match kate.t headphones

---

### Post by #&amp;thj^% on 2016-09-17
> **jeremy31 said:**
> Found a code snippet on askubuntu [http://askubuntu.com/questions/765233/pulseaudio-fails-to-set-card-profile-to-a2dp-sink-how-can-i-see-the-logs-and](http://askubuntu.com/questions/765233/pulseaudio-fails-to-set-card-profile-to-a2dp-sink-how-can-i-see-the-logs-and)
```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect AC:9B:0A:6C:EA:FF\n quit"|bluetoothctl;sleep 5; echo -e "connect AC:9B:0A:6C:EA:FF\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
```

It works when my Sony headset is stuck in HFP/HSP.  I did change the MAC to match kate.t headphones

Nice :) Good find!
This is probably the closest thing to a fix or work-around there is ATM.
kate.t you should be able to run the code jeremy31 has provided...and let us know how it works:)

---

### Post by kate.t on 2016-09-17
Hi, guys! Thanks, Jeremy!

Here's what happened when I put that code in with the headphones off:

```
 pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect AC:9B:0A:6C:EA:FF\n quit"|bluetoothctl;sleep 5; echo -e "connect AC:9B:0A:6C:EA:FF\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
You need to specify a profile by its name.
[NEW] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
[NEW] Device 94:23:6E:0D:11:EA Tower Stereo
[NEW] Device AC:9B:0A:6C:EA:FF MDR-ZX770BT
[bluetooth]# disconnect AC:9B:0A:6C:EA:FF
Attempting to disconnect from AC:9B:0A:6C:EA:FF
[bluetooth]#  quit
[DEL] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
[NEW] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
[NEW] Device 94:23:6E:0D:11:EA Tower Stereo
[NEW] Device AC:9B:0A:6C:EA:FF MDR-ZX770BT
[bluetooth]# connect AC:9B:0A:6C:EA:FF
Attempting to connect to AC:9B:0A:6C:EA:FF
[bluetooth]#  quit
[DEL] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
You need to specify a profile by its name. 
```

Here's what happened when I ran the code with the headphones on:

```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect AC:9B:0A:6C:EA:FF\n quit"|bluetoothctl;sleep 5; echo -e "connect AC:9B:0A:6C:EA:FF\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
[NEW] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
[NEW] Device 94:23:6E:0D:11:EA Tower Stereo
[NEW] Device AC:9B:0A:6C:EA:FF MDR-ZX770BT
[bluetooth]# disconnect AC:9B:0A:6C:EA:FF
Attempting to disconnect from AC:9B:0A:6C:EA:FF
[bluetooth]#  quit
[DEL] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
[NEW] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
[NEW] Device 94:23:6E:0D:11:EA Tower Stereo
[NEW] Device AC:9B:0A:6C:EA:FF MDR-ZX770BT
[bluetooth]# connect AC:9B:0A:6C:EA:FF
Attempting to connect to AC:9B:0A:6C:EA:FF
[bluetooth]#  quit
[DEL] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
Failed to set card profile to 'a2dp_sink'.  
```

I am going to reboot now to see if anything is different.

Kathleen

---

### Post by jeremy31 on 2016-09-17
The poster on askubuntu said that a few times the sleep timer needed to be 5 seconds or it wouldn't switch the profile
```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 5 ; echo -e "disconnect AC:9B:0A:6C:EA:FF\n quit"|bluetoothctl;sleep 5; echo -e "connect AC:9B:0A:6C:EA:FF\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
```

---

### Post by kate.t on 2016-09-17
Well, it's different and it's not different.

What's not different is when I turn on the headset and go to Sound Settings, it's in HSF/HSP mode and mono sound mode. Switching in the Sound Settings to A2DP doesn't work.

What's different is that the part of blueman I was using to do my magic fix, namely, clicking on the icon and then choosing "Devices" doesn't work at all. There is a spinning circle which eventually gives up the ghost, and then nothing happens. No list of devices pops up for me to then run my rigamarole on (switching modes back and forth). 

I did, however, find a new fix for my headphones to get stereo. I have to run "find new device" in blueman. That window does come up, and lets me re-pair and reconnect. When I do that, and then go into Sound Settings, I'm able to switch to A2DP and the headphones are in stereo. When I turn off the head phones and then turn them on again, I have to run "find new device" all over again.

Well, that's the latest. I'm not fond of the fact that I lost some blueman functionality. 

I hesitate to tell you this, but my tower stereo speakers won't work, I get the message that bluetooth and the speakers paired successfully, but failed to connect.

I only mention this in case it gives you any clues to the headphone situation. 

Kathleen

---

### Post by kate.t on 2016-09-17
This was the output from the second string of code:

```
 [NEW] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
[NEW] Device AC:9B:0A:6C:EA:FF MDR-ZX770BT
[NEW] Device 94:23:6E:0D:11:EA Tower Stereo
[bluetooth]# disconnect AC:9B:0A:6C:EA:FF
Attempting to disconnect from AC:9B:0A:6C:EA:FF
[bluetooth]#  quit
[DEL] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
[NEW] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
[NEW] Device AC:9B:0A:6C:EA:FF MDR-ZX770BT
[NEW] Device 94:23:6E:0D:11:EA Tower Stereo
[bluetooth]# connect AC:9B:0A:6C:EA:FF
Attempting to connect to AC:9B:0A:6C:EA:FF
[bluetooth]#  quit
[DEL] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
 
```

I'm about to reboot.

---

### Post by kate.t on 2016-09-17
Well, now when I click on "Devices" in blueman I get the list of devices again. That's good. (I think.) This enables me to employ my finagling right there (switching to HSF/HFP, disconnecting from audio sink, reconnecting audio sink, switching to A2DP sink, then switching to A2DP sink in "Sound Settings"). Then the headphones work in stereo.

So I guess I'm back to where i was (in terms of function) before trying this new code.

(Tower stereo is still incommunicado.)

Hope this makes some sense or helps in some way!:)

Kathleen

---

### Post by jeremy31 on 2016-09-18
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324)
Seems to be related, going to see about building pulse from source omitting some patches

Edit: didn't seem to help any

---

### Post by #&amp;thj^% on 2016-09-19
> **jeremy31 said:**
> [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324)
Seems to be related, going to see about building pulse from source omitting some patches

Edit: didn't seem to help any

Thanks for the Bug Link....and as I said earlier in this thread.
> Also just tested with arch, and it works just fine. So it has something to do with Ubuntu.
But kernel and pulseaudio are newer.
```
pulseaudio --version && uname -r
pulseaudio 9.0
4.7.4-1-ARCH

```
I'm not sure when ubuntu will upgrade to pulse -V 9.0 but I think we might have better success with it.
I have always thought that 16.04 had a very buggy pulseaudio
In that bug report I see where a user was able to downgrade pulse and seemed to work for them....but I am hesitant to suggest that.
I think we are just spinning our wheels here now.:(

---

### Post by kate.t on 2016-09-19
Well, at least I can make the headphones work through the switching-back-and-forth and on-and-off method! It's a pain in the neck, but it'll have to do for now.

Thank you, 1fallen and jeremy31, for all your efforts!!!

Kathleen

---

### Post by #&amp;thj^% on 2016-09-19
Your very welcome kate...but kind of hard for me to admit to defeat here...
Check in here once in a while...will keep this updated with anything new.

---

### Post by jeremy31 on 2016-09-25
All I have been able to do is break things, spent the last half hour reinstalling things in terminal because I could login to the desktop

---

### Post by #&amp;thj^% on 2016-09-27
> **jeremy31 said:**
> All I have been able to do is break things, spent the last half hour reinstalling things in terminal because I could login to the desktop

:( I feel your pain jeremy31...but I am getting closer by compiling PA from source...with a handful of hacks.
BTW Yackkety has the same results as Xenial. (Just for Information Only)
kate.t see if you can understand this thread....[https://ubuntuforums.org/showthread.php?t=2210602](https://ubuntuforums.org/showthread.php?t=2210602)
_**Do not actually do it **_...just browse through it. Let me know if you feel you could do this if asked. (But it will also have some hacks I have added.)

---

### Post by kate.t on 2016-09-28
> **1fallen said:**
> 
kate.t see if you can understand this thread....[https://ubuntuforums.org/showthread.php?t=2210602](https://ubuntuforums.org/showthread.php?t=2210602)
_**Do not actually do it **_...just browse through it. Let me know if you feel you could do this if asked. (But it will also have some hacks I have added.)

Hello again, 1fallen! Sorry I wasn't around yesterday when you posted.

If you're asking me if I understand what it is the folks in that thread are doing, I must confess that I have not one single respectable clue. :confused:

On the other hand, I do know how to copy and paste and generally follow directions. :D 
Will that suffice?

Kathleen

---

### Post by #&amp;thj^% on 2016-09-28
> **kate.t said:**
> Hello again, 1fallen! Sorry I wasn't around yesterday when you posted.

If you're asking me if I understand what it is the folks in that thread are doing, I must confess that I have not one single respectable clue. :confused:

[U][B]On the other hand, I do know how to copy and paste and generally follow directions. :D 
Will that suffice?
[/B][/U]
Kathleen
Yes that will work._**:grin: **_One of those folks in there is me incognito.[U][B]:-$
[/B][/U]I am going to see if jereemy31 will test it when I am done_>>>_But I need to borrow the headset again from an old chum of mine.
So might be be a day or two or three[U][B]:grin:
[/B][/U]@jereemy31 Let me know if you are willing to do this.(PM me);)

---

### Post by #&amp;thj^% on 2016-10-14
Hi kate.t there has been some work done on this now...and I have seen some good results with the fix.
**This PPA is for Xenial only (16.04)**
> Pulseaudio fix for A2DP
PPA description

This PPA is meant to fix this: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324)
Adding this PPA to your system
You can update your system with unsupported packages from this untrusted  PPA by adding ppa:vooze/pulseaudio-fix to your system's Software  Sources. (Read about installing)

Just run these two lines for now.
```
sudo add-apt-repository ppa:vooze/pulseaudio-fix
sudo apt-get update
```
Now before saying yes to any changes being made by this last command (Below this line)...copy and paste back here so we can look at it first.(For Safety)
```
sudo apt-get dist-upgrade 
```
        
Again copy and paste back here so we can look at it first before accepting the changes.
As this will tell us what is getting removed so we have an idea before hand.

---

### Post by kate.t on 2016-10-14
Hi, 1fallen!

Let me see if I understand this correctly.

For the following:

```
sudo apt-get dist-upgrade


```

I should paste this line and hit the enter key, at which point there will be some changes listed which are not, however, undertaken unless and until I press "Y" for yes.  And that I should copy the changes from the terminal and post them back here before giving assent. Do I have that right?

Thanks!

Kathleen

---

### Post by #&amp;thj^% on 2016-10-14
No just use your mouse and highlight the text in the terminal and right click on the highlighted text and you will see copy.... use that and paste it back here.
Using Code tags of course.:)

---

### Post by kate.t on 2016-10-14
Here's the result of the dist-upgrade command:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-36 linux-headers-4.4.0-36-generic linux-headers-4.4.0-38
  linux-headers-4.4.0-38-generic linux-image-4.4.0-36-generic
  linux-image-4.4.0-38-generic linux-image-extra-4.4.0-36-generic
  linux-image-extra-4.4.0-38-generic linux-signed-image-4.4.0-36-generic
  linux-signed-image-4.4.0-38-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  libpam-systemd libpulse-mainloop-glib0 libpulse0 libpulse0:i386 libpulsedsp
  libsystemd0 libsystemd0:i386 libudev1 libudev1:i386 linux-libc-dev
  pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11
  pulseaudio-utils systemd systemd-sysv udev xserver-common xserver-xorg-core
19 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,708 kB of archives.
After this operation, 1,839 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

Shall I say Yes?

Kathleen

---

### Post by #&amp;thj^% on 2016-10-14
Perfect:D...Yes go ahead now with the changes.
And before you reboot...use this command...and say yes to this also
```
sudo apt autoremove
```
Just doing some tidying up. (Remove some older kernels)
When that is done...Reboot your lappy.
You should now have the option for A2DP in sound settings for your paired headphones.

---

### Post by kate.t on 2016-10-14
I'm so sorry to have to tell you it didn't work.:(

I get "device added successfully, but failed to connect".

It *tries* to connect, I see the Blueman icon change back and forth until it just gives up. I'm glad you said this can be undone, if necessary. You *did *say that, right?;)

Kathleen

---

### Post by #&amp;thj^% on 2016-10-14
I can neither confirm or deny that statement.....LOL....But Yes it can be undone.:wink:
Well you might have to get it to connect with HSP/HSF first. Or even try your work around.
One of the testers there had reported this the first time.
> Unfortunately, after turning the  headphones off/on, the headphones immediately reconnected and defaulted  to the A2DP profile, but there was no sound.  I then changed the profile  to HSP/HSF and heard low quality audio.  Changing back to A2DP resulted  in silence.  I toggled between the two profiles a few times and the  issue persisted.
 I then powered off/on once again, and this time I was able to properly select the A2DP profile and hear perfect audio!
 So, the connection issue seems to be fixed (for me, atleast)!  There  seems to be something that is a little bit strange with the audio  profile selection, although there may be some user error involved here.   I'll try and repeat my power cycling tests a few more times and see if  the issue is a software problem or a user problem.



---

### Post by kate.t on 2016-10-14
I don't know how I would be able to try with the HSP/HSF, with or without my entire workaround, since the message is "device added successfully, but failed to connect". Initially, both blueman and the bluetooth choice in Settings show multiple attempts to connect, for a mere fraction of a second. Then it gives up the ghost entirely. There is no opportunity to get to any audio choice.

Kathleen

---

### Post by kate.t on 2016-10-14
I forgot to mention that I also tried rebooting again. Booting seems to be taking longer than usual, for what it's worth. Or maybe I'm imagining it?

---

### Post by #&amp;thj^% on 2016-10-14
Humm? I may have to give Luke this page to view then...as he is getting ready to release this in regular updates soon for Xenial and Yakkety.
Well lets go back then to what you had before.:(
```
sudo apt-get install ppa-purge
```
And then remove the PPA, downgrading gracefully packages it provided to packages provided by official repositories:
```
sudo ppa-purge ppa:vooze/pulseaudio-fix
```
And Again let the package manager know of the changes made
```
sudo apt update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
And clean out the un-needed packages
```
sudo apt autoremove
```
A Reboot will be needed for the changes.
Kate I am all out of advice now for this problem.:(
But it seems to work for others.

---

### Post by jeremy31 on 2016-10-14
That was not from Luke's PPA, I think that is Joakim's.  Luke's PPA is themuso IIRC

---

### Post by kate.t on 2016-10-14
1fallen,

Bad news here. After carefully carrying out each command and rebooting, I still get the message "Device added successfully, but failed to connect".:(

This means I can't use my headphones at all. Is there anything else I can do to turn back the experimental clock, or am I stuck?:confused:

> Kate I am all out of advice now for this problem.:sad:
But it seems to work for others. 				

Well, blessings upon thee for having tried so hard for so long!!!

Kathleen

---

### Post by kate.t on 2016-10-14
1fallen,

Bad news here. After carefully carrying out each command and rebooting, I still get the message "Device added successfully, but failed to connect".:(

This means I can't use my headphones at all. Is there anything else I can do to turn back the experimental clock, or am I stuck?:confused:

> Kate I am all out of advice now for this problem.:sad:
But it seems to work for others. 				

Well, blessings upon thee for having tried so hard for so long!!!

Kathleen

---

### Post by #&amp;thj^% on 2016-10-14
> **jeremy31 said:**
> That was not from Luke's PPA, I think that is Joakim's.  Luke's PPA is themuso IIRC
Are they the same pulseaudio packages?

> **kate.t said:**
> 1fallen,

Bad news here. After carefully carrying out each command and rebooting, I still get the message "Device added successfully, but failed to connect".:(

This means I can't use my headphones at all. Is there anything else I can do to turn back the experimental clock, or am I stuck?:confused:



Well, blessings upon thee for having tried so hard for so long!!!

Kathleen
Still working on this kate... but that should have turned back the experimental clock.
EDIT: Try unplugging the device and leave it un-plugged...now reboot and plug the device back in.

---

### Post by jeremy31 on 2016-10-14
I don't think the PPA's are the same, Luke's was updated in the last couple days and Joakim hasn't made any changes in 2 weeks

Luke commented that the profile selection is a separate bug so I may have to search for that bug report

---

### Post by #&amp;thj^% on 2016-10-14
> **jeremy31 said:**
> I don't think the PPA's are the same, Luke's was updated in the last couple days and Joakim hasn't made any changes in 2 weeks

Luke commented that the profile selection is a separate bug so I may have to search for that bug report

Ok I was miss informed then...Thanks jeremey31.:D

---

### Post by kate.t on 2016-10-14
Unplugging and plugging in again didn't work.:(

Should I be searching the web for fixes to the error message "Device added successfully, but failed to connect"?

Kathleen

---

### Post by #&amp;thj^% on 2016-10-14
Well I don't think so...just waiting for an email here kate.
We might give Luke's (the real Luke's PPA) a whirl.
But i want or need some information first.
Hang tight here for a moment.

---

### Post by #&amp;thj^% on 2016-10-14
Oh I forgot to get this from you...what is the output from the terminal with this code.
```
inxi -A
```
And one more while we are here
```
hcidump
```

---

### Post by kate.t on 2016-10-14
I had to install these programs first. Here you go:

inxi -A

```
Audio:     Card-1 Intel 8 Series HD Audio Controller driver: snd_hda_intel
           Card-2 Intel Haswell-ULT HD Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-43-generic
```

And for hcidump, I had to install it too, I tried running it, but it's stuck at this point for several whole minutes now:

```
HCI sniffer - Bluetooth packet analyzer ver 5.37
device: hci0 snap_len: 1500 filter: 0xffffffffffffffff



```

Is there something I can do to make it finish?

Kathleen

---

### Post by #&amp;thj^% on 2016-10-14
Yes just click inside the terminal and use key combo <Crtl>+<c>
So just keyboard keys Ctrl+c without the +

---

### Post by jeremy31 on 2016-10-14
> **kate.t said:**
> Unplugging and plugging in again didn't work.:(

Should I be searching the web for fixes to the error message "Device added successfully, but failed to connect"?

Kathleen

I would only check one thing after seeing that error ```
pactl list short | grep blue
```
to see if module-bluetooth-discover was loaded

---

### Post by kate.t on 2016-10-14
jeremy31,

This is the only output to that code:

```
8    module-bluetooth-policy
```

Kathleen

---

### Post by kate.t on 2016-10-14
Should I be loading module-bluetooth-discover?

If so, how do I do it? Thanks in advance!

Kathleen

---

### Post by #&amp;thj^% on 2016-10-14
Kate lets have a look at these two files...Paste the content back here with code tags
```
gedit /etc/pulse/default.pa
```
And this also
```
gedit /usr/bin/start-pulseaudio-x11
```

---

### Post by jeremy31 on 2016-10-14
```
pactl load-module module-bluetooth-discover
```

You may also need to try loading module-bluez5-discover using a similar command
```
pactl load-module module-bluez5-discover
```

---

### Post by kate.t on 2016-10-14
1fallen,

Here is the output for gedit /etc/pulse/default.pa


```
#load-module module-bluetooth-discover
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/freedesktop/stereo/bell.oga
#load-sample-lazy pulse-hotplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-coldplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-access /usr/share/sounds/freedesktop/stereo/message.oga

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Should be after module-*-restore but before module-*-detect
load-module module-switch-on-port-available

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif

.ifexists module-bluetooth-discover.so
#load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music/video streams when a phone stream is active
#load-module module-role-cork

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

And here is the output for gedit /usr/bin/start-pulseaudio-x11

```
#!/bin/sh

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

set -e

if [ x"$DISPLAY" != x ] ; then

    /usr/bin/pactl load-module module-x11-publish "display=$DISPLAY" > /dev/null
    /usr/bin/pactl load-module module-x11-bell "display=$DISPLAY" "sample=bell.ogg" > /dev/null
    /usr/bin/pactl load-module module-x11-cork-request "display=$DISPLAY" > /dev/null

    if [ x"$KDE_FULL_SESSION" = x"true" ]; then
       /usr/bin/pactl load-module module-device-manager "do_routing=1" > /dev/null
    fi

    if [ x"$SESSION_MANAGER" != x ] ; then
    /usr/bin/pactl load-module module-x11-xsmp "display=$DISPLAY session_manager=$SESSION_MANAGER" > /dev/null
    fi
fi
```

Kathleen

---

### Post by kate.t on 2016-10-14
Thanks, jeremy31!

Here's the output for  

```
pactl load-module module-bluez5-discover
```

```
Failure: Module initialization failed
```

Kathleen

---

### Post by #&amp;thj^% on 2016-10-14
> **kate.t said:**
> Thanks, jeremy31!

Here's the output for  

```
pactl load-module module-bluez5-discover
```

```
Failure: Module initialization failed
```

Kathleen
1.Was there any errors when you ran this"pactl load-module module-bluetooth-discover"
2.And if you ran that command after giving me the text in "/usr/bin/start-pulseaudio-x11"
I should re-check that file again to see if any changes were made.

---

### Post by kate.t on 2016-10-14
1. No, there were no errors.

2. Here's the new output for  "/usr/bin/start-pulseaudio-x11"

```
#!/bin/sh

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

set -e

if [ x"$DISPLAY" != x ] ; then

    /usr/bin/pactl load-module module-x11-publish "display=$DISPLAY" > /dev/null
    /usr/bin/pactl load-module module-x11-bell "display=$DISPLAY" "sample=bell.ogg" > /dev/null
    /usr/bin/pactl load-module module-x11-cork-request "display=$DISPLAY" > /dev/null

    if [ x"$KDE_FULL_SESSION" = x"true" ]; then
       /usr/bin/pactl load-module module-device-manager "do_routing=1" > /dev/null
    fi

    if [ x"$SESSION_MANAGER" != x ] ; then
    /usr/bin/pactl load-module module-x11-xsmp "display=$DISPLAY session_manager=$SESSION_MANAGER" > /dev/null
    fi
fi
```

Kathleen

---

### Post by kate.t on 2016-10-14
Ooops, I forgot to mention! Sorry about that! The output to the "pactl load-module module-bluetooth-discover" was 23.

Is that an error number? It didn't say "error", just the number.

---

### Post by #&amp;thj^% on 2016-10-14
Ok now we will fix module-bluetooth-discover not loading
There seems to be an issue with some code in Blueman which deliberately unloads module-bluetooth-discover on startup (i.e. after it's been loaded from /etc/pulse/default.pa. )
So we edit the file by
```
sudo -H gedit /usr/bin/start-pulseaudio-x11

```
Now look for lines
```
if [ x”$SESSION_MANAGER” != x ] ; then
    /usr/bin/pactl load-module module-x11-xsmp “display=$DISPLAY session_manager=$SESSION_MANAGER” > /dev/null
   fi
```
Now make it look like this...and proofread to be sure, and save and exit 
```
 if [ x”$SESSION_MANAGER” != x ] ; then
    /usr/bin/pactl load-module module-x11-xsmp “display=$DISPLAY session_manager=$SESSION_MANAGER” > /dev/null
   fi

   # Add the following line:
    /usr/bin/pactl load-module module-bluetooth-discover
fi
```
now reboot.....And say Plleeaassee work.:D

---

### Post by kate.t on 2016-10-14
Well, my hands were clasped in prayer while the laptop was rebooting. To no avail. :(

HOWEVER, perhaps all is not lost. This time there was a *different* error message:

"Connection Failed: blueman.bluez.errors.DBusFailedError: Protocol not available"

What does this mean?

Kathleen

---

### Post by #&amp;thj^% on 2016-10-14
Delete the device from bluetooth devices and pair it again.

---

### Post by kate.t on 2016-10-14
Got all excited there for a minute, but no cigar.

The same error: 
"Connection Failed: blueman.bluez.errors.DBusFailedError: Protocol not available"

If you're fed up with this for today, I won't be disappointed if you quit it now.  You've gone above and beyond the call of duty!:)

Kathleen

---

### Post by #&amp;thj^% on 2016-10-14
A bit tired...and hungry.
Should we pick this up tomorrow then?:)

---

### Post by kate.t on 2016-10-14
Aye, aye, Cap'n! [salutes smartly]

Enjoy your meal and rest!

Kathleen

---

### Post by #&amp;thj^% on 2016-10-14
;) Have a Good Evening.

---

### Post by #&amp;thj^% on 2016-10-15
I can honestly say... I have never had my fanny kicked this bad before.
There has to be something so simple here...maybe like trying to find a needle in a haystack.:)
Lets see if this installed...what is the output of this kate.
```
apt-cache policy pulseaudio-module-bluetooth
```
Oh yeah Good Morning to you.

---

### Post by kate.t on 2016-10-15
Good morning, 1fallen!:)

Here you are:

```
pulseaudio-module-bluetooth:
  Installed: 1:8.0-0ubuntu3
  Candidate: 1:8.0-0ubuntu3
  Version table:
 *** 1:8.0-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status


```

Kathleen

---

### Post by #&amp;thj^% on 2016-10-15
I knew it was installed by the upgrades needed when we used Joakim's PPA
Kate do you want to try another PPA from Luke this time?
I have no idea of the outcome but it could not hurt any worse than we are now.
Everything seems to just work on my end with my hardware and earphones that I have available.
Note: For myself I have not needed any extra PPA's though. Just the edits to files we have already made.

---

### Post by kate.t on 2016-10-15
What the heck! In for a penny, in for a pound. Let's do it!

(Is this reversible, at least in theory?)

Kathleen

---

### Post by #&amp;thj^% on 2016-10-15
Yes at least in theory!:) The same procedure we used with ppa purge.
```
sudo add-apt-repository ppa:themuso/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Now cross your fingers look to the north...and reboot.
But this time unplug your bluetooth receiver and leave it out til it fully boots up.

---

### Post by kate.t on 2016-10-15
Hope springs eternal....[I]but

[/I]No dice.

I'm getting tired of the phrase, "Device added successfully, but failed to connect". That's the error again this time. Too bad it doesn't tell one *why* it failed to connect.:mad:

Kathleen

---

### Post by #&amp;thj^% on 2016-10-15
That makes two then.:(
Lets see if it even sees it now.
Remember codes tags with this
```
pacmd list-sinks
```

---

### Post by kate.t on 2016-10-15
Here you are:

```
2 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_00_03.0.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9950
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_00_03.0>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "0"
        alsa.card_name = "HDA Intel HDMI"
        alsa.long_card_name = "HDA Intel HDMI at 0xc0610000 irq 48"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:03.0"
        sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0a0c"
        device.product.name = "Haswell-ULT HD Audio Controller"
        device.form_factor = "internal"
        device.string = "hdmi:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "Built-in Audio Digital Stereo (HDMI)"
        alsa.mixer_name = "Intel Haswell HDMI"
        alsa.components = "HDA:80862807,80860101,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-0>
  * index: 1
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: front-left: 31187 /  48% / -19.35 dB,   front-right: 31187 /  48% / -19.35 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 1
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 7
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "CX20751/2 Analog"
        alsa.id = "CX20751/2 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xc0614000 irq 47"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9c20"
        device.product.name = "8 Series HD Audio Controller"
        device.form_factor = "internal"
        device.string = "front:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Conexant CX20751/2"
        alsa.components = "HDA:14f1510f,17aa3801,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output-speaker>


```

Hope this helps!

Kathleen

---

### Post by #&amp;thj^% on 2016-10-15
Humm?
What shows for this now
```
bluetoothctl
```

---

### Post by kate.t on 2016-10-15
Here you are:

```
[NEW] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
[NEW] Device AC:9B:0A:6C:EA:FF MDR-ZX770BT
[NEW] Device 94:23:6E:0D:11:EA Tower Stereo


```

Kathleen

---

### Post by #&amp;thj^% on 2016-10-15
Very Strange...well lets see if it thinks it is paired
```
info AC:9B:0A:6C:EA:FF
```

---

### Post by kate.t on 2016-10-15
It didn't seem to like that command:

```
File: dir,      Node: Top,      This is the top of the INFO tree.

This is the Info main menu (aka directory node).
A few useful Info commands:

  'q' quits;
  '?' lists all Info commands;
  'h' starts the Info tutorial;
  'mTexinfo RET' visits the Texinfo manual, etc.

* Menu:

Basics
* Common options: (coreutils)Common options.
* Coreutils: (coreutils).       Core GNU (file, text, shell) utilities.
* Date input formats: (coreutils)Date input formats.
* Ed: (ed).                     The GNU line editor
* File permissions: (coreutils)File permissions.
                                Access modes.
* Finding files: (find).        Operating on files matching certain criteria.

C++ libraries
-----Info: (dir)Top, 254 lines --Top--------------------------------------------


```

Kathleen

---

### Post by jeremy31 on 2016-10-15
Run the last command from 1fallen after running ```
bluetoothctl
```

---

### Post by #&amp;thj^% on 2016-10-15
Kate I finally gave a quick search on this matter...well I am just amazed just how many users were in the same boat.
See this with no solutions: [http://askubuntu.com/questions/tagged/bluetooth?page=2&sort=newest&pagesize=50](http://askubuntu.com/questions/tagged/bluetooth?page=2&sort=newest&pagesize=50)
This seems like a very high number of users....and nothing reported as being worked on outside of the PPA's for testing the fix.
Dose your device still show up in 'alsamixer' and if it dose, dose it show as muted?
This almost makes me want you ask if they will install Ubuntu 14.04 back on the laptop where you had said it worked flawlessly.
Or you could also install 14.04...just thinking out loud here all we seem to be doing is chasing our tails here.

---

### Post by kate.t on 2016-10-15
jeremy31, thanks for the help!

1fallen, here's what you asked for before:

```
[NEW] Controller 10:08:B1:FB:EE:92 kathleen-Lenovo-G50-70 [default]
[NEW] Device AC:9B:0A:6C:EA:FF MDR-ZX770BT
[NEW] Device 94:23:6E:0D:11:EA Tower Stereo
[bluetooth]# info AC:9B:0A:6C:EA:FF
Device AC:9B:0A:6C:EA:FF
    Name: MDR-ZX770BT
    Alias: MDR-ZX770BT
    Class: 0x240404
    Icon: audio-card
    Paired: yes
    Trusted: yes
    Blocked: no
    Connected: no
    LegacyPairing: no
    UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
    UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: Handsfree                 (0000111e-0000-1000-8000-00805f9b34fb)
[bluetooth]# 


```

I checked ALSAmixer and the headphones were muted, but when I fixed that, it didn't make any difference in the troublesome behavior.

---

### Post by kate.t on 2016-10-15
Hmmm...14.04.

It was my prior laptop that had 14.04 on it. I wouldn't know how to put a different operating system on here, as I don't understand partitioning. I suppose VirtualBox would work, too??? Do you know where to send me to get step-by-step instructions to install 14.04 on this laptop with its own partition? Or do I need to post another thread here?;)


Kathleen

---

### Post by jeremy31 on 2016-10-15
I wonder if the command I use will work for you now
```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 5 ; echo -e "disconnect AC:9B:0A:6C:EA:FF\n quit"|bluetoothctl;sleep 10; echo -e "connect AC:9B:0A:6C:EA:FF\n quit"|bluetoothctl; sleep 10; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
```

Does ```
pactl list short | grep bluetooth
```
show module-bluetooth-policy and module-bluetooth-discover.

---

### Post by kate.t on 2016-10-15
jeremy31,

No, those two items don't show up. This is all that's there:

```
8    module-bluetooth-policy        

```

Do I need to get them loaded before trying your other code?

Kathleen

---

### Post by jeremy31 on 2016-10-15
yes you do.  Let's do it this way
```
pacmd
load-module module-bluetooth-discover
```

See if it gives any errors

---

### Post by kate.t on 2016-10-15
jeremy31,

I stupidly missed the pacmd (sorry), and just did the load-module module-bluetooth-discover.

This is what I have listed now:

```
8    module-bluetooth-policy        
24    module-bluetooth-discover    

```

The great news is that my workaround works again!!!!  Thanks so much!!!! I can use my headphones again. The fact that the workaround is a pain doesn't matter right now in the grand scheme of things.

Kathleen

---

### Post by #&amp;thj^% on 2016-10-15
Good Job jeremy31!
@kate you might want to keep this somewhere just in-case.
Maybe save it to a text file.

---

### Post by kate.t on 2016-10-15
Uh-oh. The workaround just got appreciably longer.

A nagging thought bothered me, so I rebooted the laptop to see if module-bluetooth-discover stayed loaded. It did not. 

So I guess now, before engaging the "classic" workaround, I'll have to reload module-bluetooth-discover each time I boot up.

Unless one of you gentlemen has an idea on how to get that sucker loaded so it stays loaded?!???

Kathleen

---

### Post by jeremy31 on 2016-10-15
The alternative to using pacmd is ```
pactl load-module module-bluetooth-discover
```

I am sure that the latest release of Ubuntu 14.04 uses the 4.4 kernel and that might work well for kate as the original 3.13 kernel used didn't support that bluetooth device out of the box

---

### Post by jeremy31 on 2016-10-15
Use ```
sudo -H gedit /etc/pulse/default.pa
```
scroll to this
```
.ifexists module-bluetooth-discover.so
#load-module module-bluetooth-discover
.endif
```

Remove the # so it becomes
```
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif
```

Save, exit gedit, reboot, cross fingers

---

### Post by kate.t on 2016-10-15
Hooray!!!:D

That worked like a charm, jeremy31! I've never been so glad to see a workaround work!!! Now I can use the headphones for my work again without too much aggravation.

Do you think this might get fixed in future? I filed a bug report way back when and the report is still listed as "new" and "undecided".

1fallen & jeremy31, I sure wish I could buy you gentlemen your favorite beverage!!! Thanks so much for hanging in there.:KS

Kathleen

---

### Post by #&amp;thj^% on 2016-10-15
Well your welcome and kudos to jeremy31
I should have doubled checked our last edit..because we had that loading by way of: /usr/bin/start-pulseaudio-x11
Adding this: # Add the following line:
    /usr/bin/pactl load-module module-bluetooth-discover
But all is well that ends well.
Best of Luck to you Kathleen you have been all ace's here throughout all of this.
Best Regards

---

### Post by jeremy31 on 2016-10-15
> **kate.t said:**
> Hooray!!!:D

That worked like a charm, jeremy31! I've never been so glad to see a workaround work!!! Now I can use the headphones for my work again without too much aggravation.

Do you think this might get fixed in future? I filed a bug report way back when and the report is still listed as "new" and "undecided".

1fallen & jeremy31, I sure wish I could buy you gentlemen your favorite beverage!!! Thanks so much for hanging in there.:KS

Kathleen

Post a link to your bug report and I will list myself as one affected and will encourage others with the same issue to also and that should bring some attention to it

---

### Post by kate.t on 2016-10-15
Here's the link to my bug report way back in August:

[https://bugs.launchpad.net/ubuntu/+source/blueman/+bug/1617847](https://bugs.launchpad.net/ubuntu/+source/blueman/+bug/1617847)

Thanks again, jeremy31!

Kathleen

---

### Post by jeremy31 on 2016-10-16
I added myself to the list and now the status is confirmed.  From the other bug link, Luke says he is going to start working on the profile switching bug

---

### Post by kate.t on 2016-10-16
Thanks, jeremy 31!

Kathleen

---

### Post by jeremy31 on 2016-11-05
See [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324/comments/123](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324/comments/123)

This works much better for me as I don't have to use the long terminal command to switch to A2DP

---

### Post by #&amp;thj^% on 2016-11-05
> **jeremy31 said:**
> See [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324/comments/123](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324/comments/123)

This works much better for me as I don't have to use the long terminal command to switch to A2DP

+1 and on Xenial not prefect but much better.
```
apt-cache policy pulseaudio
pulseaudio:
  Installed: 1:8.0-0ubuntu3.1
  Candidate: 1:8.0-0ubuntu3.1
  Version table:
 *** 1:8.0-0ubuntu3.1 500
        500 http://us.archive.ubuntu.com/ubuntu[COLOR=#ff0000] xenial-proposed/main[/COLOR] amd64 Packages
        100 /var/lib/dpkg/status
     1:8.0-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

me on Sat Nov 05 at 05:29 PM in ~  
>> apt-cache policy pulseaudio-module-x11
pulseaudio-module-x11:
  Installed: 1:8.0-0ubuntu3.1
  Candidate: 1:8.0-0ubuntu3.1
  Version table:
 *** 1:8.0-0ubuntu3.1 500
        500 http://us.archive.ubuntu.com/ubuntu [COLOR=#ff0000]xenial-proposed/main[/COLOR] amd64 Packages
        100 /var/lib/dpkg/status
     1:8.0-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

me on Sat Nov 05 at 05:45 PM in ~  
>> apt-cache policy pulseaudio-utils
pulseaudio-utils:
  Installed: 1:8.0-0ubuntu3.1
  Candidate: 1:8.0-0ubuntu3.1
  Version table:
 *** 1:8.0-0ubuntu3.1 500
        500 http://us.archive.ubuntu.com/ubuntu [COLOR=#ff0000]xenial-proposed/main[/COLOR] amd64 Packages
        100 /var/lib/dpkg/status
     1:8.0-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

me on Sat Nov 05 at 05:45 PM in ~  
>> apt-cache policy pulseaudio-module-bluetooth
pulseaudio-module-bluetooth:
  Installed: 1:8.0-0ubuntu3.1
  Candidate: 1:8.0-0ubuntu3.1
  Version table:
 *** 1:8.0-0ubuntu3.1 500
        500 http://us.archive.ubuntu.com/ubuntu[COLOR=#ff0000] xenial-proposed/main[/COLOR] amd64 Packages
        100 /var/lib/dpkg/status
     1:8.0-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages


```

---

### Post by cannedmanatee on 2017-01-26
I just wanted to add, since it seems to be something of an ongoing issue, that none of the previous fixes worked for me. [This one at the Debian wiki, however, did.](https://wiki.debian.org/BluetoothUser/a2dp) In some cases, at least, it appears the device manager, GDM, grabs the A2DP channel on a headset before Pulse has a chance. By adding the following two lines

```

autospawn = no
[FONT=inherit][/FONT]daemon-binary = /bin/true
```

 to a file called 

```
[I]var/lib/gdm3/.config/pulse/client.conf
``` 
[/I]
one may prevent this behavior. After creating this file and restarting, I was able to use A2DP on my headphones.

---

### Post by Gus_T_Reer on 2017-02-28
I've been following this thread for a while now and I have to say the patience and fortitude of the three main protagonists, jeremy31, 1fallen and kate.t, to resolve this issue has been inspiring and kudos to you all. The guys have not only been stalwart attempting to help kate.t but also all those of us who have the same issue and are monitoring the situation. Thanks fellas.
However, I've been tinkering with Ubuntu since 4.10 Warty and I have yet to have Bluetooth audio working 'out of the box'. In fact, if my memory serves me correctly and it may not, I'll swear it used to be easier, (ie. didn't take as much fiddly faffery), to have Bluetooth working with earlier versions such as Intrepid and Jaunty than it is now. There are a lot more aspects of the distro releases that have improved immeasurably over time but unfortunately Bluetooth audio is not one of them. I realise there are 1. limited resources, 2. there is a need to prioritise to keep up as technology changes apace and 3. that those priorities don't necessarily coincide with mine. However, for me, and this is not a 'fix it or else' rant, I have genuinely had enough of the fiddly faffery with Bluetooth audio in Ubuntu and had a heavy heart when I installed Yakkety only to find the status quo had prevailed.
Having tried a number of suggested solutions to no avail I decided to give it one last go with cannedmanatee's suggestion in post #224 and it worked up to a point. What this seems to do is allow the selection of A2DP to 'stick' to the headset rather than drop out.
I still had to do a little dance regarding removing the headset from Blueman, reboot, re-pair, reboot, select A2DP in Blueman and then separately in Sound Settings to start listening to Rhythmbox through the headset (Motorola S805) but it is working. Using the headset buttons I can pause the music but I can't resume or skip tracks but that's no hardship and I now have A2DP quality streaming. I hope this helps someone.
It would be nice to think that as we reach the end of the alphabet with Zesty that this problem would eventually be resolved. I guess time will tell.

Regards

GTR

---

### Post by jeremy31 on 2017-02-28
Unfortunately kate hasn't visited since her last post and hasn't replied to the [bug report](https://bugs.launchpad.net/ubuntu/+source/blueman/+bug/1617847)
I left some info about a python script there that works reliably for me but you can do the same using Blueman.  Connect to the headset and then switch audio profile to "off", disconnect and reconnect and switch audio profile to A2DP and it seems to work

---

### Post by Gus_T_Reer on 2017-03-01
Jeremy, thank you for that. I'll give the python script a go.
I would also like to raise awareness of a similar Bluetooth bug that was raised on Launchpad for Trusty 14.04 and is still running: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1283003?comments=all](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1283003?comments=all)
I have to say that even when applying the solutions proffered in this bug report I always had to manually assign A2DP to get the headset to work but what I'm finding with cannedmanatee's solution is that when I turn the headset on/off the system automatically connects/disconnects the headset and assigns A2DP without any further intervention from me. This continues to be the case even after a system shutdown so it appears to be be stable.

Regards

GTR

---

### Post by jeremy31 on 2017-03-01
When I still used Ubuntu 14.04 there was a bug in Blueman that removed a module from pulseaudio, module-bluetooth-discover that caused some issues with sound

I think 16.10 will benefit from the python script.  cannedmanatee's solution might just be relevant to 16.10 as my 16.04 install doesn't have a gdm3 folder in /var/lib/

---

### Post by Gus_T_Reer on 2017-03-02
> **jeremy31 said:**
> I think 16.10 will benefit from the python script.  cannedmanatee's solution might just be relevant to 16.10 as my 16.04 install doesn't have a gdm3 folder in /var/lib/

Neither did my 16.10 ;)

I have noticed though and I don't know (yet) if the script will fix it but the headset A2DP sound will intermittently drop out for a few seconds and then return without any action from me. Watching a DVD last night with VLC had this issue as did Spotify. I was using the legacy version of VLC as bizarrely the Snap version wouldn't play the DVD with permissions problems. Ho hum.

Thanks for the feedback though.

Regards

GTR

---

