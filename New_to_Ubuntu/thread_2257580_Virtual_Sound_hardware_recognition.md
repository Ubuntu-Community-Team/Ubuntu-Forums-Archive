---
title: "Virtual Sound hardware recognition"
date: 2014-12-20
forum: New to Ubuntu
---

### Post by Ella_Gebow on 2014-12-20
My little laptop has a broken plug for headphone/speaker so I'd been using a usb devise called Virtual7.1ChSound.  Before I installed Ubuntu it worked and now it does not.  The green light comes on but the music continues to play through the laptop computer instead.  Ubuntu had not automatically looked for the drivers so I need to know how to manual do this.  Thanks

---

### Post by sandyd on 2014-12-20
Hi, can you open a terminal (Unity Dash -> Terminal), and post the output of the following command?

```
lsusb
```
This command allows us to see whether or not linux detects the device, and what it detects it as.

Thanks!

---

### Post by Ella_Gebow on 2014-12-21
I don't know how to cut and paste this information to the post.  Is there something I can download to help me do that?  I have a snap tool on my windows computers.  Here is the main info on each line.
There is DRAM Controller,VGA compatible express Graphics Controller and Display controller Express Graphics Controller, Audio Controller High Definition Audio Controller, PCI Bridge PCI Express Port 1, 2 and 4, USB Controller USB UHCI #1, #2, #3, #4, USB controller US B2 EHCI Controller, PCI bridge, ISA bridge, IDE Interface, SNBus, Ethernet controller Wireless Network Adapter, Etherne controller Qualcom Ahteros

---

### Post by sandyd on 2014-12-21
> **Ella_Gebow said:**
> I don't know how to cut and paste this information to the post.  Is there something I can download to help me do that?  I have a snap tool on my windows computers.  Here is the main info on each line.
There is DRAM Controller,VGA compatible express Graphics Controller and Display controller Express Graphics Controller, Audio Controller High Definition Audio Controller, PCI Bridge PCI Express Port 1, 2 and 4, USB Controller USB UHCI #1, #2, #3, #4, USB controller US B2 EHCI Controller, PCI bridge, ISA bridge, IDE Interface, SNBus, Ethernet controller Wireless Network Adapter, Etherne controller Qualcom Ahteros
Ack, made a typo, run the command that I fixed above.

You can just highlight the text with the cursor, right click and select copy on Ubuntu.

---

### Post by Ella_Gebow on 2014-12-21
right click does not give me a copy, in ubuntu so here is what it says
Bus 001 Device 001: ID 1d6b:0002 Linux Foundaiton 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundaiton 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundaiton 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundaiton 1.1 root hub
Bus 002 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adaptor 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundaiton 1.1 root hub

*note:  The usb device has buttons to change volume up or down and mute sound.  These work but for some reason the computer will not let the sound go through to the headphone or speaker through there.  I tried to find a setting within ubuntu but could not find one that changed this.  Thanks

---

### Post by sandyd on 2014-12-21
> **Ella_Gebow said:**
> right click does not give me a copy, in ubuntu so here is what it says
Bus 001 Device 001: ID 1d6b:0002 Linux Foundaiton 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundaiton 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundaiton 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundaiton 1.1 root hub
Bus 002 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adaptor 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundaiton 1.1 root hub

*note:  The usb device has buttons to change volume up or down and mute sound.  These work but for some reason the computer will not let the sound go through to the headphone or speaker through there.  I tried to find a setting within ubuntu but could not find one that changed this.  Thanks

Few things to try -

1. First, check if the device is recognized by running the following command. This command displays all the possible output devices on your system.
```

aplay -l
```

It should show output similar to ```

**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: E07K [FiiO USB DAC E07K], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Your device should be somewhere in the list. If it isn't, check out instructions at [http://karuppuswamy.com/wordpress/2010/10/04/how-to-get-usb-sound-adapter-0d8c000c-working-as-primary-sound-card-in-debian-linux/](http://karuppuswamy.com/wordpress/2010/10/04/how-to-get-usb-sound-adapter-0d8c000c-working-as-primary-sound-card-in-debian-linux/)

2. If its recognized (before or after using the tutorial), open the Software Center in Ubuntu, and search for 'Pulse Audio Volume Control'. Install the first entry in the list (there should only be one).

3. You should now have 'Pulse Audio Volume Control' in your menu. Open it, and go to the 'Output Devices' tab. There, you can configure your sound card. You can also disable the onboard soundcard in the 'Configuration' tab.

Please post back if you need help.

Regards,

---

### Post by Ella_Gebow on 2015-01-04
I'm sorry, i was away for the Holiday.  Result is as follows;
card 0: Intel (HDA Intel), device 0: ALC269 Analog (ALC269 Analog)
  Subdevices:  1/1
  Subdevice #0: subdevice #0
card 1: Set (C-Media USB Headphone Set), device 0: USB Audio (USB Audio)
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

