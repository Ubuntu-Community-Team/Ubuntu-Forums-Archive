---
title: "Could use some quick help from audio experts."
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Roasted on 2008-07-29
Added a PCI sound card.
Disabled onboard audio.
Works great!
But I have no sound on YouTube or Ubuntu log in/out sounds...
I'm using Alsa. Everything under sys-pref-sounds is set to Alsa.
Ubuntu Hardy Heron 64 bit.

Any ideas?

---

### Post by iaculallad on 2008-07-29
Try to install the support audio wrapper if it works:

```
sudo apt-get install libflashsupport
```

---

### Post by Roasted on 2008-07-29
Didn't work.

Also, half the time when I reboot my computer, I have zero sound. The other half, I have sound with mp3s and such. I can tell this by whether or not I hear the two drums prior to logging in at the main screen. If I hear the two drum beats, that means I will be able to play mp3s. If I don't, I have zero sound. Period.

It's pretty much 50 50. What the hell? How can I fix this? Should I just return the card to newegg and pick up the Turtle Beach Riviera, that supposedly works 100% out of box?

---

### Post by cariboo on 2008-07-29
Have a look at this:

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

It should help you with your sound problems.

Jim

---

### Post by Roasted on 2008-07-29
Pulse Audio... are you kidding me? I tried installing that with my onboard card. Needless to say, after thoroughly following that guide, a fresh install was needed.

What makes you think that guide will fix my issues? My sound works half the time. When I tried out YouTube and it didn't work, it was after a fresh boot, so I know Amarok wasn't tying up the audio pipe. What benefits would Pulse give me in this situation, given those circumstances? 

I'm half tempted to return the card and grab another. :(

---

### Post by Roasted on 2008-07-30
So I was doing some research on other cards just to have a backup plan and I came across something...

I was looking at a Turtle Beach Montego card for a few bucks more, but had the same specs as the SIIG. I noticed the chipset... Granted, I had to google some archived forums, but they had the SIIG and the Montego listed as having the same chipset... CMI8768.

Can anybody confirm this? Do these two cards have the same chipset?

I heard the Montego was working perfectly in Linux. If that card works, shouldn't my SIIG be easy to get working too since it has the same chipset? 

(again, this is just what I found on archived web sites... not sure how accurate they are. But they seemed to be decent resources.)

---

### Post by Roasted on 2008-07-30
Would this help at all?

[http://www.alsa-project.org/main/index.php/Matrix:Module-cmipci#Introduction_for_C-Media_CMI8x38_.28PCI.29_soundcard](http://www.alsa-project.org/main/index.php/Matrix:Module-cmipci#Introduction_for_C-Media_CMI8x38_.28PCI.29_soundcard)

I just can't seem to find any viable answers for this, and it's driving me absolutely insane. I don't understand why I would need to recompile all of that garbage when it specifically said all I would need is to locate a driver... Annnnd I been googling for a half hour with no light at the end of the tunnel. 

I just don't get it. People with the TB Montego are saying it works perfectly. Yet I can't find any documentation on this SIIG. Yet, both cards have the same chipset... so shouldn't it work like the Montego???? 

:(

---

### Post by Roasted on 2008-07-31
All right, I'm done messing with the SIIG. I found no information on it regarding Linux usage whatsoever. I'm returning it.

Now, I am comparing two other cards.

Turtle Beach Riviera 5.1 24bit 48khz - 29 dollars
and
Turtle Beach Montego 7.1 24bit 96khz - 52 dollars

The 7.1 means nothing to me for what I'll be using as my speaker setup, so it's not really an added feature in my eyes. But what I do question is the sample rate. Would 96khz make a noticeable difference from 48khz? Or would 48khz be plenty sufficient?

---

### Post by Roasted on 2008-08-01
All right. Done deal. The SIIG has been returned. I'm going to order the Turtle Beach Montego 7.1.

The Montego has a CMedia 8768 chipset, a chipset that is supported by Alsa. K, great news to me.

Thing is, I'm pretty sure the SIIG had the same chipset. And yeah, the SIIG did work... half the time. 

If the chipset that the card had was indeed the CMedia 8768 which is fully supported by Alsa, then why in the world was it acting the way it was in terms of only kicking on about half of the time? I may have returned the card, but I want to know what went wrong.

Also - The Montego is DDL. Is that supported in Ubuntu?

---

### Post by Roasted on 2008-08-03
Here again, hoping maybe today I get some answers.

When I went back to my onboard card, certain system sounds don't work. Such as the login sound or the sound you get from k3b when you're finished burning a CD. 

What's the deal? Did I mess something up?

---

### Post by bobnutfield on 2008-08-03
I cannot tell you for sure that it will work, but others with similar sound problems have restored their sound with the following command, first making sure that your device is listed correctly in System>Preferences>Sound:

> sudo /etc/init.d/alsa reset

---

### Post by Roasted on 2008-08-03
> **bobnutfield said:**
> I cannot tell you for sure that it will work, but others with similar sound problems have restored their sound with the following command, first making sure that your device is listed correctly in System>Preferences>Sound:

"Command not found."

I tried altering that command, since I use a similar command to start/stop samba...

I tried reset alsa, alsa reset, restart alsa, alsa restart. Nadda worked.

---

### Post by bobnutfield on 2008-08-03
Sorry, works on my system.  You could try it with:

> sudo /etc/init.d/alsa-utils reset

---

### Post by Roasted on 2008-08-03
That command worked, however, it didn't solve the problem at hand.

---

### Post by bobnutfield on 2008-08-03
Yes, I apologize for my first post as I had sometime in the past created an alias for alsa-utils to alsa.  Sorry it didn't solve your problem.

---

### Post by Roasted on 2008-08-03
I think I'm going to make a new thread since I kind of swayed the topic that I originally intended for... that way if I end up finding a solution to it, the thread is properly labeled for search reasons in the future. 

Thanks for your help! 

Montego coming tomorrow... hoping it'll work OOB and kick some *** on my stereo setup. :guitar::guitar::guitar::guitar::guitar:

---

