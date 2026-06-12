---
title: "No audio hardware device found?"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by dyallo on 2011-10-20
Hey guys. I installed Xubuntu about two days ago, everything was working fine (I thought) until I wanted to play some sound - there was none. So I checked out Sound settings, and there it seems that Linux didn't even see I had an audio device. Which is weird.. I have an integrated sound chip on my ASRock P55 Extreme (Realtek) and it worked when running Ubuntu 11.10 last week. 
I'm not sure if it worked from the start of the Xubuntu installation, because right after I installed Gnome and I think I even installed the prop Linux drivers from Realtek's site.

Any way to Revert then to ALSA? I tried apt-get install --reinstall alsa, it did appear to reinstall, but still no audio device found by Xubuntu.

What can I do? I'm pretty sure that it will work if I reinstall Xubuntu, but I don't feel like it since I've configured a bunch of apps already..

(On Xubuntu 11.10 btw)

---

### Post by mastablasta on 2011-10-20
you would also need to remove the realtek drivers.

---

### Post by dyallo on 2011-10-20
As this is a Absolute Beginner Forum - I could use some help achieving that :P

---

### Post by dyallo on 2011-10-20
> **dyallo said:**
> As this is a Absolute Beginner Forum - I could use some help achieving that :P

bump

---

### Post by dyallo on 2011-10-21
please, if anyone show me how to remove the realtek, and reinstall the default audio driver that comes with x/ubunutu, that'd be great

---

### Post by Carborundum on 2011-10-21
I have never used proprietary drivers in Ubuntu, but I would guess you should be able to remove them in the program Additional Drivers? (Main Menu > Settings > Additional Drivers)

If not, just reinstall. I know from experience that reinstalling is usually faster than trying to repair whatever you've screwed up. Yields better results too.

---

