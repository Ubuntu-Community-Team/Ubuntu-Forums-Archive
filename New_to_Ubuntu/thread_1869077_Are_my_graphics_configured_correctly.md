---
title: "Are my graphics configured correctly?"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by cozumel on 2011-10-25
Hi,

I've installed Ironhide for my NVidia 540M (Optimus) card using the following script:

```
$ sudo apt-add-repository ppa:mj-casalogic/ironhide
$ sudo apt-get update && sudo apt-get install ironhide
```

Everything seems to be good.  But I am a bit of a noob and would like to know how to check if it working okay?  What do I need to do to test please?  I seem to be comparable (to Win7) battery life when watching DVDs.  How do I know if the Intel & NVidia cards are switching correctly please?

Thanks in advance

---

### Post by thatguruguy on 2011-10-25
If everything is working OK, then you are configured correctly.

---

### Post by Drowz0r on 2011-10-25
> **thatguruguy said:**
> If everything is working OK, then you are configured correctly.
 
Are you sure? My GFX card seemed to be working fine and the drivers correct until I tried doing dual screen and I fouund that I had the wrong drivers.
 
What kind of graphics card do you have?
 
If Nvidia, find the Nvidia app thing in ubuntu, I think typing "nv" will be enough of a filter to bring the nvidia graphics card stuff up. If you have all the options there then that's a good indication that you're drivers are correct.
 
Try the additional drivers app too, I search "drivers" and it's the only app there. I find that although with older drivers everything seems fine - gradually you find certain things load slow etc... Maybe run it through it's paces and try some games/online stuff.

---

### Post by Drowz0r on 2011-10-25
This thread might help ya [http://ubuntuforums.org/showthread.php?t=1867948](http://ubuntuforums.org/showthread.php?t=1867948)

---

### Post by cozumel on 2011-10-25
So, you guys are saying the only way to test if Optimus is functioning correctly, using Ironhide, is to play DVDs and games etc on battery power???  Is there not a recommended test, routine or procedure for testing that confirms everything is good?  Just that it seems a bit vague, kind of hit and miss...

Thanks again.

Should add that the system ghas been running well since I installed Ironhide about three days ago.  No glitches, freezes or crashes...

---

### Post by Drowz0r on 2011-10-25
> **cozumel said:**
> So, you guys are saying the only way to test if Optimus is functioning correctly, using Ironhide, is to play DVDs and games etc on battery power??? Is there not a recommended test, routine or procedure for testing that confirms everything is good? Just that it seems a bit vague, kind of hit and miss...
 
Thanks again.
 
Should add that the system ghas been running well since I installed Ironhide about three days ago. No glitches, freezes or crashes...
 
I don't know of any offical way - I've only really been using ubuntu for a few days but from an over all performance perspective, perhaps running some kind of benchmarking software. You could just try a benchmark test for a high end game to see how your machine reacts. If it's poor performance your running on the intel chip, if performance is high you're running off the dedicated card. If you get poor results while running a game, then clearly only the intel chip is working. Try opening a game and seeing what options you have available - usually they're reduced if your on the lesser "graphics card".

If the results are good, then the higher end card is working. So I guess you would just need a method of finding out if the lower card was kicking in when you wanted it to...

---

