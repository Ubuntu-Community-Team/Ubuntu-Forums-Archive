---
title: "Internal speakers work but not my audio jack speakers"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by chris246 on 2014-06-15
hello, please help my audio jack is not working in ubuntu 14.04 but the internal speakers on my laptop work fine.  i can provide system information to help diagnose the problem.  please tell me if there is a simple way to update my sound drivers or do something to make the audio jack work.

thanks

chris

---

### Post by DuckHook on 2014-06-16
Hi chris246 and welcome to the forums:

On some motherboards, Ubuntu treats each audio output as a separate and independent device that must be manually selected. The front headphone jacks are different than the built-in speakers, HDMI output is separate from analogue speakers, USB headphones are separate yet again, etc.

Before posting your internal system info, plug in your headphones, then open up the sound applet by right clicking on the speaker icon at upper right and selecting "Sound Settings" > "Output". You should see a listing of all your available devices. See if you have a separate device for your audio jack. It may be something cryptic, so try them all with your headphones plugged in using the "Test Sound" button. Also, try the different channels inside the "Mode" button. If you can't find anything that works, please post back the results of:```
lspci -vv | grep -iA12 audio
```and```
aplay -l
```<CAUTION>Be sure to make a note of the device and channel that is the default when you open up the sound applet so that you can at least get back to working built-in speakers before fiddling with the settings as per above.

---

### Post by Ben_Cunningham on 2014-06-16
You are correct DuckHook. I had exactly this problem once and I just clicked the speaker icon up in the top dashboard, selected my headphones and it was all good.

---

