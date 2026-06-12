---
title: "No Sound - Help Please?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Bye1918 on 2008-09-04
Okay, I decided to take the plunge and dual-boot Ubuntu and Windows XP. But after I install Ubuntu into its own partition, boot it up, get all the packages I want/need, I go to YouTube. No sound. Video, but no sound.

Curious, I try Rhythmbox. When I try to play an .OGG, nothing. No sound whatsoever. The "Sound Device" tests in the System menu also come up blank. They just say "Testing" with a bar going back and forth below them and no sound coming from my speakers.

Can I get some help here?

---

### Post by HunterA3 on 2008-09-04
Do you know what soundcard is in your system?

---

### Post by halitech on 2008-09-04
open a terminal (Applications - Accessories - terminal) and post the output of```
lspci
``` and ```
aplay -l
```

---

### Post by Bye1918 on 2008-09-04
No, but I've been reading up, and I think this may help you guys help me.

Here's the result when I enter "aplay -l" in the terminal.

[INDENT]**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/INDENT]

---

### Post by Bye1918 on 2008-09-04
The lspci command just pumps out every piece of hardware in the computer. I doubt you need that if you have just the soundcard. If you do, tell me.

---

### Post by Bye1918 on 2008-09-04
Any ideas folks? I imagine it's gotta be something simple, I just am not familiar enough with Ubuntu or Linux in general to do it.

---

### Post by knattlhuber on 2008-09-04
There is a "Comprehensive Sound Problem Solutions Guide" by LordRaiden, it has helped many of us here to get their soundcards working:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by Bye1918 on 2008-09-04
Can't find my solution. As I say, I really don't quite know what I'm doing with the command line, and thusly I'd really appreciate if somebody could help me specifically.

---

### Post by Bye1918 on 2008-09-04
Got it! Messed around with alsamixer long enough that I finally unmuted the right thing! It was changing surround from "shared" to "independant" that did the trick.

---

### Post by knattlhuber on 2008-09-04
> **Bye1918 said:**
> Got it! Messed around with alsamixer long enough that I finally unmuted the right thing! It was changing surround from "shared" to "independant" that did the trick.

Great! Welcome to Ubuntu!:guitar:

---

