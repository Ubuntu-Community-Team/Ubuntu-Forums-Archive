---
title: "Problem with on-board sound. (GA-EP35-DS3)"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Silent-Rat on 2008-05-05
_Greets to all!_ (first_post)

Have finally spent some money on a new system, and decided it was time to learn Linux.
 Got Hardy Installed ok, and working well.
Just when i play sound, i get noise. What i mean is, the mp3/game music plays fine, i can hear it, but when i turn down all volume, ie mute. i still get a audible white-noise through speakers and head-phones. So my sound is not totally clear.

Am using on-board-sound from a brand new Gigabyte GA-EP35-DS3. 

Do i need extra Drivers so similar?
Is the board supported?

Would appreciate any advice or ideas.

thanx

---

### Post by shadowtroopers on 2008-05-05
i not really sure whether this will work or not, if the sound driver that you r using now is alsa, try to switch it to OSS. I've got the same problem before, when i switch to OSS seems to be worked well now. You can do that by:
System> preferences> sounds

than when you change this, on desktop under volume icon, right click and select preference. Use the same configuration (switch to OSS). Hope this will help.

---

### Post by Silent-Rat on 2008-05-05
Yeah, good idea. 
I gave it a try. no change. 

After a bit of pluging around with leads, ....
Problem solved.
i realize the white noise is actually some kind of interference. I have a Samsung TFT with built in speakers, and have been running my desktop speakers and headphones through the TFT. That is where the disturbance is from. Plugging directly from the Mainboard the sound is clear.

Oh well, as one prbolem is solved another one is made....

thanx for speedy reply...

---

