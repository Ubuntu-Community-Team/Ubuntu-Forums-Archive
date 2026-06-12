---
title: "Hi, my microphone doesn't work. It makes me sad."
date: 2011-09-16
forum: New to Ubuntu
---

### Post by EllieDragonfly on 2011-09-16
[COLOR=Magenta]I just installed Ubuntu 11.04 on my Acer Aspire One (AO751h) and my microphone doesn't work. I tried something I found on the net, but it didn't help. ([http://ubuntuforums.org/showthread.php?t=1477261](http://ubuntuforums.org/showthread.php?t=1477261)) 
I am very new to Ubuntu, so please explain every step (otherwise I won't get it). I tried skype test call, it didn't play back what I said.
Please help![/COLOR]
:KS[COLOR=Magenta]Thank you.[/COLOR]:KS

---

### Post by EllieDragonfly on 2011-09-16
If it helps, my video card is: 00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07).
I installed Ubuntu from USB. (Don't know if it will help.)

---

### Post by gandaran on 2011-09-16
> **EllieDragonfly said:**
> If it helps, my video card is: 00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07).
I installed Ubuntu from USB. (Don't know if it will help.)
the video card has nothing to do with sound:) just check that the microphone is enabled in sound preferences.

---

### Post by EllieDragonfly on 2011-09-16
Oh, lol. Yes I checked sound preferences. Should I post a screenshot? :confused: I don't know what to do.:(

---

### Post by EllieDragonfly on 2011-09-16
Is it right?

---

### Post by EllieDragonfly on 2011-09-16
When I try skype call testing service, all I hear is white noise. Nothing more.:(

---

### Post by kr0n1x on 2011-09-16
Try selecting different options in "Connector" (in the screenshot you've selected Analog Input, try a different one).
If it doesn't work, put it back to Analog Input and go to the "Hardware" tab. Here try selecting different hardware if available (I don't have ubuntu on at the moment, so I can't be more specific).

---

### Post by EllieDragonfly on 2011-09-16
Thank you. I will try it out and post my discoveries.:KS

---

### Post by EllieDragonfly on 2011-09-16
I tried it, but the sound didn't work. (so I don't know if the mic did work or not)
This is so annoying. :(

---

### Post by kr0n1x on 2011-09-16
Does the "Input Level" move when you talk? If yes, it means your microphone works, it receives your voice. In the screenshot it seems to work... maybe you only have to enavle the Microphone channel in the Output tab if you want to hear your voice (usually noone want this xD talking and hearing your own voice isn't cool!) :D

---

### Post by IWantFroyo on 2011-09-16
```
alsamixer
```

Type the above into the Terminal app. If your microphone was detected by Ubuntu, there should be a bar that says "Microphone" or something similar under it. It might also be "Input" (I'm running CentOS right now, so I can't check).

If nothing works, you might want to try an older version of Ubuntu (such as 10.04.3 [what I recommend to all new users]), or just be patient and wait for updates.

Ubuntu does this sometimes. When I was on 10.10, my mic didn't work for a week or so, and then worked perfectly after.

Have you fully updated your system?

---

### Post by EllieDragonfly on 2011-09-16
it doesnt move when I talk. :(
and where should I enable the mic?

---

### Post by IWantFroyo on 2011-09-16
Type:
```
alsamixer
```

There should be an "Input" or "Microphone" bar, which you should bring up to ~75% with the upwards arrow key.

Sorry, my first post was a little cryptic.

---

### Post by EllieDragonfly on 2011-09-16
> **IWantFroyo said:**
> ```
alsamixer
```Type the above into the Terminal app. If your microphone was detected by Ubuntu, there should be a bar that says "Microphone" or something similar under it. It might also be "Input" (I'm running CentOS right now, so I can't check).

If nothing works, you might want to try an older version of Ubuntu (such as 10.04.3 [what I recommend to all new users]), or just be patient and wait for updates.

Ubuntu does this sometimes. When I was on 10.10, my mic didn't work for a week or so, and then worked perfectly after.

Have you fully updated your system?
 Yes I fully updated my system.
But I don't want to change to 10.10.  I am happy my computer is working. I dare not touch it. Before it was unresponsive and it took me a lot of tome and effort to fix it. I can't risk that again.
but thank you.

---

### Post by IWantFroyo on 2011-09-16
Your Mic tab looks like it should be working perfectly.

Mic Boost doesn't always have very good results. You should probably turn that down. A lot.

Go into the Skype settings, go the the Sound tab (something like that- can't remember; haven't used Skype for forever). Make sure it isn't changing your mixer levels (there should be a checkbox- uncheck it).

In the Sound Preferences window, does it list Skype in the Applications tab?

---

### Post by EllieDragonfly on 2011-09-16
I turned mic boost down and unchecked the box, all i hear in skype test call is white noise. This is frustrating.

---

### Post by frncz on 2011-09-16
> **EllieDragonfly said:**
> I turned mic boost down and unchecked the box, all i hear in skype test call is white noise. This is frustrating.

I have a Acer Aspire One D255  running Natty. My microphone also does not work. An analogue headset microphone with a pink plug into the headphone socket works fine though, so I can Skype!Not ideal of course, but cheap and effective work around.
I hope this helps
mike

---

### Post by kr0n1x on 2011-09-16
> **EllieDragonfly said:**
> I turned mic boost down and unchecked the box, all i hear in skype test call is white noise. This is frustrating.

Those are the playback settings. As you can read in the header of that application (alsamixer), press F4 for the Capture settings and check if the microphone channel is enabled.

---

### Post by hreichgott on 2011-09-17
Check your speakers.
My Acer Aspire only has a left speaker, not a right speaker. If yours is the same, could be that Skype is playing sound back just fine, but the balance is all the way to the right or something.
Try listening for your played-back sound through a pair of plugged-in headphones.

---

