---
title: "[SOLVED] Audio really low"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by m_ad on 2008-07-24
After playing mp3s on my new system, I've realized the volume is REALLY low. The volume control (physical knob) is all the way up, the system volume is all the way up, and Audacious' volume is all the way up. Usually this would be unbearable (in my old Windows setup). It's barely loud now.

```
matt@ubuntu-desktop:~$ lspci | grep Audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

if I remember correctly, in my Windows machine my audio controller was something along the lines of "SigmaTel."

In Audacious, the current output plugin is set to PulseAudio output Plugin. Switching to OSS or Alsa does nothing.

---

### Post by benditlikebecker13 on 2008-07-24
> **m_ad said:**
> After playing mp3s on my new system, I've realized the volume is REALLY low. The volume control (physical knob) is all the way up, the system volume is all the way up, and Audacious' volume is all the way up. Usually this would be unbearable (in my old Windows setup). It's barely loud now.

```
matt@ubuntu-desktop:~$ lspci | grep Audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

if I remember correctly, in my Windows machine my audio controller was something along the lines of "SigmaTel."

In Audacious, the current output plugin is set to PulseAudio output Plugin. Switching to OSS or Alsa does nothing.

I just had the same problem.  Right click on your volume icon (not left click), open Volume Control Options and you should get a handful of sliders.  Mess with any of them that aren't muted and you should be able to fix the problem.

---

### Post by m_ad on 2008-07-24
This worked :lolflag: thanks.

---

### Post by DeMartini on 2008-07-24
Thanks this worked for me as well, kinda silly I didn't think to check that....:guitar:

---

### Post by RequinB4 on 2008-07-24
For future reference, putting the PCM level up too high can trade off with sound quality.  If you have a problem such as that, just put PCM back down some.

---

### Post by caljohnsmith on 2008-07-25
> **RequinB4 said:**
> For future reference, putting the PCM level up too high can trade off with sound quality.  If you have a problem such as that, just put PCM back down some.
And if we want to be really pedantic about it :) , the "magic value" for PCM volume is 74%: anything above 74% means there is digital amplification, which can cause distortion *if* the original signal is all ready using the full digital dynamic range. Setting PCM < 74% means you are attenuating the digital signal, which there is usually no reason to do since you will achieve better signal-to-noise ratio (SNR) if you just decrease the master volume. 

Thus it is usually ideal to set PCM volume at exactly 74%, and use the Master volume to adjust the overall volume. Only in cases where you know your digital sound signal is low, then you can crank PCM volume up higher and you won't get any distortion.

OK, sorry--I'll get off my soapbox and end my pedantic diatribe here. I just can't help being interested in stuff like that since I'm an electrical engineer. :)

---

### Post by drs305 on 2008-07-25
> **caljohnsmith said:**
> Thus it is usually ideal to set PCM volume at exactly 74%, and use the Master volume to adjust the overall volume. Only in cases where you know your digital sound signal is low, then you can crank PCM volume up higher and you won't get any distortion.


And to answer the next question: how do you set 74% when you right click on the speaker but get only slider bars without percentages:

Open 'alsamixer' in terminal, expand it to full screen (at least I have to), use the arrow keys to move to the PCM bar, and adjust it to your wishes.

;-)

---

