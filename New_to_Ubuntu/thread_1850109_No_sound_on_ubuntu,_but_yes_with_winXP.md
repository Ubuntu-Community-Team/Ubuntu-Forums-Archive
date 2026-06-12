---
title: "No sound on ubuntu, but yes with winXP"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by kens60 on 2011-09-25
I have Logitech dual speakers and they work good with winXP, but do not work on 10.04 ubuntu. do I need to find a different driver for making sound here? or is there a player I need to download?

---

### Post by kens60 on 2011-09-25
still no sound at all.

---

### Post by kens60 on 2011-09-25
Guess I'll go back to windows to listen to music.... It plays on windows, but no sounds on ubuntu. I wonder why... CD player no sound either....  Radio no sound... must need a driver of some kind, but don't know what... I thought whatever it could do on windows it could do on linux, but guess not..... C-YA..

---

### Post by Denver Dave on 2011-09-25
Don't mean to insult, but this tripped me up - ubuntu classic defaults to muted on my PC until I change it.  Might click the sound icon on the top right, just in case.

If that doesn't work there is a way to check which sound device is being used - don't remember how

---

### Post by kens60 on 2011-09-25
Thanks Denver (I'm in Grand Junction) yea I checked the many areas where there are mute buttons.. I just played a song on winXP and came back here and updated 10.04 (52 items) and now, still no sound at all....   got ta be a driver I would think, but don't know which one since it works on winXP...

---

### Post by mörgæs on 2011-09-25
Do you get sound in a live boot of 11.04?

---

### Post by kens60 on 2011-09-26
I don't have 11.04.  I have 10.04     11.04 would not work on my old computer.. Computer is a DELL 3000 from 2005

---

### Post by technosysind on 2011-09-26
is your problem solved now ?

---

### Post by mastablasta on 2011-09-26
first type in 
 
```
 
lspci

```
 
in terminal then copy paste the results. the command tell us which sound card is recognised by linux.
 
If the sound card is linux compatible (and not windows only), then you can do this (upgrade the drivers):
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
 
Or you can try to upgrade the drivers by adding the PPA: [https://launchpad.net/~team-iquik/+archive/alsa](https://launchpad.net/~team-iquik/+archive/alsa)
 
Might be more simple for you (instructions are found on the site). 
 
if it's still not working then we need to look at pulse audio option. if it wont' work then then the sound card is windows compatible only. it was made to work only on windows. and in that case it is just best to stay on windows.

---

### Post by mörgæs on 2011-09-26
Try booting a live Lubuntu 11.04 and see (or listen) if you get sound. Might be muted by default, as posted above.

---

### Post by kens60 on 2011-09-26
MASTABLASTA, WHAT TERMINAL...

first type in 
 
 	Code:
 	 
lspci 
in terminal then copy paste the results. the command tell us which sound card is recognised by linux.

---

### Post by kens60 on 2011-09-26
MORG...  how do I do this? <<Try booting a live Lubuntu 11.04>>    I don't have version 11.04, I have 10.04 and I've never heard a sound on ubuntu, so I'm sure thinking it is in the sound card being only for WINDOWS... I might go into BIOS and see if it might be changable. I need it to work both in ubuntu and windows at this time....  might have to get another sound card to do this, we'll see... 

Problem is NOT solved at this time, still working on problem and like to thank those helping me.

---

### Post by kens60 on 2011-09-26
Solved the problem.......

I went into the BIOS and checked SOUND and it was ON, so I turned it to OFF....  Now I'm on only the sound card I installed with Xtreme Sound PCI card...  Amazing

Thanks for all the help..

---

