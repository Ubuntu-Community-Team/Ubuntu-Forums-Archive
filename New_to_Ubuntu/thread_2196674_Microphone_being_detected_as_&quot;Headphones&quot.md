---
title: "Microphone being detected as &quot;Headphones&quot;"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by fengyang-wang-0 on 2013-12-30
I have an [HP Pavilion 15-e073ca]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c03785353"), which has a combo headphones-out/microphone-in jack. I recently purchased an external microphone, a Nexxtech desktop microphone. This microphone is not being detected as a microphone, but rather as "headphones".

To be clear, this is what Sound Settings ("Output" tab) displays when the microphone is **not** plugged in:
[IMG]http://i.imgur.com/ZVMHp5O.png[/IMG]

This is what the same screen shows when the microphone is plugged in:
[IMG]http://i.imgur.com/StIadRt.png[/IMG]

The "Input" tab looks like this regardless of whether the microphone is plugged in:
[img]http://i.imgur.com/XPCqRQ0.png[/img]

I must note that when the microphone is plugged in, sound output does not work, but the laptop's internal microphone continues to function. This leads me to suspect the microphone is being detected as a headphones.

I'm perplexed as to what's causing this and have been unable to locate any prior guides for resolving the issue. Is there a way to force the OS to treat the "headphones" as a microphone? Thanks in advance for any help!

---

### Post by conversationjames on 2014-01-02
Sounds like some configuration needs to be done... If these links don't help, maybe get a USB mic?[URL="http://ubuntuforums.org/showthread.php?t=1502395"]
Mic/combo jack post[/URL]
[Headset/mic adding a line to alsa-base.conf]("http://ubuntuforums.org/showthread.php?t=2057466")
[Mic bug on laptop]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/950490")
[Remove pulse and install alsa]("http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/")
[Alsa mixer]("http://en.wikipedia.org/wiki/Alsamixer")

---

