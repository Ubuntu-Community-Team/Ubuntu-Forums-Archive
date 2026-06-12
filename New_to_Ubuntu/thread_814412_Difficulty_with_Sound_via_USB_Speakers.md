---
title: "Difficulty with Sound via USB Speakers"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by tea for one on 2008-05-31
Good evening

I am using Ubuntu 7.04 with every conceivable codec/restricted extra installed.

When I play a CD via Sound Juicer, the sound is perfect from my external C Media USB speakers.

When I play a DVD or a CD via Totem Movie Player or via Linux VLC Media Player, the sound only transmits through the internal speakers of my laptop (Packard Bell Easynote purchased in September 2006).

I suspect that there is a setting or control switch that I have to apply, but so far, after reading a zillion threads in the Ubuntu fora, I have not found the answer. 

As I dual boot with Windows XP, I thought I would try various players within Windows. I regret to report that DVD and CD sound via VLC, Realplayer and Coolplayer all transmitted through the external speakers within XP.

Any suggestions to consistently activate external USB speakers with Ubuntu 7.04.

---

### Post by Xiong Chiamiov on 2008-06-03
It might have to do with the default soundcard.
Run
```

asoundconf list

```
with the speakers plugged in, then
```

asoundconf set-default-card [name of card]

```

---

### Post by tea for one on 2008-06-03
Thanks for your reply, unfortunately your suggestion was unsuccessful. I am still unable to hear sound via external USB speakers when playing a DVD. I only have "tinny" sound from internal laptop speakers.

However, I still have perfect sound vis USB speakers when playing a CD in Sound Juicer.

I did examine the VLC forums to try and find an answer but that was also a fruitless endeavour.

---

### Post by garpt on 2008-12-25
Hi all,
 i'd like to bump this thread back up even though it's not mine, I have the exact same problem and have tried for a week to solve it. I get power to the USB speakers, but no sound, (internal only.) Have tried the settings in Alsa to output to USB speakers, no luck. 

Thanks. Gary

---

