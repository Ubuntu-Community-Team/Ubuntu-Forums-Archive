---
title: "Upgrade to 11.10 stuck..."
date: 2012-01-14
forum: New to Ubuntu
---

### Post by 2CV67 on 2012-01-14
Every Ubuntu upgrade brings its new miseries, but this time I can't even complete the job & suspect I am going to lose everything.
Upgrading from 11.04 to 11.10 was going OK until I got a warning about "File system root" having only 238M space left.
One option was "Investigate" which I accepted.
That opened disk analyzer which took a long time to complete & stayed with only gray border so I could not move it from in front of the Upgrade screen!

I went away to eat & came back to find a new pop-up screen asking me if I wanted to replace '/etc/cups/cupsd.conf' or not.
This screen also lacks a header which would allow me to move it & it does not react to any mouse or keyboard input.

So now I am stuck in mid upgrade, with 2 inactive & unmovable screens in front of the Upgrade screen & apparently no way out.
Except maybe C/A/D or REISUB which I have not yet tried as I suppose that will leave me with no Ubuntu at all...

Any ideas?

---

### Post by TeoBigusGeekus on 2012-01-14
Post us the output of
```
df -h
```
and
```
cd /
du -h --max-depth=1 2>/dev/null
```

---

### Post by 2CV67 on 2012-01-16
Thanks for your suggestion, but I had already given up & used REISUO to escape.
After that, of course, everything was so screwed up that I wiped it away & made a clean install of 11.10 from a live USB.
Thankfully I had plenty of backups of all my stuff, so no disaster, but lots of work ahead to tidy things up...

I can't help brooding over the dismal performance of Ubuntu Upgrades.
Has anybody tried to get statistics of how many upgrades:
- go perfectly
- have minor problems
- have serious problems
- fail completely & irrecoverably
- cause people to abandon Ubuntu?

My own experience, since 6.10 has been very bad & I am no longer able to recommend Ubuntu to anybody else (except real geeks) because of this problem.

I wish developers would concentrate more on getting stuff working solidly & less on eye-candy...
Maybe I am in a minority?

---

### Post by mastablasta on 2012-01-16
> **2CV67 said:**
> Maybe I am in a minority?
 
yes maybe you are :-)
 
anyway for an update to go well you need a vanilla Ubuntu. No PPA's, no proprietary drivers, no pimping of the OS etc. as soon as you deviate from the standard/default things can go wrong. problme is plenty users do need to deviate from default.
 
i never could understand why Ubuntu during upgrade simply doesn't overwrite the graphics driver files or remove them by itself before doing the upgrade. same they could automaticly disable PPA for safe upgrade.
 
in your case it seems you created separate root and home and ran out of space on root (by default, the home is not separated). and yes cups cfg should probably be replaced by new config file in this case.
 
i need to make it from 10.10->11.04->11.10->12.04  in April... wish me luck.
 
i plan to disable all the PPA's and then do the upgrade and then enable the PPA's again if necessary. we'll see how it goes. thoguh likely it will be clean install in he end. quite stupid...

---

### Post by mörgæs on 2012-01-16
> **2CV67 said:**
> I am no longer able to recommend Ubuntu to anybody else (except real geeks) because of this problem.


I am recommending Buntu to everyone who cares to listen (and a few who don't), and I always instruct them to do only fresh installs. Have convinced a good number of people.

The upgrade is for a real geek - a fresh install is for everyone.

---

