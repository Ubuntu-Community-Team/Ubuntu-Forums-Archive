---
title: "Intrepid: How to un-mute microphone automatically at restart"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by shishirjaiswal on 2008-11-02
I am new to ubuntu and linux hence forgive me if this is something very stupid.
I recently upgraded from 8.04 (Hardy) to 8.10 (Intrepid). After the upgrade, external microphone is mute-ed everytime I reboot the system.
This did not used to happen with 8.04.
It is more of a nuisance than a problem to unmute it manually before initiating a voice chat/VOIP Call.
Any help in making it not mute the mic (or autmatically unmute after restart) is appreciated.

---

### Post by Melindrea on 2008-11-03
I'll add to this one. I can not get my microphone to work at all, whenever I open the preferences, capture and digital are both muted, even though I know that I've unmuted it a moment earlier.

Edited to add: In fact, all microphone settings are reset. Capture is toggled off, and Digital is toggled off, aswell as volume going down to 0.

---

### Post by TeoK on 2008-11-05
> **shishirjaiswal said:**
> I am new to ubuntu and linux hence forgive me if this is something very stupid.
I recently upgraded from 8.04 (Hardy) to 8.10 (Intrepid). After the upgrade, external microphone is mute-ed everytime I reboot the system.
This did not used to happen with 8.04.
It is more of a nuisance than a problem to unmute it manually before initiating a voice chat/VOIP Call.
Any help in making it not mute the mic (or autmatically unmute after restart) is appreciated.

bumped.

identical problem.

---

### Post by titimoi on 2008-11-05
same for me.. still haven't found anything yet..

---

### Post by Dr.Suave on 2008-11-12
I have the same problem as Melindrea - just upgraded to Ibex from Gutsy, and Gutsy worked fine with my mic!

I've even disabled pulseaudio and told the system to use ALSA, but still no luck.

What the chuff?

Wilf

---

### Post by spegru on 2008-11-22
same problem for me
Mic keeps muting itself after a few seconds
works fine while it is working - and then it mutes
help!

---

### Post by albesan on 2008-11-22
same here

---

### Post by mgangav on 2008-11-22
Bump. Same problem here.

---

### Post by HydroModeler on 2008-11-26
Same here.  Dell Inspiron 1420.

---

### Post by arcticmagnolia on 2008-11-29
Same here! For me, the problem started couple days ago after downloading updates for 8.10. My mic stays now continuously muted. I have tried different solutions with no luck.. 

Is there configuration file where these settings could be changed perhaps? Can I undo updates (& where I could find what updates I have installed recently)? 
Major issue and seems to be that many are experiencing the same problem... 
Ubuntu-team, will you please do something!

*irritated* :evil:

- i386, amd, nVidia CK804 AC'97 Audio Controller, external mic -

---

### Post by arcticmagnolia on 2008-11-29
*PHIUF!*
This is how I managed to solve this problem.. 
- installed gnome-alsamixer (sudo apt-get install gnome-alsamixer)

Then checked that out (gnome-alsamixer) and there the Capture setting was okey -> So I went to volume control and changed device from NVidia to Realtek ALC658D (OSS Mixer). Then, on the Capture tab, I unmuted the Microphone. It worked for me. 

Don't know exactly what's the magic here, since it worked fine previously with nVidia... We'll see how long this solution lasts!

Oh, and I also installed all alsa+pulseaudio stuff as well (don't know does it make any difference though, but just in case)

---

### Post by arcticmagnolia on 2008-11-29
Sorry, no problemos...

---

### Post by linux_tech on 2008-11-29
1420/ 1520 mic
[http://ubuntuforums.org/showthread.php?t=956565](http://ubuntuforums.org/showthread.php?t=956565)

---

### Post by naeem.ally on 2009-02-18
Hi

I have a t61 and after reading quite a few posts i made this change and it worked for me.

1.go to System > Preferences > Sound
2.under the "device" tab there is a field Sound capture
3.change the drop down list to HDA intel AD198x Analog (ALSA)

Under Volume Control i set the volume for Capture to full, it stills shows that its mute but it unmutes itself while making a call on skype.

---

