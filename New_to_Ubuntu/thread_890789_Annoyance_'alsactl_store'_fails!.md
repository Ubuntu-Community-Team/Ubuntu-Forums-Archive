---
title: "Annoyance: 'alsactl store' fails!"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by iamajd on 2008-08-15
I tried seeking help in the Hardware & Laptop forum with no success ([http://ubuntuforums.org/showthread.php?t=888119](http://ubuntuforums.org/showthread.php?t=888119)), so I thought I'd try here...


This problem is more like a minor annoyance.  It has only three symptoms:

Symptom 1)
While "Shutting Down ALSA" as the computer is shutting down, the following appears:
```
alsactl store: get_control: 209: Cannot read control info '2,0,0,Master Playback Volume,0': No such file or directory
```

Symptom 2)
Since "alsactl store" always fails, sound levels are reset at boot (there is an annoying hiss from CD and Mic that goes away when they are muted).

Symptom 3)
The volume slider sticks to the top in the volume control applet (although this might not actually be related, perhaps it could help with troubleshooting).

Other info:
The computer in question is a Toshiba Satellite A105-S1014.
I've appended /etc/modprobe.d/alsa-base with "options snd-hda-intel probe_mask=8 model=auto"
Sound works in the LiveCD, but "sudo alsactl store" has the same error.
I believe this to be new as of Hardy Heron.

Please let me know what info/files I might include to be of the utmost assistance.

---

### Post by skyraven on 2009-04-16
Hello there,

I know this is old..but did you find any solve/answer to your problem ?

I'm having something similar with a PS3 Eye camera connected to my PC..the microphone on it is recognized but won't work with alsa..
$ alsactl store

alsactl: get_control:262: Cannot read control '2,0,0,Mic Capture Volume,0': Invalid argument


-
Mihai

---

### Post by iamajd on 2009-04-16
Mihai,

Sorry. I don't remember if I ever found a solution but I'm pretty sure it was never resolved... unless of course you consider replacing my old laptop with a newer one the answer. I wish I had something more helpful to share with you.  Best of luck!

-AJ

---

