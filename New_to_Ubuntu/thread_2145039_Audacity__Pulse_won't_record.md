---
title: "Audacity / Pulse won't record"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by BNZBKK on 2013-05-14
A few days ago I had to replace my mouse and since then I can't **'record'** in Audacity (but it plays files) - probably due to the old mouse being clicked everywhere in desperation. I've been through Pulse / Alsa and Audacity (Edit/ Preferences / etc etc, ) also the Audacity pages many many times trying to reconfigure but without success.

Any suggestions ?

---

### Post by ajgreeny on 2013-05-14
Are you recording using a mic?  Open up audacity and start to record something, ignoring that nothing is actually recording, then open Pulse volume control application and see if the record and input tabs are set too low or muted.

---

### Post by BNZBKK on 2013-05-14
Here are Pulse screenshots with Audacity on record in the background

---

### Post by ajgreeny on 2013-05-15
Still not recording?

What device is showing as recording in audacity?  See screenshot.

---

### Post by editheraven on 2013-05-15
Try going in gnome alsa mixer and see the level for recording devices. Moreover, in the second screenshot the device seems to be "muted".

---

### Post by ajgreeny on 2013-05-15
No, the second screenshot shows the mute icon with the small x in it, but the icon itself is not selected (see the next icon to its right hand side for a selected icon), so it is not muted.

---

### Post by BNZBKK on 2013-05-15
Everything, radio, YouTube, VLC records as Alsa Default

 'Line-in, Microphone' etc, etc, I've set and re-set them all however when the audio is muted and I can't hear anything ..it records

---

### Post by ajgreeny on 2013-05-16
Just to make sure, what are the audacity preferences set to for the recording devices?

Here's mine,  Default: Rear Mic:0 , and my audacity records fine.

---

### Post by editheraven on 2013-05-16
Show the levels in gnome alsa-mixer.

---

### Post by BNZBKK on 2013-05-16
> **editheraven said:**
> Show the levels in gnome alsa-mixer.


Thanks and here ya go...

---

### Post by BNZBKK on 2013-05-16
> **ajgreeny said:**
> Just to make sure, what are the audacity preferences set to for the recording devices?

Here's mine,  Default: Rear Mic:0 , and my audacity records fine.


Here's mine...

---

### Post by editheraven on 2013-05-17
I don't think that's gnome alsa-mixer. 

[http://www.domenech.org/bt878a-adc/gnome-alsa-mixer-ensoniq.png](http://www.domenech.org/bt878a-adc/gnome-alsa-mixer-ensoniq.png)

---

### Post by BNZBKK on 2013-05-17
> **editheraven said:**
> I don't think that's gnome alsa-mixer. 

[http://www.domenech.org/bt878a-adc/gnome-alsa-mixer-ensoniq.png](http://www.domenech.org/bt878a-adc/gnome-alsa-mixer-ensoniq.png)


Yes you're correct, here it is

---

### Post by editheraven on 2013-05-17
The input device is set to "mic" and the shown levels for mic are too low. Try raise them.

---

### Post by BNZBKK on 2013-05-18
> **editheraven said:**
> The input device is set to "mic" and the shown levels for mic are too low. Try raise them.

....

---

### Post by BNZBKK on 2013-05-22
Anyone ?

---

