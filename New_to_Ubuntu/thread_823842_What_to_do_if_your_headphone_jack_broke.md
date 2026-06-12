---
title: "What to do if your headphone jack broke?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Valir on 2008-06-09
Hi there, 

This might be useful for somebody. I am using Ubuntu Hardy (Studio kernel).

I managed to break my headphone jack plug (on my ACER laptop), so I couldn't use my headphones.

1. My first option was to buy USB headphones. NOT A GOOD OPTION!!! 

I managed to get it to work by System>Preferences>Sound (after having added it in system>Administration>Services), by marking USB sound in every dropdown list.

The PROBLEM: Sound streams out of your headphones perfectly unless you are using Firefox. When you try to enjoy any media in your browser, be it flash or what have you, either there is NO SOUND at all or sound comes out of your speaker but not your headphones.

The SOLUTION: I did not find it. I messed around with a lot of things, looked around the forums, reconfigured everything, uninstalled and reinstalled all sound and media properties of ubuntu, to no avail. Worse, by tinkering around with the sound - switching from USB to Alsa to PulseAudio - the result was erratic behavior. It worked switching from the headset to the speakers, but not back, and other strange things. 

THIS might be an internal problem with Firefox, so I gave it up.

2. My second option was to use the line jack as a headphone out.

Good fortune. By tinkering around I stumbled on a simple solution: ALSAMIXER. If you a have Line jack beside your mic jack and headphone jack you can use that. 

Go to a terminal and type:

```
alsamixer
```

There you can move to the line jack column and change it to headphones, plug your headphones in the line jack, and bingo!

Tip: Sound is still coming out of your speaker with you headphone plugged in, because the line jack does not detect like your headphone jack whether you are using headphones. YOU CAN TURN the speaker sound off by going to the headphone column in ALSAMIXER and change it to Line in. 

You can later on add to your panel a volumecontrol. Open volumecontrol, go to options, and switch the headphone jack mode, if you want sound out of your speakers. 


This will work until you break your line jack as well! :D

best,

---

### Post by y-lee on 2008-06-09
That is pretty Cool :)

Thanks for sharing, it was a good read too :KS

---

### Post by NuSuey on 2008-07-07
This is EXACTLY what i need.

But i cannot change the line in to the headphone out..

Could someone give me a little help with it? 

That would help me a LOT.

Thanks in advance.

---

### Post by RequinB4 on 2008-07-07
This sounds exactly what I want to do since my headphone port stopped playing nice, but forgive a hardware noob -- which port is the line in?  I have one that has a microphone picture and one that has an arrow to a musical note.

Also, if you could edit the first post with a more user-freindly step-by-step I'm sure MANY will be appreciative.

Thanks, RequinB4

---

### Post by NuSuey on 2008-07-07
can anybody help with this?

---

### Post by RequinB4 on 2008-07-08
This is my last bump -- after a day or so I'm just going to post a question with my problem.  Help would help out a LOT!

---

### Post by NuSuey on 2008-07-11
So anybody?

---

### Post by Valir on 2008-10-28
I thought I had described this in my above post, but it might be different with your soundcard.

I have alsamixer. The best way to do this is to add the volume control (alsamixer) on the toolbar, by right clicking and adding and selecting volume control. Go to configuration and check the box for line jack mode and headphone jack mode. Then you can go to options and drop select for headphone jack mode "line in" - this will silence the speakers. And drop select "headphone out" for line jack mode - then you can plug in your headphone in the line in. 

The line in symbol is usually an arrow pointed into a wave circle. 

Hope this works.

---

### Post by Crafty Kisses on 2008-10-28
Very clever, nice one. :)

---

