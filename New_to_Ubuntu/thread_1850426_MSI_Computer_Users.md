---
title: "MSI Computer Users"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by ShawnxBuntu on 2011-09-26
Ive had my Problems but i finally solved my Subwoofer Issue..

           **For People that Use MSI Laptops / Desktops:**

         Its Pretty Simple Im kinda embarrssed that I was asking for help when it was right in front of me this whole time... anyways..

            Go into Terminal **A**ccessories -> **T**erminal Type in the Following Commands:

                   ***sudo gedit /etc/modprobe.d/alsa-base.conf:***
                         Dont ever change the root password for any reason
                                   If it requeries root just do **sudo -i** then type your password in
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
options snd-hda-intel model=targa-2ch-dig
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

    **You wil NOT** have "options sna-hda-intel model=" in your alsa-base.conf file when starting off because ubuntu thinks that its already configured your system.. So what you need to do now is.. add that line into your alsa base.conf.. 

           [B]Here are some other models of msi..
                                   You can do: options snd-hda-intel model=targa-dig
                                                         options snd-hda-intel model=targa.8ch-dig
                                                         options snd-hda-intel model=targa.2ch-dig

Im running the MSI GT660 what worked for me was the Targa.2ch.dig, Then i downloaded HDA Analyzer, 

              Open Terminal Once again.. Type the Follwing:
                         [/B]wget -O run.py [http://www.alsa-project.org/hda-analyzer.py](http://www.alsa-project.org/hda-analyzer.py)
                                           python run.py
  **Ok now another window should pop up.. that is HDA Analyzer... Now **

                       Im not sure if its different on other systems you go to [B]Node [0x0c] AUD_MIX
           Should be Options Val[0] and [1] Now if u mute those u will here the Bass as it should be working.. if u unmute those 2 u will hear your Main Speakers.. Now if u want to turn up the bass Go to Nod[0x16] PIN If  they are muted.. Un mute them and turn the Val[0] and [1] Up all the way.

 Not sure if i left out anything but if u need help with anything just PM me or Reply Thank u
[/B]

---

