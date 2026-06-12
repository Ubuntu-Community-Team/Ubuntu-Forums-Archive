---
title: "Sound recorder input select for streaming ?"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by Innernet on 2012-05-27
Hi.
Is there a way for 12.04 to choose the audio from a streaming website to be recorded ?
It is for a Presario CQ60 Compaq laptop, with its 'integral sound card'

The recorder works, but for the microphone only, and cannot see how to select 'internal' input.

---

### Post by ajgreeny on 2012-05-27
> **Innernet said:**
> Hi.
Is there a way for 12.04 to choose the audio from a streaming website to be recorded ?
It is for a Presario CQ60 Compaq laptop, with its 'integral sound card'

The recorder works, but for the microphone only, and cannot see how to select 'internal' input.
With the recorder running you need to open pulsaudio-volume-control (pavucontrol package if you don't already have it installed) and set the "Recioed stream from" to "Monitor of ..." as shown in my screenshot.

This is from 10.04, but I am assuming it is something similar in 12.04; I've not tried it yet.

---

