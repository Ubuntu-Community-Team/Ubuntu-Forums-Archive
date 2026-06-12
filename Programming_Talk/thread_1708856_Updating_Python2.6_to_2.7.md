---
title: "Updating Python2.6 to 2.7?"
date: 2011-03-17
forum: Programming Talk
---

### Post by anthonyvo on 2011-03-17
The last thing I wrote was in BASIC on an Apple IIe. Yeah.
Getting back into it and decided to learn Python.

I'm running Ubuntu10.10, 'already had Python2.6. I installed 2.7 and 3  (since everyone is telling me to jump into 3 since I'm born-again to coding I might as well know 3) along with their respective IDE's.

Now, I want to get rid of 2.6 (since I have 2.7), but there are things that are dependent on 2.6 that will be removed (per Synaptic Package Manager.) Some I don't care about losing, like alsa (only installed to mess w/ xsquawkbox,) but many I need - like gmountiso, brasero, digikam, dolphin, and mencoder to name a few.

My question - obviously there's no harm in having 2.6 and 2.7 on here, but do you think I'll be able to reinstall those mentioned with only 2.7 on here?

Or is there some PATH changes I need to make to let Ubuntu know that 2.7 is to be called for Python now instead of 2.6?

Confused newbie.
-Anthony

---

### Post by mjs2600 on 2011-03-17
I use Python 3 (python3) when I don't need a library that hasn't been ported yet. I've never really seen the need to pick one over the other. They are both same language, Python 3 just fixes a couple of things. Unless there is some feature that only 2.7 has that you know you'll need, I would use the default python. If you do need 2.7, just run python2.7. If you really want to switch the default python (I wouldn't), you can replace /usr/bin/python with a link to /usr/bin/python2.7.

---

### Post by robots.jpg on 2011-03-17
Agreed, there's really no reason to remove it. The different versions  of Python are completely separate, independent installations, so it's  not like they can interfere with one another.  Look at it this way -  Best case, you free 30MB on your hard drive and nothing else changes.   Worst case, you break a bunch of stuff.

---

### Post by anthonyvo on 2011-03-17
Thank you, both, for your input.
When you put it that way (worse vs best case,) I'd rather leave well enough alone then.

Thanks again!
-Anthony

---

