---
title: "Microphone problems"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Inseki on 2008-08-10
I have been going through the forums trying various things to be able to record sound, but as of yet to no avail. 

When I turn on the microphone volume, in the sound settings, it plays over my speakers, or in my headsets, but it will not record sound and doesn't work with Skype. 

Any advice? It seems my microphone is working because I can hear it, and the speakers in the same headset it is a part of work. 

Thank you m(_ _)m

---

### Post by ajmorris on 2008-08-10
> **Inseki said:**
> I have been going through the forums trying various things to be able to record sound, but as of yet to no avail. 

When I turn on the microphone volume, in the sound settings, it plays over my speakers, or in my headsets, but it will not record sound and doesn't work with Skype. 

Any advice? It seems my microphone is working because I can hear it, and the speakers in the same headset it is a part of work. 

Thank you m(_ _)m

I there, have you tried running sudo alsaconf to configure your sound card with alsa?
Also, if you run ```
arecord test.wav
```and speak into your mic, do you get any errors outputed to the CLI?

AJ

---

### Post by Inseki on 2008-08-10
I tried the arecord test, and this was my result

> &#37682;&#38899;&#20013; WAVE 'test.wav' : Unsigned 8 bit, &#12524;&#12540;&#12488; 8000 Hz, &#12514;&#12494;&#12521;&#12523;

Recording WAVE 'test.wav' : Unsigned 8 bit, route 8000 Hz, Monorail 

The recorded file played no sound, I then tried to record something else with the sound recorder but it alos failed to capture any sound. 

In the sound recorder programme, there is an option &#37682;&#38899;&#12377;&#12427;&#20837;&#21147;&#12398;&#31278;&#39006; Type of Recording Input, that has a drop menu next to it, but there is nothing in the menu to select.

---

### Post by cenhfan on 2008-08-15
Have you turned on the Capture channel yet?
edit: I mean when you open the mixer (Kmix)

That was the problem in my case. Had exactly the same problem.

Wish you luck!

Greetz,
Timo

---

### Post by muhsinmuttaqi on 2008-08-22
Hello

How do I turn on the Capture Channel? (HDA Intel (Alsamixer)

---

### Post by cenhfan on 2008-08-22
right-click, channels -> capture.
(in the mixer)

---

### Post by roy.nico on 2008-09-07
Hi, 

i have exactly the same problem under Ubuntu Hardy : i can hear my microphone in the speakers, but, i can't record the sound. 

Did you find a solution ? 

nicolas

---

### Post by ooobuntooo on 2008-09-07
```
alsamixer
```

Type this into the terminal and put the volume up for the microphone.

---

### Post by Crafty Kisses on 2008-09-07
I'd like to see the results of this command:
```
lspci
```

---

### Post by drifter2502 on 2008-09-21
I had this problem for months until I found this...
[http://ubuntuforums.org/showthread.php?t=778932&highlight=unable+record+sound](http://ubuntuforums.org/showthread.php?t=778932&highlight=unable+record+sound)

---

