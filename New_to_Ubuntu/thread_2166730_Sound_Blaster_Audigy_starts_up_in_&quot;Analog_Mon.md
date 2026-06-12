---
title: "Sound Blaster Audigy starts up in &quot;Analog Mono Output&quot; mode"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by mKtHFw4 on 2013-08-10
I just installed Ubuntu 13.04 64-bit.  I love it!

Just one slight problem.  My Sound Blaster Audigy starts up in Analog Mono Output instead of Analog Stereo Output.  Is there a way to force it to always be in stereo?  Like a configuration file somewhere?

[IMG]https://lh6.googleusercontent.com/-29LoerM5TSg/UgbLLGHTflI/AAAAAAAAnsQ/sfA2UecIFyU/s800/audigy_ubuntu.jpg[/IMG]

---

### Post by alvinmoneypit on 2013-08-10
I have audigy2.  It started working properly after a few boots in my 12.04 64-bit system.  At first, Ubuntu didn't see it at all, then it began working regularly after some time.  How long have you had the system installed?

---

### Post by mKtHFw4 on 2013-08-11
> **alvinmoneypit said:**
> How long have you had the system installed?

I installed Ubuntu 13.04 64-bit yesterday.

---

### Post by alvinmoneypit on 2013-08-17
post again if it still isn't working if you will.

---

### Post by mKtHFw4 on 2013-08-17
Hello,

A revision to my original post... The card operates properly in stereo mode.  Starts up and stays that way.  However, when I go to Sound Settings, it reverts my audio settings to mono (from stereo).  I guess this isn't a bug but I would expect when I go to the audio settings, it wouldn't default to mono... Instead it should default to whatever mode I am currently using.

[IMG]https://lh5.googleusercontent.com/-OjUZ8C-jnNk/UhATdC_0cwI/AAAAAAAAntQ/Y88IBJVECPg/s800/Menu_001.png[/IMG]

[IMG]https://lh5.googleusercontent.com/-DVJpFW8HZe4/UhAUOpk-e-I/AAAAAAAAntY/H6j_Li6weII/s800/Sound_002.png[/IMG]

---

### Post by alvinmoneypit on 2013-08-18
how do you know it's working in stereo mode before you go to sound settings?

---

### Post by mKtHFw4 on 2013-08-18
Because it sounds amazing before I go into Sound Settings and then it sounds like garbage when I enter into Sound Settings.  My ears can discern the difference between mono and stereo.

---

### Post by alvinmoneypit on 2013-08-18
Huh, I've never heard of this problem before.  There has been some issues with the use of microphones on this distrobution.  Do you have a microphone attached when you go to the sound settings?  If so, disconnect it, reboot, and try to go to sound settings again.  If this doesn't help, I don't know what to try except some other app is telling Ubuntu to be in mono, but you say it's working in stereo until you click on sound settings.  Odd.

Make sure you install the updates offered for your system , it still may resolve.  I had some issues with the default mono issue, but it resolved within 36 hours or so on it's own with reboots, and switching back and forth between the onboard sound (ALC892) and Audigy2.

---

