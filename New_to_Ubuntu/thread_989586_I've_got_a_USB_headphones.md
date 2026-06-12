---
title: "I've got a USB headphones"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Kosimo on 2008-11-21
So, I've got a USB headphones and well... I know there is a mass with ALSA, OSS, PulseAudio and all the "preferences" any single app has...
I could setup skype to use those headphones, but not all apps allow to do it. (Flash player for example, and many others...)

I would love to connect my USB Headphones and have all sound automatically sent to the headphones... Then once disconnect, everything back to normal...

Do I am dreaming too much?

---

### Post by Kosimo on 2008-11-22
up

---

### Post by kostkon on 2008-11-22
> **Kosimo said:**
> So, I've got a USB headphones and well... I know there is a mass with ALSA, OSS, PulseAudio and all the "preferences" any single app has...
I could setup skype to use those headphones, but not all apps allow to do it. (Flash player for example, and many others...)

I would love to connect my USB Headphones and have all sound automatically sent to the headphones... Then once disconnect, everything back to normal...

Do I am dreaming too much?
What version of Ubuntu do you have?

---

### Post by Kosimo on 2008-11-22
> **kostkon said:**
> What version of Ubuntu do you have?

Intrepid

---

### Post by kostkon on 2008-11-22
> **Kosimo said:**
> Intrepid
Good, good...

Then you can do exactly what you want easily. 

Just install the *PulseAudio Device Chooser* (its package is called *padevchooser*)

Run it (it will create a menu entry in *Application &#8594; Sound & Video*) and it will put its icon in your taskbar.

Left-click on its icon and select *Volume Control*. In the *Playback* tab you should see the audio streams of the various applications (the one that produce sound, that is) you are running (e.g. *Totem*, *Flash*, etc.). Left click on the stream you want, select *Move Stream...* and a list will appear listing your audio devices (in your case your soundcard and USB headset). You can then select the audio device you want this application to use to send its sound to. And so on...

*PulseAudio* will remember the audio device you have selected the next time you run this application.

Thus, you are having great flexibility on deciding what audio device each of your applications to use. Plus, you are getting individual volume levels per application.

In the *Output Devices* tab you can set the audio device you want to be used as the default by right-clicking on it and enabling the Default option. The same for the *Input Devices*.

You can set the *PulseAudio Device Chooser* to start every time you login from its preferences (i.e. left-click on its icon and select *Preferences*).

Hope you like it. I think it is exactly what you want, right?

---

### Post by Kosimo on 2008-11-22
> **kostkon said:**
> Good, good...

Then you can do exactly what you want easily. 

Just install the *PulseAudio Device Chooser* (its package is called *padevchooser*)

Run it (it will create a menu entry in *Application &#8594; Sound & Video*) and it will put its icon in your taskbar.

Left-click on its icon and select *Volume Control*. In the *Playback* tab you should see the audio streams of the various applications (the one that produce sound, that is) you are running (e.g. *Totem*, *Flash*, etc.). Left click on the stream you want, select *Move Stream...* and a list will appear listing your audio devices (in your case your soundcard and USB headset). You can then select the audio device you want this application to use to send its sound to. And so on...

*PulseAudio* will remember the audio device you have selected the next time you run this application.

Thus, you are having great flexibility on deciding what audio device each of your applications to use. Plus, you are getting individual volume levels per application.

In the *Output Devices* tab you can set the audio device you want to be used as the default by right-clicking on it and enabling the Default option. The same for the *Input Devices*.

You can set the *PulseAudio Device Chooser* to start every time you login from its preferences (i.e. left-click on its icon and select *Preferences*).

Hope you like it. I think it is exactly what you want, right?

Thank you for the detailed explanation. Yes, it is exactly what I want and in fact I'm gonna give it a try right now.  
I'll write here in a couple of minutes :)

---

### Post by Kosimo on 2008-11-22
Ok. It works, so for now on I can finally use my USB headphones for almost everything :)   The only problem is: PulseAudio doesn't remember my settings, and each time I connect the headphones I must go to padevchooser and change settings to the USB device.  It is annoying, but at least works.

Thank you for your advice

---

### Post by kostkon on 2008-11-22
> **Kosimo said:**
> Ok. It works, so for now on I can finally use my USB headphones for almost everything :)   The only problem is: PulseAudio doesn't remember my settings, and each time I connect the headphones I must go to padevchooser and change settings to the USB device.  It is annoying, but at least works.

Thank you for your advice
That's strange.

Do you have your sound playbacks in your sound preferences (*System &#8594; Preferences &#8594; Sound*) set to *Autodetect*?

---

### Post by Kosimo on 2008-11-22
> **kostkon said:**
> That's strange.

Do you have your sound playbacks in your sound preferences (*System &#8594; Preferences &#8594; Sound*) set to *Autodetect*?

Yes it is.   
Actually I am happy with it as I couldn't use my USB Headphones before and now I can...    
There are only two "issues": As I said, I need to change settings each time I connect my headphones. And I need to set up every single app manually.

Thank you again for your help!

---

