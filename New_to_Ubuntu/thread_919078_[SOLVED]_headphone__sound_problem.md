---
title: "[SOLVED] headphone / sound problem"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by neu2buntu on 2008-09-13
hello..my prob is that whenever i plug headphones into laptop the sound from my inbuilt speakers is not cut out. 
 i have tried tweaking the settings in both alsamixer and gnome-sound-manager but to no avail...  i would really appreciate any help/tips..thanx
:-\"

---

### Post by eggdeng on 2008-09-13
Post the output of
```
aplay -l
```
and the make and model of your box.

---

### Post by neu2buntu on 2008-09-13
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


and i am on Advent k4000

---

### Post by eggdeng on 2008-09-13
Problems routing output are common with HDA-Intel cards. Depending on the laptop, the solution can be more or less difficult to find. The fix is usually to open a config file
```
gksudo gedit /etc/modprobe.d/alsa-base
```
and add a line to the bottom of the file. On my LG for example
```
options snd-hda-intel model=lg
```
does the trick. With lesser-known vendors, it's pretty hit & miss. You could try with ```
=auto
``` or ```
=laptop
``` or just google or do a forum search for snd-hda-intel to turn up more options. Remember to save the file and reboot for any changes to take effect.

---

### Post by neu2buntu on 2008-09-13
brilliant stuff thanks.. got it going with model=acer-aspire...i have been baffled with this headphone prob for months now:lolflag: my girlfriend will be happy now that i can use my headphones...cheers

---

### Post by febsn on 2010-06-16
=auto has done the trick for me in Mint 9 on an Asus L50VN, built-in speakers were never switched on before - thanks a lot :-)

---

