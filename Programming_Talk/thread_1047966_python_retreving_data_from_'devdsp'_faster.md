---
title: "python: retreving data from '/dev/dsp' faster"
date: 2009-01-22
forum: Programming Talk
---

### Post by h12 on 2009-01-22
I'm looking for a way to retreive data from /dev/dsp. It needs to be in the format it would be in if it were retreived by: 

dsp = file('/dev/dsp')
dsp.read(2064)

I have already tried pymedia and ossaudiodev. ossaudiodev works if I do not set any paramiters, just: 

audio_in= ossaudiodev.open("/dev/dsp", "r")

And there is a large speed increase, but still lag. 
Is there a data format that I could set ossaudiodev to that would be the same that comes out of reading /dev/dsp directly from file?

---

### Post by h12 on 2009-01-22
Sorry to reply to my own thread: the format type is unsigned eight bit audio, AFTM_U8, and streaming it through osaudiodev only works at the default sample rate of 8000.

So, is there any way to stream AFTM_U8 faster than the default rate?

---

