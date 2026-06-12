---
title: "high pitch sound"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by maskiepop on 2011-10-19
I have a dual boot system on a 64bit desktop. The first system is a WIN7; the other system is an ubuntu 10.10. 

I cannot exactly pinpoint the time when the high pitch sound started -- the reason being that the first person to have noticed it switched off the speakers. It was only after some time that someone pointed out to me that the system is emitting a very high pitch sound.

It happens right after grub loads the system and the ubuntu splash screen appears. During this time only the very high pitch sound is emitted, nothing else. If I remember this correctly there is a sound that accompanies the appearance of the splash screen, right up to the login. That sound is gone; only the high pitch sound remains. Once the high pitch sound starts, it doesn't stop; it goes on continuously.

I have swapped the speakers and the amplifier with another machine, to see if the problem might be with the sound equipment. No such luck; the high pitch sound continued even with the new equipment. 

It might also be useful to note that the sound is normal when I boot up the WIN7 and use that. There is no high pitch sound at all associated with the WIN7 on the same machine.

I have tried troubleshooting the sound problem and have some information about my desktop's hardware and software. It is in [_*[COLOR="RoyalBlue"]my pastebin titled ALSA Details[/COLOR]*_]("http://pastebin.com/u/maskiepop")

Hope someone can help.

---

### Post by anewguy on 2011-10-19
Are you sure the sound is actually coming via an audio device on the PC?  Sometimes a monitor will make a noise like that from either a high voltage problem or from some other problem such as frequency mismatch.  You may want to listen right up by your monitor and see if it is making the noise.

Dave ;)

---

### Post by feedmebits on 2011-10-19
> **anewguy said:**
> Are you sure the sound is actually coming via an audio device on the PC?  Sometimes a monitor will make a noise like that from either a high voltage problem or from some other problem such as frequency mismatch.  You may want to listen right up by your monitor and see if it is making the noise.

Dave ;)

Or you can take out the power cable from the monitor and boot your pc to still if the noise still occurs.

---

### Post by maskiepop on 2011-10-19
> **feedmebits said:**
> Or you can take out the power cable from the monitor and boot your pc to still if the noise still occurs.
Thanks for your responses to my post, guys.

I think I am almost sure that it is not coming from the monitor. And that it is coming from the audio.
1) If I switch off the audio, the noise goes away.
2) If I switch off the monitor when the noise is on, the noise stays on.
3) The noise came up after I pulled the plug from the monitor, and then powered on the desktop, as suggested above.

Here's what I'd like to do:
1) uninstall the docky app, and see if that fixes things.
2) if not, unistall the xbmc media center, and see if the noise goes away.

These are two apps I have installed recently. 

After that, I honestly don't know. I'd rather not re-install if I can help it.

---

### Post by maskiepop on 2011-10-24
Guys, I did a re-install. That fixed the problem. But as I said, I wish I didn't have to do that. Maybe someone can come up with a better way.

---

