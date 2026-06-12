---
title: "Asus M70 sound used to work. Not anymore. 8.10"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by sudo_chop on 2008-11-06
I booted up my laptop today and the sound just doesn't work. I has always worked under 8.10. I cant figure it out, everything looks like it always has when I open volume control, like the same device as always with the same switches as always. Can someone help me troubleshoot this please?

- sudo chop

---

### Post by sudo_chop on 2008-11-07
^
 
Still not working. Just need some help troubleshooting, I don't know what to do.

---

### Post by CoCoKnots on 2008-11-07
Sudo_Chop
I had the same problem this week-end with the upgrade from 7.10 to 8.04. Try System> Preferences> Sound & re-configure the setting & hit the 'Test' buttons for a response. That worked for me.

---

### Post by sudo_chop on 2008-11-07
Thanks CoCo, I did try those test buttons, but they didnt make any sound...
 
Ubuntu didnt even recognize my sound card in 8.04 and only started working in the first 8.10 Alpha I tried, which was 6. I think it is a pretty new driver for the linux kernel, thats probably why I am having problems. I think something is just wrong with this ALSA driver.
 
Whats weird here is I didnt make any changes. No new updates were downloaded or installed, nothing. I wasnt even connected to the internet. One reboot later and it just doesnt make sound.
 
Maybe I could try reinstalling the driver? Or reconfiguring it? Anybody know how to do that?

---

### Post by sudo_chop on 2008-11-08
bump again

---

### Post by Sef on 2008-11-08
I would get a live cd and see if you can get sound on that.   Use 8.10 and something else other than 8.10 for the check.  It is possible that your sound card is bad.

---

### Post by sudo_chop on 2008-11-08
> **Sef said:**
> I would get a live cd and see if you can get sound on that. Use 8.10 and something else other than 8.10 for the check. It is possible that your sound card is bad.
 
Works fine in Windows... (I dual boot)
I probably should have said that in the first post.

---

### Post by drgor on 2008-11-09
hi I have the same problem, my sound suddenly stopped working, i m using 8.10, probably after an update

results after aplay -l

"card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0"

I dual boot with XP, sound is working in XP, programs do not complain about abscent sound they just keep going, like i am deaf

I tried booting with older kernel but it doesnt solve problem,

is it normal to have 1/1 subdevices??, why I m hving 2 duplicate like card 0 entries??

it would be of great help if anybody can solve the problem

---

