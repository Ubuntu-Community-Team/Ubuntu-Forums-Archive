---
title: "Sound problem with Ubuntu Feisty Fawn ."
date: 2008-09-02
forum: New to Ubuntu
---

### Post by wayto_rishi on 2008-09-02
I recently installed Ubuntu on my Lenovo laptop with dual boot. Everything is working fine except sound. System shows the drivers are installed. 
cat proc/asound/card0/codec#* | grep Codec shows this 

Codec: Realtek ALC861-VD
Codec: Motorola Si3054

alsamixer shows the screen with CARD : HDA Intel , Chip:RealTek ALC861-VD

I also checked volume controls  but still no sound .Went to System >Preferenes.>sounds for sound Test but did not hear any sound.
please Help . ... I really need to solve this ..

---

### Post by cwsnyder on 2008-09-03
Which version of Linux kernel did you use for your Feisty Fawn install?  There are several, including one which ends in '-generic'.  The '-generic' kernel was the only kernel which would allow the ALSA sound driver to work on my desktop.  If you are using the '-generic' kernel already, you may have to choose one of the kernels which more closely matches your processor architecture.  Of course the simplest check is whether the volume controls all have their MUTE box unchecked.

---

