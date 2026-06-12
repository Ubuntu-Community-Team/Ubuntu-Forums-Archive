---
title: "HOWTO: Audigy 2 ZS"
date: 2006-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by _simon_ on 2006-06-11
No sound?
Partial sound?
Bad sound?

1.First make sure that any on board sound is disabled in the BIOS.

2. Open System -> Preferences -> Sound and check that the default sound card is listed as Audigy.

3. Open up Terminal and type: alsamixer

The volumes below are based on my own setup with 5:1 speakers.

Check that the following have the volume set:

Master (about 74)
Bass (set as you like)
Treble (set as you like)
PCM (about 74)
Front (about 74)
Surround (about 76)
Center (about 74)
Audigy A(nalog) (press M on your keyboard to turn it on)

Hopefully you will now have sound!

---

### Post by tarmen on 2009-04-29
Thanks Simon, this solved my problem for sure.
I've seen the information partially on other places but your explanation did it!

---

### Post by screaminj3sus on 2009-04-29
Would this work with my audigy 4? I currently am getting no sound with my audigy 4 and 5.1 speakers. trying it now.

---

### Post by loo0olz on 2009-04-29
thanx pro

---

### Post by AROtotheN on 2009-10-04
What can I do if my BIOS won't let me disable on-board audio?

edit 10/08/2009 nevermind, found it and it works perfectly!

[http://ubuntuforums.org/showthread.php?t=233294&page=2](http://ubuntuforums.org/showthread.php?t=233294&page=2)

---

### Post by dalv on 2009-12-12
Yay, disabling on board sound in BIOS did the trick for me.
Thanks!

---

### Post by gkh73 on 2010-02-01
My card works just fine, but I can't use the headphone jack that's on the front panel.

I do get "sound" out of the headphones when I crank the Analog Mix in the Alsamixer in terminal... a hissing sound.
And if I turn on the microphone I can hear that just fine in the headphones.

I tried turning on the Alsa A(nalog) in the terminal by pressing M but nothing happens.

I recall having some issues getting any audio at first when I switched to 9.10, but then I clicked the Audigy Analog/Digital Output Jack, and I've been fine since then... just can't listen to music/internet in my front panel headphones.  Not a show-stopper but definitely a tad frustrating.

---

