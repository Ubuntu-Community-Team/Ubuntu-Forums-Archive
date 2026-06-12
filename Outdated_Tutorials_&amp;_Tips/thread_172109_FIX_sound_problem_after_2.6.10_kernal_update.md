---
title: "FIX sound problem after 2.6.10 kernal update"
date: 2006-05-08
forum: Outdated Tutorials &amp; Tips
---

### Post by megahertza on 2006-05-08
I know some pll have had sound issues after the recent kernal update and they varied from no sound to to damaged sound.

For what every reason, the sound settings where changed during the update. To get acces to the sound settings.

Double click the sound ICON 

I have to bar sound settings (master) and (PCM) and my sound was damaged. My problem was that PCM was at max, so i brought it down to half and that fixed my problem.

As no sound, check that the bars are not at zero. Goto edit -> Preferences and tick "DAC" make sure that it is not at zero. If you don't have DAC, don't worry

---

### Post by Rizado on 2006-05-09
I've been using linux for about 4 years and I have always had bad sound when PCM is at max. I've had two different motherboards with different chipsets but always the same audio driver (snd-intel8x0). When pcm is at 84% there's no problem at all. Does anyone have the same experience?

---

