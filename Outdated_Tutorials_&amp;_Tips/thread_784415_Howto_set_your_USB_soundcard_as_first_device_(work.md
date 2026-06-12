---
title: "Howto set your USB soundcard as first device (working with KDE and Flash)"
date: 2008-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by TTL on 2008-05-06
Why?
I did it because my headphone output of my laptop is broken and I prefer to use external speakers instead of the internal ones whenever I'm at home with my laptop. The solution is an USB soundcard.
An USB soundcard costs only about 10-15 Euro.

What's the problem?
As soon as you plug in a usb soundcard the proper kernel module is loaded, but the internal Soundcard is still the first device and is used by all common programs such as KDE or the Flash plugin.

Solution?
Unloading the driver for your internal soundcard works with KDE but not with Flash because the usb soundcard still wont be the first device.
For the unloading of the module for the internal soundcard, I use the following siple script which runs on every startup:

#!/bin/sh

#by TTL 2008-02-10

SNDUSB=`lsmod | grep snd_usb_audio | wc -l`

if [ "$SNDUSB" -gt "0" ]; then
  echo "USB Soundcard detected, removing other card"
  modprobe -r snd_hda_intel
else
  echo "Using internal soundcard"
  modprobe snd_hda_intel
fi

Replace snd_hda_intel by the name for the kernel module of your internal soundcard.
Save it in a file into /etc/init.d/usb_sound_card.sh and give it the executable permission.
Then make a softlink to this file from /etc/init.d/usb_sound_card.sh to /etc/rc2.d/S90usbsound
So whenever your usb soundcard is connected on system startup, the internal driver gets unloaded and if it is not connected it gets loaded.

But now the usb soundcard has still not the first device number (needed for Flash), so we have first to allow the system to make it the first one. In the file /etc/modprobe.d/alsa-base comment-out the line
options snd-usb-audio index=-2
by adding a # before the line
#options snd-usb-audio index=-2
and save the file.

Unfortunately the device (on my system) still did not get the first device id because the driver for the internal card is loaded before the driver for the usb soundcard. So I prevented the internal driver to be loaded until the script above does it explicitly. Open the file /etc/modprobe.d/blacklist and add a line
blacklist snd_hda_intel
(use the module name for your internal soundcard) and save the file.

Note: After a distro upgrade (eg Gutsy -> Hardy) you have to change the configuration files once again.

Please write an answer here if this HOWTO was helpful for you or if something did not work as expected.

---

