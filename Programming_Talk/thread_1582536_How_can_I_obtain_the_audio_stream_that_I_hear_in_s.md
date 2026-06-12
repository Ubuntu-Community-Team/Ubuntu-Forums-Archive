---
title: "How can I obtain the audio stream that I hear in speaker system or in earphones?"
date: 2010-09-26
forum: Programming Talk
---

### Post by hciotastihissois on 2010-09-26
Let assume that we have the following situation: we have a sound in the speaker systems or in earphones, maybe we play an audio CD, some mp3's or maybe a movie, etc. 
All I know is that the sound goes through sound card to speaker system or in earphones, no matter the source.

How can I obtain the audio stream that I hear in speaker system or in earphones? 

I would like to write an application that record and analyze the audio stream that I hear in my speaker system or in earphones.
My OS is Ubuntu 10.04.

If you have a recommendation like "try to use ALSA", please provide more details like "in alsa-utils you have a class Class_Name, with the following function Funcation1, etc. Try to use the Function5 as in the following example".
Any help is appreciated.

---

### Post by turc0033 on 2010-11-23
If you're using java, you can use the SourceDataLine class which contains a buffer.

---

