---
title: "No sound"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by tL0z on 2008-09-16
Hello,

I have no sound in Ubuntu and I have no idea how to fix it. I have a Creative Soundblast sound card.

Thanks

---

### Post by Freiberg on 2008-09-16
Could you be a little more specific?  What you have tried already, whether you have made sure that Ubuntu supports the sound card, etc.

---

### Post by niglet101 on 2008-09-16
try this

[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by tuxxy on 2008-09-16
Do you hear the test sound files play, when you select ALSA as the sound output at **system > prefs > sound**

---

### Post by tL0z on 2008-09-16
It worked fine in 7.04, that's why I don't understand why it doesn't work now. I didn't try anything, except trying [this]("http://ubuntuforums.org/showthread.php?t=759147") utility which also didn't solve the problem.

> **tuxxy said:**
> Do you hear the test sound files play, when you select ALSA as the sound output at **system > prefs > sound**
Nop

---

### Post by tuxxy on 2008-09-16
Maybe you soundcard isnt selected, if you have a soundblaster icon/menu make sure its selected rather than your using onboard

---

### Post by Squid Tamer on 2008-09-16
This sounds really, *really* stupid, but make sure that your speakers are plugged in/in the correct port/turned on.

It's happened to me and others before, and it's easy to miss. I doubt 
 that is the problem though.

(If you have a laptop this is useless, of course.)
(Don't take this as an insult to your intelligence please :) )

---

### Post by halitech on 2008-09-16
open a terminal and post back the output of```
aplay -l
```

---

### Post by jan de beuker on 2008-09-16
check your volume control

---

### Post by tL0z on 2008-09-17
> **halitech said:**
> open a terminal and post back the output of```
aplay -l
```

> **** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: Audigy [Audigy 1 [Unknown]], dispositivo 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdispositivos: 32/32
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
  Subdispositivo #2: subdevice #2
  Subdispositivo #3: subdevice #3
  Subdispositivo #4: subdevice #4
  Subdispositivo #5: subdevice #5
  Subdispositivo #6: subdevice #6
  Subdispositivo #7: subdevice #7
  Subdispositivo #8: subdevice #8
  Subdispositivo #9: subdevice #9
  Subdispositivo #10: subdevice #10
  Subdispositivo #11: subdevice #11
  Subdispositivo #12: subdevice #12
  Subdispositivo #13: subdevice #13
  Subdispositivo #14: subdevice #14
  Subdispositivo #15: subdevice #15
  Subdispositivo #16: subdevice #16
  Subdispositivo #17: subdevice #17
  Subdispositivo #18: subdevice #18
  Subdispositivo #19: subdevice #19
  Subdispositivo #20: subdevice #20
  Subdispositivo #21: subdevice #21
  Subdispositivo #22: subdevice #22
  Subdispositivo #23: subdevice #23
  Subdispositivo #24: subdevice #24
  Subdispositivo #25: subdevice #25
  Subdispositivo #26: subdevice #26
  Subdispositivo #27: subdevice #27
  Subdispositivo #28: subdevice #28
  Subdispositivo #29: subdevice #29
  Subdispositivo #30: subdevice #30
  Subdispositivo #31: subdevice #31
placa 0: Audigy [Audigy 1 [Unknown]], dispositivo 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdispositivos: 8/8
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
  Subdispositivo #2: subdevice #2
  Subdispositivo #3: subdevice #3
  Subdispositivo #4: subdevice #4
  Subdispositivo #5: subdevice #5
  Subdispositivo #6: subdevice #6
  Subdispositivo #7: subdevice #7
placa 0: Audigy [Audigy 1 [Unknown]], dispositivo 3: emu10k1 [Multichannel Playback]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

By the way, I have tried the "first step" of [http://ubuntuforums.org/showthread.php?t=843012lthis]() guide and it still doesn't work.

---

