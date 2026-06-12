---
title: "How to excomunicate this intruder ?"
date: 2022-09-01
forum: New to Ubuntu
---

### Post by Innernet on 2022-09-01
Hello all
How to block forever the intrusion of this memory hungry **'isolated web co' **something ?'  and what does it ?

The system monitor shows it.  After killing; always comes back soon.

---

### Post by QIII on 2022-09-01
What release of Ubuntu are you using?  Do you use Firefox?

---

### Post by Innernet on 2022-09-01
Thanks.  Yes, Firefox on 22.04.

---

### Post by QIII on 2022-09-01
Does the hog calm down if you close Firefox?

Please have a read through [this]("https://hacks.mozilla.org/2021/05/introducing-firefox-new-site-isolation-security-architecture/").  You may be encountering the result of Mozilla's design decisions, but if it is sucking up a crazy amount of memory it may not be working as they intended.

Please let us know if anything there seems to fit.  This might be useful to others in the future.

---

### Post by Innernet on 2022-09-01
Will report when I find out as solid behavior.  From memory, it lingers in the 'System monitor' but will confirm later.   Am using 'Web' browser when Firefox gets clogged by apparently this 
isolated' thing.  In my ignorance about this, appears like something grows and grows and piles up more and more when using Firefox until freezes.   Coincides with half a dozen entries of this 'isolated' thingy.

I would prefer to choose not to have that feature if Mozilla invented and shoveled it to me for some 'security' reason.  I do not store credit cards nor personal data in my compfuser.  If this 'isolated' thingy can be blocked, I would prefer to live without it.  Even if not harmful; the abuse it takes on my memory resources is not tolerable.

---

### Post by QIII on 2022-09-01
It may be a bug or some condition peculiar to your machine/setup.  

I don't see those entries when running Firefox with several tabs open -- but that might just be the sites I have open.

---

### Post by mIk3_08 on 2022-09-02
> **Innernet said:**
> Will report when I find out as solid behavior.  From memory, it lingers in the 'System monitor' but will confirm later.   Am using 'Web' browser when Firefox gets clogged by apparently this 
isolated' thing.  In my ignorance about this, appears like something grows and grows and piles up more and more when using Firefox until freezes.   Coincides with half a dozen entries of this 'isolated' thingy.

I think this is not an intruder. I think this is part of the tabs you  opened on Firefox. I think this is a part of security features of Firefox  that prevents hackers from cloning, mirror or whatsoever for the purpose  of stealing important data from us end-users of Firefox. By the way, I always use Firefox but haven't encountered any issue like yours using Firefox so far. Regards and  cheers

---

### Post by col48 on 2022-09-06
This is not limited to Ubuntu.  A quick internet search throws up this, for example, on a Fedora forum.

[https://forums.fedoraforum.org/showthread.php?328149-Isolated-Web-Co-virus&p=1857400]("https://forums.fedoraforum.org/showthread.php?328149-Isolated-Web-Co-virus&p=1857400")

If that post is right, it may be worth looking at the list of websites you routinely visit in case one or more of them is bringing this on.

---

