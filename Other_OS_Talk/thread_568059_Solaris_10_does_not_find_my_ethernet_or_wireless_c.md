---
title: "Solaris 10 does not find my ethernet or wireless card, Solarisforums NO HELP AT ALL"
date: 2007-10-05
forum: Other OS Talk
---

### Post by rudeboyskunk on 2007-10-05
So if anybody here uses Solaris and has this problem, you'd be a big help.  There are about 5 users on the Solaris forums and only about 10% of the questions get answered.

I'm trying to get internet to work on my Solaris partition, but the OS cannot find my ethernet card nor my wireless card.  I'm at work now so I can post details on what types they are in about an hour or so when I get home.

Is there a quick fix, or does it take about 3 hours worth of editing config files?

---

### Post by jrusso2 on 2007-10-05
What makes you think Solaris even supports your hardware?

Solaris has very limited hardware support and most of it is old hardware.

The times I played with Solaris I had to find a very old ethernet card for it.

---

### Post by qamelian on 2007-10-05
Did you run the compatibility tool on the Solaris web site first to be sure your hardware will work?

---

### Post by rudeboyskunk on 2007-10-05
I ended up finding the solution.  I had to find out what exact kind of card it was, then checked and found that Solaris does not *officially* support it, but there is a driver for it.  I found it and as soon as I make Solaris and Ubuntu dual-bootable, I will install.

---

### Post by D-EJ915 on 2007-10-06
you are using the official Sun solaris I assume?  "Solaris community edition" is light-years beyond the official Sun distribution of solaris.  If you end up not being able to get it to work, try it out, even though I have sun hardware I stuck a netgear wireless card in it and it even didn't work in windows but worked with solaris community edition on first boot, go figure.
> **jrusso2 said:**
> What makes you think Solaris even supports your hardware?

Solaris has very limited hardware support and most of it is old hardware.

The times I played with Solaris I had to find a very old ethernet card for it.A lot of shitty ethernet cards don't even work well with linux, a good ethernet card is always a good thing to have handy.

---

