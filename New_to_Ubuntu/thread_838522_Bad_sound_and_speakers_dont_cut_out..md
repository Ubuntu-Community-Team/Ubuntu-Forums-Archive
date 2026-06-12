---
title: "Bad sound and speakers dont cut out."
date: 2008-06-23
forum: New to Ubuntu
---

### Post by DaleNewton on 2008-06-23
Hi all,

Getting everything set up just right on my laptop running Hardy. Just a couple of annoying things that I havre to go back to windows for though. 

Main thing is playng back any forem of recorded sound, and the headphones not cutting out the speaker sound.

When I use the sound recorder, skype, or anything that I use to record sound using my mic or inbuilt mic, the sound that gets played back is terrible, and also inserting the headphones doesnt cut out the sound to the laptop speakers.  The sound comes to the headphones, but ALSO to the speakers.  

When playing back recorded sounds, it sounds like severe digital distortion. I also fiddled with the settings and found the only way to improve the sound was by lowering the 'digital' knob in recording and turning up 'capture' to compensate.Still sounds terrible though.

I am using alsa (the latest upgrade).  I have selcted alsa for everything in multimedia (not autodetect). For mixer tracks device I have selected 'HDA intel (alsa mixer)' 

PLayback of dvds cds etc is fine. Also, in windows ( I have dual boot) everything works fine (so probably not hardware?)   

THanks everyone,

Dale.

---

### Post by Pjotr123 on 2008-06-23
Probably something that alsamixergui can fix:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)
(number 2 )

---

### Post by angryfirelord on 2008-06-23
If it's recorded sound through the mic port on your sound card, then the record volume is probably too high. Turn it down and see what it does.

---

### Post by DaleNewton on 2008-06-24
Thanks pjotr123 and angryfirelord for those suggestions.

I managed to improve the sound by changing device to Realtek device and changing properties there aswell.  I guess I have more than one sound device on the computer? I have Alsa PCM, HDA intel , adn Realtek HALC883.

Cant get the speakers to cut out when I plug the headphones in yet.

---

