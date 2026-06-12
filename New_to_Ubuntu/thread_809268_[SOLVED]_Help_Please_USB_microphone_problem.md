---
title: "[SOLVED] Help Please: USB microphone problem"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by luckylucky on 2008-05-27
Hi,  I am an exclusive Ubuntu user, but there are just a couple of things that I have to boot into my Windows for once in a blue moon.  For years I had been experiencing a problem using my USB microphone (Logitech) but since I only needed it from time to time I resigned to booting into win for that (of course it works there).

Now I have a need to use it regularly and would like to resolve the issue in Ubuntu so that I can use it within Ubuntu.  I would appreciate anyone's help on this issue.  Thank you in advance.

Basically I plug in the USB microphone to record my voice into Audacity.  Of course I went into audacity to play around in the preferences, selecting the USB microphone option (and trying everything else) but it simply doesn't work.  On this computer I am still using Ubuntu 7.10 as I don't feel I need to upgrade yet (though on the others I have upgraded to current version 8.04).

Please, if anyone call tell me how to fix this I would be very grateful.  

Thank you!

P.S. I am an experienced linux user comfortable hacking xorg & stuff if necessary.  I'm not a coder, or by any means an "expert" level, just that I've been around the block in console.

---

### Post by luckylucky on 2008-05-27
I finally solved this one myself!!!

Here is the solution for using the Logitech USB microphone in Audacity.  

Step 1)  In audacity click Edit > Preferences
In the "Recording" section select the device ALSA: AK5370 which is your USB microphone
Channels set to 1 (Mono)

Step 2)  This is the trick that has stumped me, and probably a ton of you too.  Double click on your volume icon in your task bar / system tray.
Click File > Change Device > AK5370 (ALSA Mixer)
Then raise the volume all the way up (or most of the way up).
It seems that by default it is set to almost zero!!!  

This, I believe is why so many people have been experiencing problems with the Logitec USB microphone.  It is such a fabulous microphone, and am pleased to now be able to use it in Ubuntu!

---

### Post by carlosfocker on 2008-05-27
You solved it faster than I could type. lol good job.

---

