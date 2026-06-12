---
title: "Sound Quality"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by JoHenning on 2008-10-23
Is there anything i can do about the horrible sound quality?

thanks

---

### Post by markbuntu on 2008-10-23
Not without providing some more specific information.

---

### Post by JoHenning on 2008-10-23
I have Logitech 2.1 Speakers, they work perfectly fine connected to an ipod windows etc.

i have a nvida nforce2 sound card.

Only my right speaker works and the sound quality is very bad.

:(

i tired qamix it didnt work, i tried plugging the speakers in and out didnt work...

---

### Post by JoHenning on 2008-10-23
anyone any ideas???

---

### Post by JoHenning on 2008-10-24
?

---

### Post by Delever on 2008-10-24
What exactly is horrible about sound? Do you use ubuntu 8.04 or 8.10?

When I had nForce 2 audio card I experienced bad sound quality too. Specifically, sound skips under small load, like, resizing windows.

---

### Post by igknighted on 2008-10-24
Please, one bump per 24 hours.

What version of Ubuntu are you using?  If it is 8.04, it is almost certainly a PulseAudio issue (a new sound server that was introduced in that version).  There were configuration issues with how it was set up... check out this thread for some possible solutions:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by JoHenning on 2008-10-24
im using 8.04

ony one of my speakers is working and the sound quality is just very bad.
The speakers are new and work perfectly with other systems.

---

### Post by igknighted on 2008-10-24
> **JoHenning said:**
> im using 8.04

ony one of my speakers is working and the sound quality is just very bad.
The speakers are new and work perfectly with other systems.

Again, this sounds like a configuration error with the sound server (pulseaudio)... did you try the tips in the link I posted?

---

### Post by JoHenning on 2008-10-24
Yes, thank you i tried it however it didn't work.
I followed exactly the instructions...

---

### Post by JoHenning on 2008-10-26
anybody any ideas?

---

### Post by fornix on 2008-10-26
Type this command and check whether the PCM is not greater than 80%.
```
$ alsamixer
```
If it is more, reduce it. I used to experience distortion when PCM was 100%.

---

### Post by igknighted on 2008-10-26
> **fornix said:**
> Type this command and check whether the PCM is not greater than 80%.
```
$ alsamixer
```
If it is more, reduce it. I used to experience distortion when PCM was 100%.

Since sound is only coming out of one speaker I doubt this is the issue, but it is possible.  What sound card do you have?  Can you please post the results of the command 'aplay -l'? (that's the lower case letter L, not the number one)

---

### Post by JoHenning on 2008-10-26
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by JoHenning on 2008-10-26
...

---

### Post by JoHenning on 2008-10-29
up

---

### Post by statto1977 on 2008-10-30
I'm having the same problem, and pulseaudio doesn't seem to have worked for me either. This is the output from my aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I've done the "alsamixer -Dhw" command, and PCM is at maximum. Could that be causing the problem, and if so how do I lower it? I also don't seem to be getting any sound at all from flash clips. Really stumped on this.

EDIT: All my sound issues were stemming from the PCM being too high. Lowered it, and it's now fine. Flash is still not working though.

---

### Post by Xerp on 2008-10-30
Yes, if PCM volume is at maximum then things really sound bad - its like putting your 100w stereo on 11 with 10w speakers :) I usually have mine set to about half way, using the volume controls from the applet.

---

### Post by statto1977 on 2008-10-30
Flash is now working too. I just had to install libflashsupport :)

---

