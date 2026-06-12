---
title: "[SOLVED] Who/what controls the mic volume?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by nuddernuby on 2008-07-13
Another basic one. (8.04)
Was testing the mic for Skype when I discovered that Volume Control did not control mic volume. The mic worked but I could not adjust its volume. Is this function controlled by some other programme and how would one go about determining which?
Thank you in advance.

---

### Post by spydon on 2008-07-13
You can double click the normal volume-control and add mic in the settings.

If you write ```
alsamixer
``` is a terminal you will also be able to control it.

---

### Post by nuddernuby on 2008-07-13
Thank you, spydon. No matter how I change the mic level setting in either Volume Control or the alsamixer panel, it stays exactly the same. IOW, recording with Sound Recorder I get exactly the same volume level in the recording, whether mic level is set to min or max.
Hence I suspect that another programme must be controlling it. Any ideas?

---

### Post by spydon on 2008-07-13
Have you tried changing the line-in volume too?

---

### Post by markbuntu on 2008-07-13
Try fooling with the capture levels.

---

### Post by nuddernuby on 2008-07-14
No controls on Volume Control or alsamixer had any effect. Only after a considerable amount of fooling did I discover that changing the box 
> Record from Input:
in Sound Recorder from **Microphone** to **Mix** did anything happen.  So, having the source for the recording set to Microphone does not work at all - and I have no understanding why this should be so.  Setting it to Capture also worked.

Thank you, spydon & markbuntu, for helping with this.

---

### Post by rhomany on 2008-07-17
> **nuddernuby said:**
> No controls on Volume Control or alsamixer had any effect. Only after a considerable amount of fooling did I discover that changing the box 

in Sound Recorder from **Microphone** to **Mix** did anything happen.  So, having the source for the recording set to Microphone does not work at all - and I have no understanding why this should be so.  Setting it to Capture also worked.

Thank you, spydon & markbuntu, for helping with this.

I think I love you. 2 weeks I've been playing around with the mic settings to get sound input. Tinkering with capture fixed the problem completely. Thanks.

---

