---
title: "Strange flash related problem"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by chris-burmajster on 2014-04-09
Hello Everybody,

I put Lubuntu 13.10 on a friend's machine to replace Windows XP. Everything is fine except that when you try to play a video on the BBC News website or on the You Tube website. You click on it and it disappears, you just get white space where the video use to be. I had already installed Ubuntu Restricted Extras and flash is listed as a plugin in Firefox and set to 'always activate', so I can't understand what is going on. I used the very same disk to install Lubuntu on my old XP machine (different hardware) and it all works fine. Can anybody please point me in the right direction? Is it a hardware issue?

Many thanks,

Chris

---

### Post by sudodus on 2014-04-09
Yes, it could be a hardware issue. Please specify the following for the computer

- Computer brand name and model
- CPU
- RAM size
- graphics chip/card
- wifi chip/card

---

### Post by chris-burmajster on 2014-04-09
Thanks for responding. The computer is at home and I'm at work at the moment, so I'll supply full details later. From memory, it's about 7 years old, has an AMD processor, 2Gb of RAM and a 40Gb hard drive. The only embarrassing thing is that it all worked under XP and I was extolling the virtues of Linux, so I now have egg on my face.

---

### Post by sudodus on 2014-04-09
You can check the specs with the advice in this link (particularly the part about K7 processors)
> Be aware that K7's do not offer SSE2 and hence do not support the latest Flash
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by monkeybrain20122 on 2014-04-09
Try right click a flash video and in settings disable hardware acceleration.

---

### Post by chris-burmajster on 2014-04-09
Thank you very much to both of you for this information. That explains both why they had it before and why they don't have it now!

---

### Post by mörgæs on 2014-04-09
If you are satisfied with Flash without acceleration please mark the thread 'solved'.
If you want acceleration please post the output requested in post 2.

---

### Post by chris-burmajster on 2014-04-09
> **mörgæs said:**
> If you are satisfied with Flash without acceleration please mark the thread 'solved'.
If you want acceleration please post the output requested in post 2.

Will do as soon as I get home and try it!

---

### Post by chris-burmajster on 2014-04-09
> **sudodus said:**
> Yes, it could be a hardware issue. Please specify the following for the computer

- Computer brand name and model
- CPU
- RAM size
- graphics chip/card
- wifi chip/card

It doesn't have a name on it, but Sys Info says that it has an AMD Athlon XP processor running at 1733, 2Gb of RAM and a 40Gb hard drive.

---

### Post by mörgæs on 2014-04-09
That's one of the processors which don't support SSE2 and hence not the latest Flash.

There are workarounds here:
[http://ubuntuforums.org/showthread.php?t=2201985](http://ubuntuforums.org/showthread.php?t=2201985)

---

### Post by chris-burmajster on 2014-04-10
Thank you to everybody who replied for your suggestions and help. It's much appreciated! 

I tried every suggestion, but unfortunately I have not been able to get flash to work on Lubuntu. Given that this machine's primary purpose is entertainment / time wasting, I have given up and reluctantly put XP back on it. It's interesting that flash (even flash 13) works with IE 8, but not Firefox 28, so I un-installed that. As my friends are completely non technical, once I have finished the zillion odd upgrades, I'll image the hard disk and burn it to a bootable CD, so that if / when they get attacked they can restore a clean image in a sensible amount of time.

---

