---
title: "Microphone can't record sound"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Inseki on 2008-09-15
In my sound settings I have 6 volume controls. The first is for volume, the second is called "line in", the third is "microphone", fourth is "CD", fifth "PCM-2", and the sixth is "input gain". 
I usually operate with line in, microphone and input gain turned off. When I turn on the microphone volume control I can hear my voice and whatever it picks up in the speakers but it doesn't record sound. Also, if it is turned up to max it records some sounds like my voice less clearly.
The line in volume command makes my microphone sound clearer when I turn it on, but it only works in a specific range. At a certain volume there is a sort of clicking sound and you can hear it, and at a higher volume it clicks off again. 
The input gain control is a bit of a mystery to me, but when I try to record, if I have it set to max it instantly resets itself to half volume.

I have tried a numerous variety of settings with these volume controls, but I still can't record sound or use voice programmes like skype. 

If anybody knows anything, or has any advice I would be inconceivably grateful.

---

### Post by Inseki on 2008-09-15
Ah, I forgot to mention I usually have the CD volume turned off as well. I haven't played with it much though, as I don't think it's related to my microphone problems.

---

### Post by Najmudin on 2008-09-15
I'm not sure about your sound card but it might be same as mine so try to double click on the volume icon and select Edit> Prefrences a window will pop up search for CAPTURED feedback and check it, so it will be added to the main volume window try to rise it to maximum, then try to record.
I hope that can help.

---

### Post by Inseki on 2008-09-16
I have checked the preferences or settings before but there are only the six options which I already have checked. Sadly there is nothing which clearly says "captured feedback"

---

### Post by Bucky Ball on 2008-09-16
Double click speaker icon, you should have 3 tabs there with your slider controls - Playback, Recording and Switches. Go to the recording tab. There you will find 'Ext Mic Capture'. The sliders will probably be on 0 or all the way down.

You can also go to the drop down menu 'Edit' to get to your preferences.

---

### Post by Inseki on 2008-09-16
I only have one tab, which says "recording playback". 

[http://img151.imageshack.us/my.php?image=screenshotar6.png](http://img151.imageshack.us/my.php?image=screenshotar6.png)
It looks like this

[http://img48.imageshack.us/my.php?image=screenshot1ju0.png](http://img48.imageshack.us/my.php?image=screenshot1ju0.png)
It may also help to see the recording bit. It doesn't have an option for "kind of recording input", so I think this might have something to do with the problem.

---

### Post by Inseki on 2008-09-16
It also occurs to me to show my sound settings from the system preferences
[http://img440.imageshack.us/my.php?image=screenshot2ul8.png](http://img440.imageshack.us/my.php?image=screenshot2ul8.png)

I have capture set on the OSS now because that is what it says my headset is, I tried to set it to ALSA but when I opened the sound recorder to test it I was told the settings were not appropriate.

---

### Post by Bucky Ball on 2008-09-16
Got ya. On that window, go to file and see if you have another device in there. The OSS is not the best and you should get better options if you use your specific device drivers. Could be the problem.

* Update, just read your last post. Hmm. The driver maybe needs to be set by right clicking the speaker icon and going to preferences there and setting the alsa driver. Make sure that is the only sound window open.

---

### Post by Inseki on 2008-09-16
I switched the device to "capture: monitor source ALSA", and the sound capture settings to "pulse audio sound server" (which I had somehow overlooked before), and so long as the sound capture settings are on pulse audio I can record sound with the sound recorder. However, the volume is incredibly miniscule and it still does not record with skype.

Thank you so much for your advice so far m(_ _)m

---

### Post by Bucky Ball on 2008-09-16
What do you now get in the volume control window when you double click the speaker? Still only the one tag or more? Does sometimes take a little tweaking to get the right combination depending on system and sound card etc.

In the Volume Control, check Edit/Preferences and make sure you have all the appropriate things ticked again. You could even try logging in and logging out again and see if that makes a difference. :)

** Skype: That problem could be a setting in Skype itself. Have you tried opening, there is a little blue 'S' button bottom left, go to 'Options->Sound Devices' and fiddle around there. I have HDA Nvidia (plugw ... etc) selected. If you are plugged into the audio sockets you will probably need the plug devices selected. This bit is trial and error but if the other things are working, Skype should too. I'd say experiment there.

---

### Post by Inseki on 2008-09-16
All the options in the volume control besides the OSS only have one volume control "master", and none of them including the OSS have more than one tag.
But I will try logging in and out to see what changes. Thank you so much for your help.

---

### Post by Bucky Ball on 2008-09-16
Just updated my last post with some Skype info. And no problem, BTW. :)

---

### Post by markbuntu on 2008-09-16
You can read my guide here, it is a troubleshooting and setup guide for sound problems:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by PlanetT on 2008-09-20
Hi All!

I also have problems with my mic, I cannot record any sound. I have unmuted the mic at volume controll but the mic still doesn't work. I made some screenshotes about the volume controll settings. However, the front mic does work, if I enable it, but extremely noisy. I am using Ubuntu 8.04 and trying to use skype. I am quite a beginner to Linux. Does anyone know the solution? 

Thank you!

---

### Post by markbuntu on 2008-09-20
Do you have the mic and mic boost and capture checked in the switches section?

---

### Post by drifter2502 on 2008-09-21
> **markbuntu said:**
> Do you have the mic and mic boost and capture checked in the switches section?
I struggled for ages trying to resolve all my recording problems and then found this stupidly basic but correct answer to all my problems here...
[http://ubuntuforums.org/showthread.php?t=778932&highlight=unable+record+sound](http://ubuntuforums.org/showthread.php?t=778932&highlight=unable+record+sound)

---

