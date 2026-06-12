---
title: "SB Live! 24 bit, 2 speakers work"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by polotip on 2008-04-23
So there are other posts about this, but ive never used linux before so i dont know how to install drivers or really do anything...  So, if anyone can help it would be great, but I need all the commands to put in the terminal since I dont know what to put.  HELP!!!
Thanks everyone,
Brian

---

### Post by polotip on 2008-04-24
I guess I should add that I have logitech 5.1 speakers...  Also,  Any way to get logitech quickcam deluxe for notebooks to work.  The sound works, but not the video?!?!?!

---

### Post by yaknowwat on 2008-04-24
The speakers aren't going to be the issue. (unless their broken)

Getting sound depends on 2 factors:
Your SoundCard Intergrated or seperate and if it has supporting drivers.
Also make sure the sound manager is set to put sound out of everything.

Double click the volume control Icon
This will load the volume manager

There is File > Change Device
(thats for making sure you are setting it to the correct volume control device.)
Then Edit > Preferences 
(to make sure you have all controllable volume managers open for use.)

You can control the volume from the sliders.

Make sure 
PCM, Front, Surround, Center, LFE, Side, PC Speakers

are all maxed up so that you can use them.

Master is controlled via the sound control icon in the toolbar unless you have pulseaudio installed then its controlled in a seperate master control.

---

### Post by polotip on 2008-04-24
Everythings is all the way up, which device should it be on?  I have everything checked off and al the way up, i think i need to install a new driver for the SB Live! 24 bit soundcard, but dont know how or where to get it...

---

### Post by FuturePilot on 2008-04-24
What version of Ubuntu are you using? This may be related to PulseAudio

---

### Post by jaytek13 on 2008-04-24
> **FuturePilot said:**
> What version of Ubuntu are you using? This may be related to PulseAudio

Yes. It has been well discussed on the development forums that pulseaudio has fubard things pretty well for a lot of people, with one of the issues being surround sound speakers. 

Kind of disappointing that they would release it like that, and even more disappointing that a new user using Ubuntu for the first time is going to be turned off from Linux probably for a long time for that very reason.

---

### Post by FuturePilot on 2008-04-24
I found this, worth a shot. Afterwards make sure you logout and log back in.
[http://ubuntuforums.org/showpost.php?p=4751258&postcount=11]("http://ubuntuforums.org/showpost.php?p=4751258&postcount=11")
```
gksudo gedit /etc/pulse/daemon.conf
```
Remove the # from the line that says
```
default-sample-channels
```
and save it.
Go System&#8594;Preferences&#8594;Sound and set everything to output through PulseAudio.

---

### Post by polotip on 2008-04-24
Well, I put the first command into the terminal and it opened up daemon.conf in gedit, but it was just a blank page :(.  As for jaytek13's comment about me being turned off, im fine for now.  2 speakers work, and linux is way freakin faster than windows, and i've heard it stays this way, whereas windows begins to lag over time.  Im still concerned about my webcam problem too though, even though I can just use it on my laptop, which is still running windows at a reasonable rate, I would love to be able to use it with linux!  As for the daemon.conf file, what should I do about it being blank?  Keep helping, I appreciate it greatly...
Brian

---

### Post by polotip on 2008-04-24
Also, Im running Ubuntu 7.10 i think, whatever was before the version just released today...  Should I try updating to the newest version?

---

### Post by jaytek13 on 2008-04-24
As far as the webcam, it depends on what you're looking to do with it. If you intend to use it for MSN messenger or Yahoo messenger, than the program Kopete supports cams. 

If you're using the previous distro that wasn't released today, being 7.10, then it's not pulseaudio. The problem may be that you are expecting things that aren't surround sound to come out as surround sound to your speakers? Like, the default for Windows is that it will emulate stereo sound to the 5 or 7 speakers even though they aren't actually being used by the audio in question. There is a certain way to do this in Ubuntu. I'll have to look around for the post on these forums, or if someone else knows it off hand..

---

### Post by crjackson on 2008-04-24
> **polotip said:**
> Also, Im running Ubuntu 7.10 i think, whatever was before the version just released today...  Should I try updating to the newest version?

I have an SB Live! 24 and it uses all speakers correctly.  Be sure you enable ALL your repositories, get ALL updates, and go back to the sound manager and double check your settings afterwards.

Ubuntu latches on to the wrong volume control / device by default.  You have to monkey around to make sure all volume controls for your device and enabled and unmuted.  It works great for me.  Heck, it even worked in 7.04 but 7.10 has better sound.  7.04 tended to overdrive the output levels.

---

### Post by Bentai on 2008-04-25
> **FuturePilot said:**
> I found this, worth a shot. Afterwards make sure you logout and log back in.
[http://ubuntuforums.org/showpost.php?p=4751258&postcount=11]("http://ubuntuforums.org/showpost.php?p=4751258&postcount=11")
```
gksudo gedit /etc/pulse/daemon.conf
```
Remove the # from the line that says
```
default-sample-channels
```
and save it.
Go System&#8594;Preferences&#8594;Sound and set everything to output through PulseAudio.
I 100% vouch for this fix. I had a 2 speaker issue on my SB Live! Value (ooold PCI card). Has 4.1 output. I edited "default-sample-channels" from 2 to 4. Saved, restarted and I have proper output now. Make sure you typed the ```
gksudo gedit /etc/pulse/daemon.conf
``` command correctly.

---

### Post by polotip on 2008-04-26
So, when i updates to the new version of ubuntu, the daemon.conf file came back, so that was a positive.  On the other hand, i tried both getting rid of the default-sample-chanells and changing it from 2 to 5, but niether case worked...  I might be kinda over it, unless someone has a last ditch effort...
Thanks again,
brian

---

