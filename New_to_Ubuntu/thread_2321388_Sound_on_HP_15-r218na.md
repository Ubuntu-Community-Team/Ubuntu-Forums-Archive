---
title: "Sound on HP 15-r218na"
date: 2016-04-22
forum: New to Ubuntu
---

### Post by ncfcdaniel on 2016-04-22
Hi, 
I installed Ubuntu 16.04 lts yesterday and the sound is really quiet compared to what it was like on Windows, it is tinny.
Please help. 
Thanks

---

### Post by RobGoss on 2016-04-22
I'm not sure what you mean by tinny but as long as you have sound you just need to a just it accordingly

---

### Post by ncfcdaniel on 2016-04-22
I've tried turning it up, the 'loudest' is still very quiet.

---

### Post by Mc_Fow1er on 2016-04-22
Quick question: Have you tried plugging in a set of external speakers like headphones or something? Because it might just be an odd bug to do with the on board speakers. If not then it might be a driver that's to blame as I have read here and there on the net that some audio chipsets don't like some Linux distros. I've encountered that a few times trying out some distros in VMs when the virtual hardware generally would have been supported. I know it isn't much help but offering what knowledge I have to others in need is better than nothing in my opinion.

---

### Post by ajgreeny on 2016-04-22
Use command **alsamixer** in terminal and check that the levels of outputs of all channels are not set too low.

Move from channel slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

You can also look in **pulseaudio-volume control** which you open as Sound Settings from a click (or maybe a right click depending on DE in use) on the volume icon in the panel.

---

### Post by RobGoss on 2016-04-22
Clicking on the Sound tab at the top your desktop it should open up the sound settings as suggested you might have to adjust the level in order to raise the volume

If you're already hearing sound then it's just a matter of adjusting it

---

