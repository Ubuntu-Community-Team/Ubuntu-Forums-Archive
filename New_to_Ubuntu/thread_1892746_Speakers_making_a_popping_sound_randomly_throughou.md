---
title: "Speakers making a popping sound randomly throughout usage. (11.10)"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by Langstaff on 2011-12-08
When I boot Ubuntu 11.10, the speakers make a popping sound. And when I run Skype, Banshee, and any other audio-based programs, my speakers pop. The speakers also pop at shut down. Like three times. And IT IS LOUD AND ANNOYING!!!

Sincerely,
Langstaff

P.S.
Please, respond with a reasonable and understandable answer. I just got Ubuntu four days ago.

---

### Post by pierreyy on 2011-12-08
hello and welcome, can you give more info about your system?

it might be a bug with the alsa driver bug#445135

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/445135](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/445135)

if so then the fix for it has been released follow the link above.  hope this helps.

---

### Post by atom94 on 2011-12-08
Did this happen with your previous operating system, running the same hardware, or have you changed something hardware-wise? If so it's likely to be a hardware issue.

Is it the same sort of noise you often get when plugging or unplugging audio cables with the power switched on? In that case, presuming it's not a hardware problem, then it could be that your sound card is being switched on and off every time it plays anything, which is weird as it should usually stay on all the time.

It would help if you could post some more information about your setup. Are you using the built-in speakers in a laptop, stand-alone self-powered desktop speakers, an external amplifier/sound system, etc. Have you tried it with headphones to see if it makes the same noise?

---

### Post by Langstaff on 2011-12-08
It has never happened with my other OS. And I haven't changed anything hardware-wise, other than RAM, but that was before I got Ubuntu.
They are built-in speakers. Also, I have heard of a power-save thingy that may be the problem, but I'm not sure. Again, I just got started you guys, so try to keep it simple please!
And thanks for the quick reply, guys.

---

### Post by atom94 on 2011-12-08
Could you tell us a bit more about this power-save thingy you mention.

---

### Post by Langstaff on 2011-12-08
In other threads, I have heard of similar things happening to other people. (where people mention the term "power_save") Here's a few examples:

[http://ubuntuforums.org/showthread.php?t=1748115](http://ubuntuforums.org/showthread.php?t=1748115)

[http://ubuntuforums.org/showthread.php?t=1314834](http://ubuntuforums.org/showthread.php?t=1314834)

To answer your question... I have no idea what it's about other than what it says in other posts.

---

### Post by atom94 on 2011-12-09
Okay, try running this command:

```
cat /etc/modprobe.d/alsa-base.conf
```

Copy everything it displays and post it here.

---

### Post by Langstaff on 2011-12-09
Holy Cow! Here you are:

marc_langstaff@ubuntu:~$ cat /etc/modprobe.d/alsa-base.conf
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

Ok, I have no idea what that was... but I'm a beginner, so excuse my lametalk. I don't know Linux code yet.

---

### Post by atom94 on 2011-12-10
OK, it doesn't look like you have the power_save option enabled like in the thread you linked, so that can't be the problem. However, some of the threads mentioned other power saving features that can cause a similar problem. In either case, a popping sound usually happens when sound hardware is turned on or off, so power saving features would be the first thing to look at.

Do you know what make or model sound card is installed in your PC?

---

### Post by Langstaff on 2011-12-10
My sound card is Conexant AC-Audio, possibly a CX20468-31. I think so. I haven't booted Vista in a while (I am using a multi-boot) to see what my sound card was, but it sounds like it is the Conexant AC-Audio CX20468-31 AC97. (Altec Lansing)

---

### Post by Langstaff on 2011-12-12
Ok, I'm on Vista now, and it says that it is Conexant AC-Link Audio, but that's all it says. Apparently there is no real information on there that says what specific model number it is.

---

### Post by Langstaff on 2012-01-10
Hello? Is anybody looking at this anymore? This is also happening in Linux Mint 12.

---

### Post by surement on 2012-05-18
I have the exact same problem on a Samsung laptop. I also don't have an Intel sound card or anything mentioning power save in alsa-base.conf.

---

### Post by GeekG on 2012-10-09
Hi everyone.

I'm experiencing the same problem.

---

### Post by GeekG on 2012-10-09
> **GeekG said:**
> Hi everyone.

I'm experiencing the same problem.

 cat /etc/modprobe.d/alsa-base.conf
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

---

### Post by Pletched on 2012-10-09
This problem was in all releases after 10.04 until 12.04 came along.

The volume is quite low in 12.04. In 10.04 I don't have to turn the volume up until it almost reaches the end to get some sound.

---

