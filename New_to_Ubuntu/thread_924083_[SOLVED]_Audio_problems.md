---
title: "[SOLVED] Audio problems"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by jrsc109 on 2008-09-19
I'm getting there, and resolved my graphics problem all by myself - must be getting brave.  I'm thoroughly enjoying this Linux thing...

However, an audio issue is outstanding.

The problem is, I have audio, but I have to turn the speakers up to full to hear anything.
Since there is some sound, it's more than just a 'not detecting soundcard' problem.
It's a dual-boot with XP, and the sound on XP is normal.

Any ideas?

Thanks

---

### Post by Orange_and_Green on 2008-09-19
Hi jrsc109:KS

Welcome to Ubuntu and congratulations on your bravery with the Graphics!

For the audio part:

1) Do you know what hardware you are using?
2)Type "alsamixer" in a shell, make sure the main channel is up to 100% (0 dB) and try muting ('m' key) any unnecessary stuff on the far right side
Unmuting everything is also an option worth trying, although, in my case the opposite is true (I get no sound if I don't mute the external amplifier)
3) A few articles that might help you further:


[https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems")
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

Good luck:KS

---

### Post by jrsc109 on 2008-09-19
Thanks Orange_And_Green

I'm at work, and will have to wait until this evening to try this.  Appreciate the quick response.

:)

---

### Post by jrsc109 on 2008-09-19
Tried this and now solved - thanks very much for your help.  Now to solve the external hard drive problem...

---

