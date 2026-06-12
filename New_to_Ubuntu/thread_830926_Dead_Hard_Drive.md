---
title: "Dead Hard Drive?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Trzone on 2008-06-16
My friend recently gave me a hard drive, i plugged it in and it powered up, ubuntu detected it and it worked fine.  Then, as i was plugging it into my other computer, i saw a bright flash near the power place of the hard drive and suddenly, everything turned off, so i unplugged that computer from the wall and tried again.  Unfortunately, it wont turn on in any computer that I have.  Does this mean it's dead or is there anything i can do to fix this?  It has nothing that i need on it, but i'd like some extra space.  Any input would be greatly appreciated!

Sorry if this isnt a ubuntu specific question

---

### Post by ukripper on 2008-06-16
> **Trzone said:**
> My friend recently gave me a hard drive, i plugged it in and it powered up, ubuntu detected it and it worked fine.  Then, as i was plugging it into my other computer, i saw a bright flash near the power place of the hard drive and suddenly, everything turned off, so i unplugged that computer from the wall and tried again.  Unfortunately, it wont turn on in any computer that I have.  Does this mean it's dead or is there anything i can do to fix this?  It has nothing that i need on it, but i'd like some extra space.  Any input would be greatly appreciated!

Sorry if this isnt a ubuntu specific question

boot into ubuntu live cd and run follwoing in terminal:
```
sudo fsck
```

this will check your hardrive for any bad sectors on file system and may fix it or block it from accessing while you use ubuntu.

---

### Post by bobnutfield on 2008-06-16
I am afraid that what you are describing is short at the power connection and the liklihood is that the connectors are fried.  I would not advise plugging into your motherboard as it could short the power supply connector to your mother board, and that is real trouble.  You might take it to a computer shop and have them test it.

Bob

---

### Post by Trzone on 2008-06-16
Well, the same connection that i'm plugging into works for my other hard drive on both computers.  So it must be the dead hard drive? I call it dead because it does not power up at all.

---

### Post by ukripper on 2008-06-16
> **Trzone said:**
> Well, the same connection that i'm plugging into works for my other hard drive on both computers.  So it must be the dead hard drive? I call it dead because it does not power up at all.

Can you boot into live cd and in terminal do following:
```
sudo fdisk -l 
``` it is 'ell' not 1
and lets see if it is detected or not.

---

### Post by bobnutfield on 2008-06-16
That is what I was referring to, the power connector on the hard drive, not your computer.  I had a similar experience with a bad component and continued attempts to get it working resulted in shorting out my power supply which damaged the motherboard.  I am not saying that this is definitely going to happen, but if the hard drive connector has shorted out, it COULD damage your power supply.

---

### Post by sleepingdragon on 2008-06-16
"Flash and bang" hard drive... been there, done that. As you may have read from the other posts, connecting it into a healthy PC might not be the best idea. Sorry, but it's probably best to scrap that drive. You seriously run the risk of frying everything else. If you have a serious need to recover data from that drive, take it to a pro and hope they don't charge the earth to recover.

I don't want to be the bearer of bad news, but don't risk borking your entire PC because of it.

---

### Post by Trzone on 2008-06-16
With my luck, if i try it again in 6 months it'll work :lolflag:  but I believe you're right, although i don't think it'll short anything out, but i think the hard drive just kinda got screwed over.. oh well heh

---

