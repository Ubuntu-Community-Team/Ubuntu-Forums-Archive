---
title: "Subwoofer Too Loud!"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by Little Bacon on 2012-06-16
I have a Dell XPS 15 (L502x) with a JBL speaker system in it which originally ran with WAVES MAXXaudio3 on Windows 7. I split my hard drive and installed Ubuntu on the new partition.

Now when I run Ubuntu, my subwoofer is far too loud and makes a terrible grinding noise at 70-75% volume and what seems to be no way to turn down the sub at all.

I know my sub is not blown, it just needs to be turned down or if it comes down to it, cut off completely. I can't listen to anything loud enough to hear it without a loud-*** "BZZZZZZZ..." coming from under my PC

Dell.com does not have drivers for Ubuntu and I cannot for the life of me find a MAXXaudio3 driver or any way to fix the sound. So I've pretty much given up on finding a sound driver to help me, but maybe there is some kind of stand-alone equalizer that will stay in the background and let me sub down?

---

### Post by MG&amp;TL on 2012-06-16
If you've tried the normal sound settings dialog, you could try this command:

```
alsamixer
```

which gives you fine control over output devices.

---

### Post by ajgreeny on 2012-06-16
There are various equalisers available, either within the music player applications, or I think also as a system wide utility.  However you may find that running alsamixer in terminal and playing with the PCM channel may help you considerably.

Even on my simple sound setup with small logitech speakers and woofer I can not push the PCM volume up above where it is shown in the screenshot, around 80%, or I also get distortion.  I can push the master volume all the way to 100% with that lower PCM value and still get plenty of volume, but no distortion.

---

### Post by TheGuyWithTheFace on 2012-06-16
Have you tried the basic Ubuntu sound settings dialog? Click the speaker in the top right corner, click on sound settings, and you should have a subwoofer slider on the right...

---

### Post by Futant on 2012-06-17
Are you sure the sub is not blown? I have the same laptop and have not experienced this problem... not very helpful I know, sorry.

---

### Post by Futant on 2012-06-17
Forgot to mention - one thing I have experienced with mine (and so have many others online) is the speakers crackling/buzzing/generally sounding terrible when there is a phone connected to the internet nearby. When mine first started having the problem I was really worried, sounded like the speakers had blown, only way I could tell it wasn't that was sometimes it would be one speaker with the problem and sometimes it woud be the other, then sometimes the sub. Try banning smartphones from the house?

---

### Post by audiomick on 2012-06-17
> **Futant said:**
>  crackling/buzzing/generally sounding terrible when there is a phone connected to the internet nearby

Any phone may cause interference, not just one connected to the internet. The phone is a radio transmitter, and if the computer, or any audio device for that matter, is not well shielded, you are likely to get the characteristic noise that a phone makes when it transmits.

---

### Post by Futant on 2012-06-17
That is true, but there is a definite issue with sound interference from internet phones, seperate from the usual phone noise. Don't know which computers it affects apart from this model.

---

### Post by audiomick on 2012-06-17
> **Futant said:**
> That is true, but there is a definite issue with sound interference from internet phones, seperate from the usual phone noise. Don't know which computers it affects apart from this model.
They sound different depending on what function they are using. Blackberries sound really awful, for instance. You can safely assume it affects all computers. ;)

---

### Post by Enigmapond on 2012-06-17
The 8th comment here:
[http://ubuntuforums.org/showthread.php?p=12007044#post12007044](http://ubuntuforums.org/showthread.php?p=12007044#post12007044)

Has a deb attached for the oneiric version of the system-wide EQ. This works very well in 12.04. I use it a lot and it will definitely solve your issue.

Cheers!

---

### Post by Little Bacon on 2012-06-20
Enigmapond, BEAUTIFUL!
You, sir, have saved my subwoofer.

All other posts were appreciated though.
Except the one asking if my sub was blown, I'm sure we covered that in the initial post.

I also had to calm down the electronics in my room, but it's pretty perfect now.

---

### Post by alokmahor on 2013-04-20
I have same laptop and facing same problem of too loud woofer 
i have installed pulseaudeio equalizer on ubuntu 12.10
but still woofer's sounds is very loud. how did you solve your problem?

---

### Post by Nixarter on 2013-04-20
> **Futant said:**
> Are you sure the sub is not blown? I have the same laptop and have not experienced this problem... not very helpful I know, sorry.


This.  There is only one possibility for any sort of "scratching" sound coming from a subwoofer.  If there is no level adjustment on the subwoofer, I take it you are talking about a set of inexpensive miniature speakers that many use for computers.  If this is the case, dropping them often misaligns the speakers because the metal is very thin for the woofer baskets, causing the voice coil to scratch when moving.

So, yeah, volume adjustments wont make it better.  You will need to unhook the subwoofer or get a new set.

---

