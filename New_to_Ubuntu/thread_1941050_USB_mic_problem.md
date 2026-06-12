---
title: "USB mic problem"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by acimi66 on 2012-03-14
I have a USB CAD U1 mic for doing broadcasts. I'm running 11.10. 
When I check my sound systems it shows it there, but makes no sound. 
If i unplug it and plug it back in the sound is there.

Then after some time it drops the sound again.

Any thoughts?

---

### Post by Ms. Daisy on 2012-03-15
Have you plugged it into other USB ports on your machine and had the same problem?

Does Ubuntu recognize the microphone when it has dropped the sound? Check this by running 

```
lsusb
```

---

### Post by acimi66 on 2012-03-15
Hey Thanks Daisy,
Yes the mic seemd to work in other USB ports
And the device does show up with lsusb.

Being the noob that i am I feel I might have to re-install the OS. Because between installing JACK and IDJC I have tried a lot of different "fixes" through the forums but after reading about the linux sound architecture ALSA ( complicated as ALL hell) I feel I should have been more pragmatic in DOCUMENTING what IS/HAS install on my PC.

Any thoughts?

---

### Post by Ms. Daisy on 2012-03-16
I think re-installation is a bit rash at this point. Documentation is always a good idea. Do I understand that you're concerned that all the attempted "fixes" have broken your Ubuntu installation? 

[QUOTE=acimi66]Yes the mic seemd to work in other USB ports
And the device does show up with lsusb.[/QUOTE]
So then the problem is solved?  When you plug the mic into a different USB port the sound does not drop out?

---

