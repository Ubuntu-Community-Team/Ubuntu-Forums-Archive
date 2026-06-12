---
title: "Sound Problem in Ubuntu 9.10"
date: 2010-04-04
forum: Philippine Team
---

### Post by dmzamora on 2010-04-04
Hi everyone!  I hope to get help here.

I installed Ubuntu 9.10 about a month ago on my laptop (dell vostro 1014).

The sound is working properly when I use it, I plugged in my headset, it works too... the problem is, sabay ang sound sa headset at ng laptop speaker. ](*,)

I hope someone has encountered (and solved) this issue. Thanks!

---

### Post by loell on 2010-04-04
whats your sound device?

```
lspci -v|grep Audio
```

---

### Post by dmzamora on 2010-04-04
Here it is:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

---

### Post by loell on 2010-04-04
this  is somehow common to some intel based sound devices.

try this though,

edit alsa-base.conf

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

at the bottom, add this,

```
options snd-hda-intel model=dell
```

save then reboot, see if can auto switch (speaker/headset).

---

### Post by dmzamora on 2010-04-05
Thanks mr. loell. I'll try it later though.  Have to earn my keep usa.

Maayong buntag gikan sa mid east.:p

---

### Post by dmzamora on 2010-04-05
Maayong gabii!

I did as instructed... mao man gihapon. :(

Ganito po ba dapat ang hitsura:

```
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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=dell
```

Thanks so much!

---

### Post by loell on 2010-04-05
oo, ingon ana lang, kung mao lang gihapon, basig lahi ang ibutang nga model, tanawon nato ang uban.

---

### Post by suxenexus on 2010-04-05
Sana gumana tong fix na to sakin...  Di gumagana 5.1 ko eh :(

---

### Post by dmzamora on 2010-04-05
Katong nag wubi install pa ko nagresearch ko, kay the same ang problem-- gawas ang tingog sa headset ug laptop speaker.

mao ni akong nakita:

[http://ubuntuforums.org/showthread.php?t=1324555](http://ubuntuforums.org/showthread.php?t=1324555)

and akong amigo diha sa davao gladly explained to me na ani daw akong buhaton:  

```
1. add ppa:zsitvaij/ppa-zsitvaij to your software sources --->  type sa terminal...sudo add-apt-repository ppa:zsitvaij/ppa-zsitvaij
2. install linux-backports-modules-alsa-karmic-generic ---->  type sa terminal ...sudo apt-get install linux-backports-modules-alsa-karmic-generic
3. reboot
```

PERO:  nagbinuang na nuon akong flash (sa firefox), di na ko katan-aw ug pinoy channel. mao to, balik ko windows! lol!

di na nuon ko gusto mutry ana, lest magbinuang napud. hehehe.

salamat kaau!

---

### Post by dmzamora on 2010-04-06
@ suxenexus:  pasensya po, nagbisaya ako.  check niyo yang link baka magwork sa iyo. same ang problem na yan sa akin eh.  It did not work for me.

---

### Post by suxenexus on 2010-04-06
> **dmzamora said:**
> @ suxenexus:  pasensya po, nagbisaya ako.  check niyo yang link baka magwork sa iyo. same ang problem na yan sa akin eh.  It did not work for me.

Yung iba kasing mga work around di rin gumana sakin T_T

Pero try kong magreboot ngayon to see what happens

---

### Post by loell on 2010-04-06
@dmzamora try this one

```
options snd-hda-intel index=0 model=toshiba position_fix=1
```

---

### Post by dmzamora on 2010-04-06
ganun pa rin @loell. :-<

---

### Post by stormsurge on 2010-04-06
Try mo iturn-off yung software etc. etc. sa hardware mo. I had that same problem before. After I turned it off ay ok na.

---

### Post by dmzamora on 2010-04-07
Hi @stormsurge!  What do you mean turn on/off?  I tried using the sound option, pwede ko manipulate yung mga softwares (with sounds) running, the same thing eh...

Pasensya po... newbie here...

---

### Post by dmzamora on 2010-04-08
bump. :)

---

