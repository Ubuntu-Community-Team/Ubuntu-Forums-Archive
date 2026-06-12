---
title: "Graphics card overriding sound card."
date: 2015-09-08
forum: New to Ubuntu
---

### Post by felix33 on 2015-09-08
Hello

I've just recently gotten myself a new computer and started installing ubuntu 15.04.

Everything works fine except for the sound which works when I unplug the GPU, but doesn't work when I plug it in.

When I run alsamixer without the graphics card it works fine, when the card is plugged-in I get a 'no such file or directory' error.

When listing /proc/asound/cards the output I get differs.


WITHOUT the GPU:

 0 [PCH            ]: HDA-Intel - HDA Intel PCH

                       HDA Intel PCH at 0xdf140000 irq 130

WITH the GPU:

 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdf080000 irq 17


This is what aplay -l gives me when I run with the graphics card.
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



When I run it without the gpu, the "nvidia" is replaced with "Intel"

What annoys me is that it works fine as long as the graphics card isn't plugged in. I have been trying to find an answer for this for quite a while without any success.

The default sound card is enabled in BIOS as well.

Let me know if you need any more information, I don't really know what information that is helpful and what is not.

Thanks in advance

---

### Post by mastablasta on 2015-09-09
have you checked dmesg for any errors?

you can reload alsa modules  and see if that solves it or at least makes it appear in alsamixer.

[http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)

---

### Post by felix33 on 2015-09-09
Hello,

I tried your suggestion however it seems not to do the trick. The sound setting actually registers two sound outputs already (HDMI / DisplayPort 1, HDMI / DisplayPort 2) which are from my two monitors plugged into the graphics card.

The dmesg output looks like this: [http://pastebin.com/QPNk4Utm](http://pastebin.com/QPNk4Utm)  I don't really know what to look for in there...

What is interesting is this: I can see the two options under "Play sound through" which are coming from my graphics card, however, when I run alsamixer I get the following: 
felix@felix:~$ alsamixer
cannot open mixer: No such file or directory

Checking up /proc/asound/ I can see card0 and card1 as well as a symlink called NVidia which points to card1

card1 contains some files, as expected. However, card0 doesn't appear to contain anything at all. Might this be why alsamixer returns such a weird error message? The configuration for the alsamixer is as follows:
felix@felix:/etc/modprobe.d$ cat alsa-base.conf 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2



I greatly appreciate you taking interest in this issue.

Regards,
Felix

---

### Post by mastablasta on 2015-09-10
```
felix@felix:~$ alsamixer
 cannot open mixer: No such file or directory
```

I assume alsamixer is installed? an option would be to track down where it is (search for it) and then run it directly, to see what happens.

I need to check how I do the reload... I have intel chip but it looks like OS get's confused by ATI card or something as sometimes it shows dummy output. reloading the modules helps sometimes. but no always. sometime i need to take away the power (unplug from socket) for it to register the chip.

---

### Post by felix33 on 2015-09-10
Hmm, I did try to start the application given the full path before without success, however, this time it worked.

The alsamixer tells me that I do only have one card, which is the NVidia one. I wonder if my motherboard (an uefi asus Z170-A) doesn't care to load it now that it sees the NVidia card available.

I tested reloading the sound, but it still doesn't do anything (pulseaudio -k && sudo alsa force-reload).

I'm going to look a little bit more into the drivers and see if that might be it.

---

### Post by QDR06VV9 on 2015-09-10
See if this helps further.
[Ubuntu Default Sound Card Select]("http://ubuntu4me.blogspot.ca/")

---

### Post by Yellow Pasque on 2015-09-11
> snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)

[http://ubuntuforums.org/showthread.php?t=2293912](http://ubuntuforums.org/showthread.php?t=2293912)

---

### Post by felix33 on 2015-09-14
> **runrickus said:**
> See if this helps further.
[Ubuntu Default Sound Card Select]("http://ubuntu4me.blogspot.ca/")

Updating the drivers did the trick! Thank you a ton, it works like a charm!

---

