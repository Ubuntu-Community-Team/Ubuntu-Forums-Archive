---
title: "[SOLVED] No Sound"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by duckfeet on 2008-07-23
Just loaded 8.04, happily, works fine--after several failed attemps--from USB...

But no sound: I thought it was the Adobe flash plugin I was lacking--I use Opera, btw, but I looked on here, and found out how to put that in from Synaptycs...kept searching, did what was suggested: no sound, and on other HD, in Windows, it works fine...on Ubuntu, doesn't work, neither on Rythmbox, or NPR radio, or anything...

Spent last hr on here, on Terminal, did: 
"asoundlist"
   Audio PCI
   Intel

did "alsamixer", and everything looked good...

When I go to System/Preferences/Sound, under Devices, I have for Sound playback: ALC880 Digital.
For Music and Movies I have Autodetect.

I am so happy w/everything else, and you'all have been helpful, and I have been searching the forums, but I either get bogged down, or don't understand what I am to do...

TIA

geff

---

### Post by northern lights on 2008-07-23
Can you post the output of ```
cat /proc/asound/cards
```

Thank you.

---

### Post by duckfeet on 2008-07-23
geff@geff:~$ cat /proc/asound/cards

 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xdc00, irq 19
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefffc000 irq 16






> **northern lights said:**
> Can you post the output of ```
cat /proc/asound/cards
```

Thank you.

---

### Post by northern lights on 2008-07-23
mkey.

So your machine's got two sound devices - an onboard Intel Chip and a PCI audio device.

Which one are you wanting to use?

What is set as default in "System > Preferences > Sound"?

---

### Post by duckfeet on 2008-07-23
I'd be happy with either one. I tried different devices in preferences/sound  but still nothing, so I set them to "autodetect" unless you think different..appreciate the help...
edit: default is Alsa880, I reset to autodetect, just to see, still nothing...

> **northern lights said:**
> mkey.

So your machine's got two sound devices - an onboard Intel Chip and a PCI audio device.

Which one are you wanting to use?

What is set as default in "System > Preferences > Sound"?

---

### Post by northern lights on 2008-07-23
I assume you plugged your speakers into the respective device when it was selected?

Have you left the speakers in either line-out and gone through each device in the drop-down menu while checked the "Test Sound" everytime?

---

### Post by duckfeet on 2008-07-23
I hand't checked that, since it was working fine on my other Hard Drive, w/windows, on same computer...but I'll check, and do the tests...

> **northern lights said:**
> I assume you plugged your speakers into the respective device when it was selected?

Have you left the speakers in either line-out and gone through each device in the drop-down menu while checked the "Test Sound" everytime?

---

### Post by kcoylenet on 2008-07-23
I had this problem with Hardy, and it turned out that the volume control was set to 'mute'. Right click the volume control in the upper right of the menu bar. OPen 'preferences.' Check to see that "master" isn't set to mute.

---

### Post by Dave Otter on 2008-07-23
Try going to BIOS and disable on board sound

---

### Post by duckfeet on 2008-07-23
Knowing me, I figured that it would be something like that, as my problems are usually the kind that are obvious to me...in hindsight...but this one I actually did check...what I'm doing now is removing the sound card, as I have another idea, since it has two devices...

Thanks...


> **kcoylenet said:**
> I had this problem with Hardy, and it turned out that the volume control was set to 'mute'. Right click the volume control in the upper right of the menu bar. OPen 'preferences.' Check to see that "master" isn't set to mute.

---

### Post by duckfeet on 2008-07-23
Thanks to this, and the previous poster pointing out that I also had a sound card, not just inhouse sound...of course it seems obvious, but I guess the linux setup was reading the sound care, rather than the inhouse setup, which is why Windows was working, as I guess it was reading either both, or just the netchip...

Anyway, I removed the sound card, all is well, working fine,,,

Thankyou...

> **Dave Otter said:**
> Try going to BIOS and disable on board sound

---

### Post by duckfeet on 2008-07-23
Working!  Thankyou for helping me, and sticking with me on this...your last post made it seem to me that probably what was happening, was that Linux was reading the sound card, while my XP OS was probably reading the in-house stuff...so just to make sure, I removed the sound card, and rebooted, and it worked fine.

I may put the sound card back in, but this is fine for me...so now I have Johnny Cash, once again, blasting away w/"Hey Porter"....

Kind of a learning experience for me, and again, I really appreciate the help...

geff


> **northern lights said:**
> I assume you plugged your speakers into the respective device when it was selected?

Have you left the speakers in either line-out and gone through each device in the drop-down menu while checked the "Test Sound" everytime?

---

