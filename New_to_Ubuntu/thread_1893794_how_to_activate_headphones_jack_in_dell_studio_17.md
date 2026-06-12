---
title: "how to activate headphones jack in dell studio 17"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by bala.thunder on 2011-12-11
:( i  have installed ubuntu 11.10 in my dell studio 17.. sound is coming from the spreakers ( JBL with a sub woofer) but sound is not comin from the head phones jack( 2 jacks).. can any one help me to do this..

---

### Post by gennatolls on 2011-12-11
Open up a terminal and type: alsamixer

You can configure it from there or install Gnome Alsa Mixer from the Software Center. I'm assuming your using alsa instead of pulse audio for your sound driver.

---

### Post by 3rdalbum on 2011-12-11
> **gennatolls said:**
> Open up a terminal and type: alsamixer

You can configure it from there or install Gnome Alsa Mixer from the Software Center. I'm assuming your using alsa instead of pulse audio for your sound driver.

Why make that assumption? There's pretty much no reason to remove Pulseaudio, especially not for something as trivial as changing your sound output.

You just need to go to the little speaker icon on your top panel and go to Sound Settings. In the Output tab, change the "Connector" to your headphone jack.

---

### Post by gennatolls on 2011-12-11
> **3rdalbum said:**
> Why make that assumption? There's pretty much no reason to remove Pulseaudio, especially not for something as trivial as changing your sound output.

You just need to go to the little speaker icon on your top panel and go to Sound Settings. In the Output tab, change the "Connector" to your headphone jack.

I thought alsamixer was just a way to configure your sound options?
I didn't think using alsamixer removed pulse audio.
I forgot about the Sound Settings way, better advice.

---

