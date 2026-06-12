---
title: "Removing PulseAudio"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by justbinfishin on 2014-02-11
[COLOR=#000000]Short intro: I installed ubuntu 12.04 yesterday on my 3yo desktop. After demo-ing Windows 8 (I need a Microsoft live account just to log into my own computer?!?) on my desktop & hearing plans for Windows 10 to be cloud-based, I decided that Microsoft will never get another dime of my money.[/COLOR]

[COLOR=#000000]Anways, I installed PulseAudio Equalizer, and it caused immediate problems in my music playback exerience (lags and scratchiness every time I change the volume of a playing song). I ran sudo apt-get autoremove pulseaudio, and then sudo apt-get purge pulseadio. That didn't work, pulseaudio is still installed and still works. So I looked it up on this forum and followed the directions on [/COLOR][http://ubuntuforums.org/showthread.php?t=841911](http://ubuntuforums.org/showthread.php?t=841911)[COLOR=#000000] . I ran sudo apt-get install esound, followed by sudo apt-get remove pulseaudio, and purged it again. The app is still installed... sudo apt-get purge returns "pulseaudio is not installed, so not removed". [/COLOR]

[COLOR=#000000]What gives?[/COLOR]

[COLOR=#000000]Thank you[/COLOR]

[COLOR=#000000]Justin B[/COLOR]

---

### Post by monkeybrain20122 on 2014-02-11
I don't know, that thread is outdated (from 2008) and nowadays removing pulseaudio is more likely to break your sound than to fix it. Your problem could probably have been fixed by adjusting some settings.Since pulseaudio is installed by default I am not sure why you would need to install it (do you use lubuntu?)

---

### Post by BlinkinCat on 2014-02-11
There is a little about Pulse Audio here -

[http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

---

### Post by justbinfishin on 2014-02-11
I was unaware it came pre-installed. I was just perusing the web looking for a whole-system equalizer and tried to install it. I had no idea it was there till after I ran the install prompt. I guess I'll leave it in place but keep the equalizer disabled. Whenever I change the volume in Rhythmbox, the playing song goes scratchy and skips for a few seconds afterwards.

---

### Post by NM5TF on 2014-02-11
you might try Audacious Player....available from Software Center.....

has it's own equalizer......still goes thru Pulseaudio anyway, but works very well

am listening to it right now....

YMMV

tommy

---

