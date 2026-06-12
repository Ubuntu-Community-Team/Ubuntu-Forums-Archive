---
title: "Loud Beep on Shut-down After Installation of &quot;Ubuntu Tweak&quot;"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by Javelin Dan on 2012-08-08
Running Ubuntu 12.04 on a Mac G-4 Powerpc, 1Ghz processor, 1GB RAM, 40 GB hard drive.
   
  I’m posting this in the beginner’s forum as I believe it is a basic operational question rather than a powerpc question. 



Last week, I installed “Ubuntu Tweak” and since that time, I have an extremely loud beep on shut-down – loud enough to wake the dead. I went into “Ubuntu Tweak” and turned off event sounds, but the beep is still there. I'm not discounting the idea that it may inadvertently be operator error and not have anything to do with "Ubuntu Tweak".



I haven’t been able to find where I can turn this off, turn the volume down, or otherwise control it, and I’m getting tired of scraping my wife off the ceiling every time she uses her computer. Can someone shed some light on this please?

---

### Post by philinux on 2012-08-08
Can you tell if the beep is coming from the pc speakers or from the pc itself?

---

### Post by zeroseven0183 on 2012-08-08
Have you tried uninstalling Ubuntu Tweak to see if the loud beep still comes out during shutdown?

---

### Post by Javelin Dan on 2012-08-08
phiillinux - It's so stinkin' loud it _*has*_ to be coming from the speakers. But no, I don't know for sure so I'll have to pay attention and get back to you on that.

zeroseven - Yeah, I guess I'll try that too. The truth is, about the only thing I found of value to me in there is Computer Janitor and I already know I can install that separately if I want. 

I guess the only other thing I would like to know is there anything else that can cause this and where would the control for it be? It's still remotely possible that I accidentally turned something on without realizing it...

---

### Post by Javelin Dan on 2012-08-09
OK, I did check and the sound is definitely coming from the speakers. I did uninstall "Ubuntu Tweak" and the sound still persists. I found a thread talking about going into KDE configuration and either turning down the volume, or turning off the sound altogether. I did both with no results. I'm going to have a look at ALSA, but don't really expect to find anything there. Still would appreciate some help if someone's able.

---

### Post by jsthrower on 2012-08-09
Might want to mute the speaker before shutdown until you sort it out.

---

### Post by Jennasis on 2012-08-12
I am having what appears to be the same issue, but mine is usually at start-up. It is as if the system welcome and goodbye sounds/chimes (if there are any) have just been replaced with a really loud klaxon. It is coming via the 5.1 system; I have actually had this issue for ages but never found a way to fix it from googling, so would be really nice to have a solution! 

PC Speaker and Beep are muted in alsamixer
OSS prioritised, pulse second, alsa third (I think)
Sometimes it doesn't happen... but it is only ever at startup and/or shutdown

---

### Post by Javelin Dan on 2012-08-12
OK, this is creeping me out, but the loud beep is GONE! Here's the only thing I did:

As I previously threatened, I un-installed Ubuntu Tweak and installed Computer Janitor. As I reported, this had no bearing on the shut-down beep whatsoever. I decided that I liked the GUI in Ubuntu Tweak much better (gave much more information about the cruft it was cleaning), and since it had no impact on the beep, I figured I would remove Computer Janitor and re-install Ubuntu Tweak. I did so Friday evening and since then, no more beep! Still don't know what any of this was about, but I'll count my blessings and keep my fingers crossed. Hope it works for jennasis and others. I guess I'll mark this solved.

---

### Post by Javelin Dan on 2012-08-14
To paraphrase Elton John…”The Beep, the Beep, the Beep is Back”. I spoke too soon. After 3-days of blissful silence, the beep came back with absolutely no input from me. I think this box is haunted…

---

