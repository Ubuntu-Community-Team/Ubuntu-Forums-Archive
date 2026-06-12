---
title: "Sound on Firefox not switching to headphones"
date: 2020-11-22
forum: New to Ubuntu
---

### Post by joubqa on 2020-11-22
Ubuntu 20.04. PS4 wireless bluetooth headphones. I have the headphones selected in Sound settings and audio from local videos plays through them but the audio from Firefox plays through the speakers. What should I try?

---

### Post by mastablasta on 2020-11-22
you need to set it in the sound mixer so that Firefox application uses headphones as first choice and if heaphones are not in it will use the speakers.

---

### Post by joubqa on 2020-11-22
Thanks. Where is this Sound Mixer? I can't find it in Ubuntu or Firefox.
This is all I have in Settings/Sound:
[IMG]https://i.ibb.co/xLxM8c8/sound.png[/IMG]

---

### Post by ajgreeny on 2020-11-22
Make sure you have ***pulseaudio-volume-control*** package installed with ```
sudo apt install pavucontrol
```
I thought it was installed by default but perhaps it is not in Ubuntu.

---

### Post by joubqa on 2020-11-22
Thanks. I can chance firefox to use the heaphones from Pulse but it doesn't automatically switch audio when I turn on/off the headphones, Also audio on Youtube is lagging but that might be a separate issue

---

### Post by mastablasta on 2020-11-24
mine also stays on speakers, but my kids sound does go off on speakers while he plugs in the headphones. maybe a sound driver thing?

the only thing that does switch properly in my case it is the mic (it switches from logitech HD cam to headphones mic). maybe i just set it wrong. whatever, i just turn off the speakers by hand. :-)

---

### Post by joubqa on 2020-11-26
I've just been using Pulse to choose the correct audio output. It's fine

---

