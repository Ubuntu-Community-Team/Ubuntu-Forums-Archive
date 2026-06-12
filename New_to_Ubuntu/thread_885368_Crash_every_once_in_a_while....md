---
title: "Crash every once in a while..."
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Roasted on 2008-08-10
I just got a random crash. I was on firefox with 4 tabs open, two were YouTube, one was MySpace, and my active one was replying to a thread on Ubuntu Forums. I was listening to Amarok. I made a typo and hit backspace, and suddenly my system locked up, leaving the mp3 playing in Amarok to sound like a broken record player, repeating the last second sang over and over and over.

This happened once or twice before, and I have to wonder... is it a good chance it's the flash player causing it?

---

### Post by Vivaldi Gloria on 2008-08-10
> Flash 9 does not support PulseAudio by default, but there is a support library called "libflashsupport" that enables PulseAudio output in Flash. Unfortunately, this support library causes Flash content to occasionally crash when opening new pages. There is a workaround: ...

from

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by Roasted on 2008-08-10
I was about to respond back and be like heyyyyyyy I don't have pulse installed! But I forgot, Hardy has it somehow by default, even if you don't "truly" use it. Right?

Guess my fix is installing libflashsupport?

---

### Post by Vivaldi Gloria on 2008-08-10
> **Roasted said:**
> I was about to respond back and be like heyyyyyyy I don't have pulse installed! But I forgot, Hardy has it somehow by default, even if you don't "truly" use it. Right?

Guess my fix is installing libflashsupport?

Yes, Hardy definetely has pulseaudio. I suggest you follow that guide closely. Just installing libflashsupport might not be enough.

---

### Post by Roasted on 2008-08-10
I've tried to follow that guide, many times. Despite the fact the guide may be pretty nice, the simple blunt fact is that Pulse just isn't all there in Hardy. I'd rather tolerate a random crash now and then than have to go through loopholes and do backflips to get Pulse to work. 

But, at the same token, I had libflashsupport installed before I formatted and I never had a crash. So I'm sure it helped my case. I'll give it a shot.

---

### Post by Roasted on 2008-08-10
Hey, folks. Try going to this news web site. Every time I open the video to be played, firefox just crashes.

I've tried this both with libflashsupport installed and uninstalled.

[http://www.wgal.com/video/17122708/index.html](http://www.wgal.com/video/17122708/index.html)

EDIT - cancel that. I didn't properly restart firefox after uninstalling libflashsupport.

libflashsupport is indeed the reason that this web site crashes. Without it, it works perfectly fine. Guess it doesn't really help out stability issues that much at all, does it?

Can ANYBODY with libflashsupport installed view that video? Why is it giving me issues?

---

### Post by L Campbell on 2008-08-10
> **Roasted said:**
> Hey, folks. Try going to this news web site. Every time I open the video to be played, firefox just crashes.

I've tried this both with libflashsupport installed and uninstalled.

[http://www.wgal.com/video/17122708/index.html](http://www.wgal.com/video/17122708/index.html)

EDIT - cancel that. I didn't properly restart firefox after uninstalling libflashsupport.

libflashsupport is indeed the reason that this web site crashes. Without it, it works perfectly fine. Guess it doesn't really help out stability issues that much at all, does it?

Can ANYBODY with libflashsupport installed view that video? Why is it giving me issues?


I have been having Firefox just 'crash' several times every day, too.

When I went to the website you mentioned, sure enough, Firefox crashed.

I checked and do have ' libflashsupport ' installed.

---

### Post by t0p on 2008-08-10
> **Roasted said:**
> Hey, folks. Try going to this news web site. Every time I open the video to be played, firefox just crashes.

I've tried this both with libflashsupport installed and uninstalled.

[http://www.wgal.com/video/17122708/index.html](http://www.wgal.com/video/17122708/index.html)

EDIT - cancel that. I didn't properly restart firefox after uninstalling libflashsupport.

libflashsupport is indeed the reason that this web site crashes. Without it, it works perfectly fine. Guess it doesn't really help out stability issues that much at all, does it?

Can ANYBODY with libflashsupport installed view that video? Why is it giving me issues?

libflashsupport doesn't help with stability, no - what it does is fix pulseaudio problems.  Until I followed that pulseaudio howto, I didn't have audio playback while watching flash vids.  Now I have sound, but also a browser that tends to crash sometimes.

Far from a perfect fix.  But until someone who knows what they're doing (ie not me, nor you) issues a proper fix, it'll have to do.

---

### Post by Roasted on 2008-08-10
Then figure this one out...

I am using ALSA, Ubuntu Hardy Heron 32 bit 8.04, Flash 9, Firefox 3.

I am not using Libflashsupport, yet I can watch youtube videos and listen to amarok at the exact same time without any issues. And I did not uninstall pulseaudio.

Under system-preferences-sounds, everything is set to ALSA.

As long as Amarok's engine is set to ALSA, everything works. However, once I install libflashsupport, Amarok must be on auto detect for everything to work. With this, my browser crashes now and then, as you said as well.

But, like I said, I can just not install libflashsupport and set Amarok to ALSA and everything works. Why? 

I posted a detailed thread regarding this less than an hour ago, because I want to see if anybody else has gotten the same results I did. 

[http://ubuntuforums.org/showthread.php?t=885840](http://ubuntuforums.org/showthread.php?t=885840)

---

