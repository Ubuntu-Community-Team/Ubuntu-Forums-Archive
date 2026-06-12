---
title: "GUI based tools to troubleshoot Laptop"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by Newbeatontheblock on 2013-02-21
Hi,
I have a new Aspire 5538g.  It is working ok but it crashes when skype is launched and this freezes my pc.

Pretty sure it is Harware related.

I would like to use Ubuntu Easy use Troubleshooters to check whats wrong with my hardware,,,,,

Any suggestions for a nube that is not that good in terminal stuff

?

Thanks

---

### Post by MG&amp;TL on 2013-02-21
"Terminal stuff" is by far the most efficient and effective way of debugging things, it may be worth getting used to it. :)
 
As for your problem, since Skype is a pretty normal program other than the fact it accesses your webcam, I suspect it is indeed a problem with your webcam. To test that, try installing another program that uses your webcam and seeing if that works. "Cheese", a photobooth program, is quite fun. :)

---

### Post by Newbeatontheblock on 2013-02-21
Hi thanks very much for this reply
I wouldn t have taught about that...

Thank you

---

### Post by Newbeatontheblock on 2013-02-21
Okay,

I have installed Cheese and this working Fine which makes me suggest this isnt related to my webcam...

As i have to reconnect to wife 3 times a day or more and there are no other issues on other laptops in my lan  this could be the real issue.

Any other suggestions maybe ?

Maybe as you said time for me to start getting used to the terminal

regards

---

### Post by MG&amp;TL on 2013-02-21
Hm. That's interesting.
 
When your computer freezes, how exactly does it freeze? Does it:
 
a) "Freeze" with windows and such still in place? This usually means the display stack has died in a bizarre fashion. (and therefore presumably a graphics card problem). 
 
b) Blank the screen, with nothing else happening? This could be a variety of things.
 
c) Blank the screen, with keyboard lights flashing? Uh-oh. If the keyboard lights flash continuously, you've got a kernel panic, similar to a BSOD on windows. This doesn't happen very often at all.

---

