---
title: "Sound Not coming from speakers only sub.."
date: 2011-09-25
forum: New to Ubuntu
---

### Post by ShawnxBuntu on 2011-09-25
Kinda have a Prob.. The Sound isnt coming from my Main Speakers.. only coming from the Base (Subwoofer).. It should come from the main speakers and have the base in it also.. but thats not what its doing... anyways here is some Information from Alsa-Base.conf... tell me if u see anything wrong..

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
# Keep snd-usb-audio from being loaded as first soundcard
options snd-usb-audio index=-2

**  This is what i get for **
              *aplay -l*:
           **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ALC888 Digital [ALC888 Digital]

 **This is what i get when i do:**
            * l spci | grep Audio:*
       00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
       
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 **This is what i get when i use**:
            *cat /proc/asound/cards*:

           0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xecc00000 irq 55

  If anyone sees anything ***Wrong** Please inform  me and tell me how to fix it im new to this whole thing but learning command... please Help. Thank you*

---

### Post by ShawnxBuntu on 2011-09-25
Here is a Script Test 

 [http://www.alsa-project.org/db/?f=c2aaa6933fed4925b53027a963e80944817c7d10](http://www.alsa-project.org/db/?f=c2aaa6933fed4925b53027a963e80944817c7d10)


  Theres all my audio info

---

