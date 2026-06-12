---
title: "What controls what Audacity &quot;sees&quot; as source?"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-03-20
This is a stock, unmodified version of Oneiric. I have a 1970s cassette deck with a headphone output. The cable is 3.5 mm stereo plugs on both ends. The plug goes to my "Line In" port on the 'puter.

I have tried (like crazy) to set Audacity to "see" the correct input device. I have used: defalut line0, default line1, pulse line0 and pulse line1 --- but no matter what setting, the sound "seen" by Audacity is my webcam's microphone. I opened the Mixer and see it reads: Mixer - HDA nVidia (Alsa Mixer). I opened Options and selected and selected both Input to Line. The sliders are locked, the position is high enough to provide some signal and the front mike icon has a red X through it.

Audacity sends the sound to my earphones. 

What am I not doing?

---

### Post by Frogs Hair on 2012-03-20
The tape deck is probably an analog device . Open sound > output and see if you have analog compatibility , if so I don't know what the problem may be. Also make sure the jack works.

---

### Post by Mark_in_Hollywood on 2012-03-20
I was running under XFCE as a desktop, so switching to Gnome and running Sound shows I have the Webcam microphone selected. I thought I had changed this in XFCE, but upon re-logging back from Gnome to XFCE I can now record and playback.

Thanks.

---

