---
title: "[SOLVED] No sound upon fresh install--already seen similar forums"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by fiddler616 on 2008-07-15
Hello,
I just installed Ubuntu on my laptop 3 weeks ago (!), and so far like it a lot. Except that there's no sound, whatosever.
I've already seen [http://ubuntuforums.org/showthread.php?t=858943&highlight=sound](http://ubuntuforums.org/showthread.php?t=858943&highlight=sound) and [http://ubuntuforums.org/showthread.php?t=859004&highlight=sound](http://ubuntuforums.org/showthread.php?t=859004&highlight=sound) and both didn't help. I've also played games with ALSA, but I really can't figure out exactly how to use it (thus Absolute Beginner Talk, not regular forums), since I couldn't find my sound card in there. On that--I'm not precisely sure how to check what sound card I have (second hand computer), but I did go into the device manager in Windows, and it told me:
"SoundMAX  Integrated Digital Audio" and then
PCI bus 0, device 31, functions...etc.
I'm assuming that's it. I also feel like I saw something about Intel somewhere (Hmm, I thought they made processors. There goes my lack of knowledge).

And I feel like an idiot starting a new thread when it (seems to be) a fairly common problem, but I really don't know what else to try.

---

### Post by philinux on 2008-07-15
The command lspci in a terminal will confirm your card.

Also try >system>prefs>sound.

Try changing to alsa from auto detect and hit the test button, see if that works.

Try Pulse audio too.

---

### Post by bobnutfield on 2008-07-15
That card used the Module:snd-intel 8x0 module.  Do:

> sudo lsmod

Look for that module in the listing in the sound section.  If it is not there, post back

---

### Post by fiddler616 on 2008-07-17
> The command lspci in a terminal will confirm your card.
Did that and got this in the relevant part:
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

```
> 
Also try >system>prefs>sound.

Try changing to alsa from auto detect and hit the test button, see if that works.
That didn't do anything noticeable.
> Try Pulse audio too.
Forgive my ignorance--is that a program/package, or something I'm supposed to see in /Preferences/Sound, or the Terminal, or something completely new? I'm sorry...
**On modules:**
I found it, it looks like this (don't know if the other numbers help):
```
snd_intel8x0           35356  3 

```(Name | Size | Used by)

I'll be happy with sound that just works, but I have two little volume buttons next to the screen on my laptop (Sony Vaio), which don't don't seem to be recognized, and are sorta handy. I'm cool with just using the Volume Control in the Taskbar though, no biggie.

---

### Post by fiddler616 on 2008-08-09
It'd be fantastic if someone else would reply, I'd really appreciate it...

---

### Post by Nevyn on 2008-08-09
I don't think I'm much better than you at this, but PulseAudio and ALSA are two different ways that Linux handles sound. ALSA is the old one and PulseAUdio is the new one; presumably better but with many reported issues.

Where you changed to ALSA (in System -> Preferences -> Sound Preferences) Did you change all of the drop-down menus? Did nothing happen when you pressed the "Test"-button on any of them?
If no, you should be able to change the drop-down menus to PulseAudio. Do that and repeat the test-button-pressing. Did anything make a sound? 

If you can't find the PulseAudio option in the menus please write it here.
Don't forget to plug in your speakers and turn up the volume ;)

---

### Post by fiddler616 on 2008-08-10
I tried it with both ALSA and PulseAudio, and none of the "tests" worked.
As for speakers, I'm using a laptop, so I hope they're on! :)

---

### Post by kwacka on 2008-08-10
Firm believer in the KISS principle.

For some reason Ubuntu configures sound for 'external amplifier' (on laptops at least)

Right-click on the speaker in the panel, select 'open Volume Control'.

Select Edit -->  Preferences, now put a tick in the box for 'external amplifier'

Click 'Close' & click on 'switches'; make sure the 'external amplifier' is NOT ticked.

Come back if still no sound.

---

### Post by fiddler616 on 2008-08-11
> **kwacka said:**
> Firm believer in the KISS principle.

For some reason Ubuntu configures sound for 'external amplifier' (on laptops at least)

Right-click on the speaker in the panel, select 'open Volume Control'.

Select Edit -->  Preferences, now put a tick in the box for 'external amplifier'

Click 'Close' & click on 'switches'; make sure the 'external amplifier' is NOT ticked.

Come back if still no sound.
I opened the Volume Control, got two slidey things labelled "Master", went to Edit-Preferences, and got:
___________________________
Select Tracks to be Visible
---------------------------
[x] Master                 
---------------------------
                [X Close]  
There was no external amplifier, anywhere...

---

### Post by Novus on 2008-08-11
sounds like u'r using the wrong mixer, in the volume contol click file > change device. I donno which one you should use but im sure u can try all untill you find the external amplifier switch :)> **fiddler616 said:**
> I opened the Volume Control, got two slidey things labelled "Master", went to Edit-Preferences, and got:
___________________________
Select Tracks to be Visible
---------------------------
[x] Master                 
---------------------------
                [X Close]  
There was no external amplifier, anywhere...

---

### Post by fiddler616 on 2008-08-11
Good call, I got the "external amplifier" box on one of the devices "Intel string-of-characters (ALSA mixer)", so I went into system-prefs-sound, tried all the playback options, and none of them worked. Darn.

---

### Post by fiddler616 on 2008-08-14
Anyone...please?

---

### Post by TheMaxzilla on 2008-08-14
This already happened to me, but when I went from 7.10 to 8.04, I had sound. :)

If nothing works: wait for Ibex.

---

### Post by fiddler616 on 2008-08-14
Haha, thanks :)
...Certain OS makers who's name rhymes with Licrosoft need to take notes on fixed release cycles...

---

### Post by fiddler616 on 2008-08-15
Novus and kwacka seem to have gotten it after all--once I rebooted I got a nifty little log-in-screen noise, a rather overdone logging-in sound, and all of the System-Preferences-Sound tests work!
Moral of the story for people reading this later: if you do something cool, REBOOT! :)

---

### Post by fiddler616 on 2008-08-25
Haha, thanks x2.
I screwed up my boot order with PuppyLinux, and decided the easiest thing to do was copy my documents onto a USB drive and do a fresh install...and I completely forgot how to get the sound working until I read this again.

---

