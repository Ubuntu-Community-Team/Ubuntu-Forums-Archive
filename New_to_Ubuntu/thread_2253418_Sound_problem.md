---
title: "Sound problem"
date: 2014-11-19
forum: New to Ubuntu
---

### Post by vladan2 on 2014-11-19
Hello,I installed lubuntu 14.10
my MB: asus k8u-x
ram:1.5gb ddr1
graph:nvidia gf 5200 fx 128mb 64 bit agp ddr1
I have problem : sound doesn't work. When i start audacios or vlc i have this errors :

ALSA error: No suitable mixer element found.

ALSA error: snd_mixer_attach failed: No such file or directory.

so how i think there isn't driver for sound. How to fix it ? Thank you.

---

### Post by ajgreeny on 2014-11-19
Show us the output of ```
lspci | grep Audio
``` which will show the audio hardware you have.

It may also be worth checking that you have pulseaudio installed, as I found it was needed in Lubuntu 12.04 to get sound working properly.

---

### Post by vladan2 on 2014-11-20
00:04.0 Multimedia audio controller: ULi Electronics Inc. M5455 PCI AC-Link Controller Audio Device (rev 20)

---

### Post by vladan2 on 2014-11-20
I download pulse audio so i fix sound :)

---

### Post by ajgreeny on 2014-11-20
Great!
Can you mark the thread as solved from the **Thread Tools** at the top of the thread, please.

---

