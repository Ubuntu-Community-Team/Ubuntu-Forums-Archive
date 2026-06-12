---
title: "headphones not working"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by thegraduate on 2008-07-18
im on a fujitsu series a laptop and i installed ubuntu a couple hours ago and no matter what i try or do i cant seem to get my sound working other than the laptop speakers. i used the pulse audio thing and used the "test" buttons and when i do that it works with my headphones but when i just play music it keeps playing through laptop speakers even when my headphones are plugged in. what am i suppose to do?

---

### Post by SunnyRabbiera on 2008-07-18
Well there is a audio adjuster in ubuntu, it looks like a little speaker in the top right of your screen and right click it and open volume control...
also make sure the volume is turned up on the knob on front of the computer ;D

---

### Post by thegraduate on 2008-07-18
its not that the sound isnt working. the sound is working fine but the problem is this.

my head phones are plugged in
sound comes out of my laptop speakers instead of the headphones i have on.
the headphone inputs arent working...

---

### Post by |{urse on 2008-07-18
Then your headphones are broken or your audio jack is ruined.

---

### Post by thegraduate on 2008-07-18
my audio jack isnt ruined. i know this cuz it was working perfectly fine on vista and fidora. and it worked for the sound tests when i first installed ubuntu then it stopped working for some odd reason.

---

### Post by |{urse on 2008-07-18
you mean fedora? I'm not saying you are lying, It's just very unlikely because the headphone jack simply bypasses and captures the signal running to the speakers on your laptop. If your speakers are working.. you get the idea?

---

### Post by thegraduate on 2008-07-18
i dual boot linux with vista. and i JUST check on vista if the headphones worked and they work fine. when im on ubuntu it just doesnt recognize anything i stick in the audio jack.

---

### Post by -kg- on 2008-11-02
Yes, and I'm having the exact same problem on my laptop.

I have been in electronics for over 40 years, have held an Amateur Radio license for most of those 40 years, was a Ground Radio Communications Equipment Repairman (304X4) in the Air Force, and I most certainly know how a normal headphone jack works.  I have wired many of them.

My computer experience:  I have been into computers since the DOS2.X days, when there was no Windows (or maybe there was...I still remember seeing Windows 1.0 on the software shelf and thinking, "Oh great...another DOS Shell."  I can't remember the "time-line" involved.)  I've used DOS extensively, and have been through every flavor of Windows since 3.0, along with side tracks into other OSes.

I have repaired (hardware) a number of the early computers, and have built my last three "White Box" desktops from the ground up (not ordered them built by a local shop...BUILT them with my own two hands).  I have written programs in Basic and Basica interpreters, Microsoft Quickbasic 4.5 compiler, and Borlands Turbo C++ and Turbo Pascal compilers (all for DOS, and that was a while back).

I currently maintain several computers (I guess you could say SysAdmin, except that they're P.C.s used by various friends and family members) running W98, W2KPro, XP, Vista, and most recently Ubuntu Linux.

Having established my credentials, this is a legitimate problem.  I have the same problem with my Toshiba Satellite A135-S4487 laptop.  I plug the headphones in under Vista and the speakers are cut off and the sound is routed through the headphones.

Under Ubuntu Linux, however, I plug the headphones in and the speakers are *not* cut off and there is no sound through the headphones.  I've booted back and forth between Vista and Linux several times and the results are always the same.

My thought is: Considering that I know the way headphone jacks normally work (you do know that there are headphone jacks (and ways to hook them up) that *do not* cut the speakers off.  Though these types of systems are rare, I have seen them.

I just recently heard of USB headphones.  I had never before heard of such a thing, but upon consideration figured that for these to work, sound signals would need to be routed through the USB hub for them to be available to the USB headphones.

Now if thegraduate and my laptops are set up to support USB headphones, then it is quite possible that the front panel headphone jacks (which are of course *not* for USB headphones) may be a D/A (digital to analog) conversion system from the USB signal to the analog headphones jack.

If this were so (and if Ubuntu doesn't support USB audio devices, or isn't natively set up to do so) then of course there would be no audio to the headphones and no control over internal speaker cutoff.

There is one other possibility I can see.  Laptops (too) often have proprietary circuitry, and this may be a case of a proprietary subsystem that, when installing Vista (or whatever OS) at the factory, the proprietary drivers for those subsystems are installed as well.

If this is the case, the only hope would be to write drivers for these subsystems, or beg the company for drivers ported to Linux.  I'd be most interested to hear the views of those with more knowledge than I (I'm just beginning with Linux...I recognize that I'm a newbie in that area).

---

### Post by couloir007 on 2008-11-06
I just upgraded from 8.04 to 8.1, and my headphones stopped working. I know they are fine, so something is wrong.

---

### Post by billgoldberg on 2008-11-06
I would say change the sound to ALSA and install gnome-alsamixer.

Open gnome-alsamixer and look if they headphone jacks box is tagged.

Or if anything is muted.

---

### Post by LindaLou on 2008-11-24
Just jumping in here as this topic is related to my current predicament which is the microphone on my headset is not working.  Worked fine until yesterday but. I use both Ekiga and Wengophone for phone calls to land lines and cellulars.  I have not changed any of the settings as they were working just fine until yesterday.  I borrowed a functioning headset (the fellow uses it for chat on his PC with Windows OP) and was still able to hear the person that I phoned, but they could not hear me.  I have tried several different numbers in several different countries to no avail.  If the audio jack is ruined, what is the resolve?

---

### Post by -kg- on 2008-11-29
I recently got a reply to one of my messages on the same problem which fixed the problem very nicely.  All it involved was adding a line into an ALSA configuration file.  My headphones now work with no problem.

See [[COLOR="Blue"]_my question_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6115891#post6115891") for what worked on my computer.  It may be different for yours, but it can't hurt to try.  I have asked my original poster to try and find the site that he found this information on.  If this doesn't work for you, it might be that that site would have the answer for your laptop.

---

### Post by LindaLou on 2008-12-01
Thanks for the info.  I will certainly give this a go and post back.

---

