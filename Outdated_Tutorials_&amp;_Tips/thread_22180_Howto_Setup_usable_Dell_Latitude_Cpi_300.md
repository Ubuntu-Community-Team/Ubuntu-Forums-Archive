---
title: "Howto: Setup usable Dell Latitude Cpi 300"
date: 2005-03-26
forum: Outdated Tutorials &amp; Tips
---

### Post by mrioseco on 2005-03-26
Hi:
My 2 day googling results: :mrgreen: 

Turn on APM
=============
1. edit /boot/grub/menu.lst (find the following line and append acpi=off noacpi)
# kopt=root=/dev/hda1 ro acpi=off noacpi

2. grub-update

3. edit /etc/modules (append at end)
apm

4. /etc/hotplug/blacklist (append at end)
shpchp
pciehp

Alsa dmix 
=============
1. edit /etc/modprobe.d/modprobe.conf and add

alias char-major-116 snd
alias snd-card-0 snd-cs4236
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
options snd-cs4236 index=0 id=CARD_0 port=0x530 cport=0x210 mpu_port=0x330 fm_port=0x388 irq=5 mpu_irq=9 dma1=1 dma2=-1 isapnp=0v

2. edit /etc/modules and append
snd-cs4236

3. create /etc/asound.conf and add
# our ICE1712 dmix:
pcm.ossmix {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 4096 # buffer size < 6653, but pow(x, 2)
        rate 44100       # we want to play CDs only
    }
    bindings {
        0 0
        1 1
    }
}
# Everything shall be dmixed, so redefine "default":
pcm.!default {
    type plug
    slave.pcm "ossmix"
}
# OSS via aoss should d(mix)stroyed:
pcm.dsp0 {
    type plug
    slave.pcm "ossmix"
}
ctl.mixer0 {
    type hw
    card 0
}

US keyboard layout with deadkeys (international support)
=========================================
1. edit /etc/X11/XF86Config-4 and check your InputDevice section and change or add the required values, using the next template:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xfree86"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us_intl"
        Option          "XkbOptions"    "modeshift:ralt"
EndSection

XMMS Alsa Output Config
=======================
Options->Preferences

    * Select Alsa Plugin
    * Configure
         1. Audio Device: "dmixer" (per example conf above) which is the same as "ossmix"
         2. Use software volume control (i don't want making music louder to raise gAIM sounds!)
         3. mixer device and mixer card are greyed out for me
         4. Advanced Setting (these settings maybe for a particular sound card)
                o buffer time: 750ms
                o period time: 75ms
                o uncheck mmap mode 


GAIM Alsa Output
================
aplay %s

------ o ------

* xmms and gaim config from [http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix)

* other config from google  (i can't remember from where i copied it  :mrgreen: )

---

