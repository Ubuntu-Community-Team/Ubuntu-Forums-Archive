---
title: "No Sound 12.04 w/ Soundblaster 2 Audigy"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by gooniegoon on 2013-01-01
Hey everyone,

I am completely new to Ubuntu .  I'm having issues with  getting the computer to play sound. I've checked earlier  threads and tried to fix the problem.

The problem:  I have an ancient machine that I was going to throw away, but instead I spent $10 and ram and decided to try Linux.  Prior to installing 12.04, I was able to get sound on my Dimension 8250 running XP.  Once I installed Ubuntu  I am unable to  get sound through my Logitech Z 680 speakers.   

System Details:
Computer: Dimension 8250
Operating System: Ubuntu 12.04
Sound Card: Sound blaster audigy 2 

Tried to follow earlier suggestions about alsa mixer, I just ran 
wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && bash alsa-info.sh --upload
 in the terminal and received the following... Any suggestions? 

!!################################ !!ALSA Information Script v 0.4.61 !!################################  !!Script ran on: Wed Jan  2 01:39:27 UTC 2013   !!Linux Distribution !!------------------  Ubuntu 12.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.1 LTS)"   !!DMI Information !!---------------  Manufacturer:      Dell Computer Corporation Product Name:      Dimension 8250                Product Version:    Firmware Version:  A04   !!Kernel Information !!------------------  Kernel release:    3.2.0-35-generic Operating System:  GNU/Linux Architecture:      i686 Processor:         i686 SMP Enabled:       Yes   !!ALSA Version !!------------  Driver version:     1.0.24 Library version:    1.0.25 Utilities version:  1.0.25   !!Loaded ALSA modules !!-------------------    !!Sound Servers on this system !!----------------------------  Pulseaudio:       Installed - Yes (/usr/bin/pulseaudio)       Running - Yes  ESound Daemon:       Installed - Yes (/usr/bin/esd)       Running - No   !!Soundcards recognised by ALSA !!-----------------------------  --- no soundcards ---   !!PCI Soundcards installed in the system !!--------------------------------------  02:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)   !!Advanced information - PCI Vendor/Device/Subsystem ID's !!-------------------------------------------------------  02:09.0 0401: 1102:0004 (rev 04)     Subsystem: 1102:1003   !!Modprobe options (Sound related) !!--------------------------------  snd-atiixp-modem: index=-2 snd-intel8x0m: index=-2 snd-via82xx-modem: index=-2 snd-usb-audio: index=-2 snd-usb-caiaq: index=-2 snd-usb-ua101: index=-2 snd-usb-us122l: index=-2 snd-usb-usx2y: index=-2 snd-cmipci: mpu_port=0x330 fm_port=0x388 snd-pcsp: index=-2 snd-usb-audio: index=-2   !!Loaded sound module options !!---------------------------   !!ALSA Device nodes !!-----------------  crw-rw---T  1 root audio 116,  1 Jan  1 19:07 /dev/snd/seq crw-rw---T  1 root audio 116, 33 Jan  1 19:07 /dev/snd/timer   !!Aplay/Arecord output !!--------------------  APLAY  aplay: device_list:252: no soundcards found...  ARECORD  arecord: device_list:252: no soundcards found...  !!Amixer output !!-------------   !!Alsactl output !!--------------  --startcollapse-- --endcollapse--   !!All Loaded Modules !!------------------  Module vesafb snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm dcdbas snd_page_alloc snd_util_mem snd_hwdep snd_seq_midi snd_rawmidi nouveau snd_seq_midi_event snd_seq snd_timer ttm snd_seq_device psmouse drm_kms_helper drm serio_raw snd bnep rfcomm soundcore i2c_algo_bit parport_pc mxm_wmi bluetooth ppdev wmi video binfmt_misc mac_hid intel_rng shpchp lp parport usbhid hid floppy firewire_ohci firewire_core crc_itu_t e100   !!ALSA/HDA dmesg !!--------------

---

### Post by gooniegoon on 2013-01-01
Alsa reply:
[http://www.alsa-project.org/db/?f=6002c88977527db38b0b2ec569acf4e369de1c80](http://www.alsa-project.org/db/?f=6002c88977527db38b0b2ec569acf4e369de1c80)

---

