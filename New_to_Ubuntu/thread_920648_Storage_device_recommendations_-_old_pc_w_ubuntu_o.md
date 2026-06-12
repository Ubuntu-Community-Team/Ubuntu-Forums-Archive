---
title: "Storage device recommendations - old pc w/ ubuntu or NAS?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by buckwheat on 2008-09-15
We purchased our daughter a new laptop, which freed up the old pc she had been using (Dell OptiPlex GX110, 512mb, PIII ~600gHz, 15 and 30 gb drives).  I spent a couple of evenings installing Hardy Heron, and without too much trouble was able to get Samba running and installed the LAMP stack.  I can read/write to it from the other machines, and can successfully point a browser to the box (thanks in large part to helpful threads here!).  All surprisingly painless, and the machine has acceptable response as long as I keep the graphic demands low.

Anyway, that was all pretty much proof-of-concept, as I am thinking of using the box as a simple file server / backup device for the home network.  I'll need to make a small investment, and thought I would see if anyone had advice from a similar experience.

It looks like I'll need a raid controller and a couple of SATA drives, should set me back about $200 (I'm in the states).  The Dell is maxed in RAM, but I'm not doing anything fancy on the machine so I don't think that will be an issue.

So, should I just go out and buy a 1 tb NAS (2 x 500 gb), or put the controller and a couple of 500 gb drives in this box?  It looks like the price would be about the same, and I could probably have the NAS up and running in a few minutes.  But I would miss out of the fun, and I'm quite enjoying working with Ubuntu.

Any suggestions?

---

### Post by egalvan on 2008-09-15
> **buckwheat said:**
> We purchased our daughter a new laptop, which freed up the old pc she had been using (Dell OptiPlex GX110, 512mb, PIII ~600gHz, 15 and 30 gb drives).  I spent a couple of evenings installing Hardy Heron, and without too much trouble was able to get Samba running and installed the LAMP stack.  I can read/write to it from the other machines, and can successfully point a browser to the box (thanks in large part to helpful threads here!).  All surprisingly painless, and the machine has acceptable response as long as I keep the graphic demands low.

Anyway, that was all pretty much proof-of-concept, as I am thinking of using the box as a simple file server / backup device for the home network.  I'll need to make a small investment, and thought I would see if anyone had advice from a similar experience.

It looks like I'll need a raid controller and a couple of SATA drives, should set me back about $200 (I'm in the states).  The Dell is maxed in RAM, but I'm not doing anything fancy on the machine so I don't think that will be an issue.

So, should I just go out and buy a 1 tb NAS (2 x 500 gb), or put the controller and a couple of 500 gb drives in this box?  It looks like the price would be about the same, and I could probably have the NAS up and running in a few minutes.  But I would miss out of the fun, and I'm quite enjoying working with Ubuntu.

Any suggestions?


wow, I'm surprised no-one has jumped in on this yet!


OK, first, from the FUN FACTOR ALONE, I would go with the Dell-as-server route..

But then that's what I did myself :) so what can I say...

Second, you can still pick up 500gb PATA drives for under $100, so you can get in even cheaper...(I think 750gb are the biggest PATA, but may not be easily avaialbe.)

edit:: just checked Newegg, 750gb PATA @ $130


Next, you can have the fun of learning to set up a SERVER-style install.

Or install Xubuntu or another even lighter-wieght windows manager

Or how about FreeNAS?

[http://www.freenas.org/](http://www.freenas.org/)

And remember you can always run the server "headless" and access it from another Linux/Win machine.

Lots of FUN, EDUCATIONAL things to do here.


That being said, you are running older hardware, so the RAID may be a good idea if you need to safely store information.


And remember to give that old machine a GOOD CLEANING. It can can a lot of dust-bunnies hiding in there.
The high-pressure air found at a mechanic's shop is very useful, but be careful.

ErnestG

:popcorn:

---

### Post by niteshifter on 2008-09-15
Hi,

Hmmm, the fun-factor. Hadn't considered that, but egalval does have a point.

Here's my take: Four years ago my RH5-based file server started getting twitchy. So I bought a 250GB NAS - a LaCie D2 - to replace it with. The price was right, so why not? Plus, saved the time and effort involved with rolling my own solution.

Mr. D2 died last week. Drive OK, the controller / computer part is dead. Never saw it coming.

So ... this week I'll be having a data copying / sifting party (180GB worth). And building my own NAS - with components replaceable / fixable by me.

Lesson learned. Now passing it on to others ....

Not knocking LaCie, that NAS worked very well, and I've other gear by them. Good stuff. But these things do fail, and I failed to consider the serviceability of the unit.

---

### Post by buckwheat on 2008-09-15
egalvan

> That being said, you are running older hardware, so the RAID may be a good idea if you need to safely store information.

Yes, I wanted the RAID setup to make sure it was fairly solid, what with the family treasures it will be storing.  Looks like I can get a decent controller for about $60, then $70 ea for the 500 gb drives.  

> And remember to give that old machine a GOOD CLEANING. It can can a lot of dust-bunnies hiding in there.

Oh, yeah, she was loaded.  Surprised it hadn't already burst into flames...

---

### Post by egalvan on 2008-09-15
> **buckwheat said:**
> Yes, I wanted the RAID setup to make sure it was fairly solid,

then make sure you are running some sort of mirroring.


> Oh, yeah, she was loaded.  Surprised it hadn't already burst into flames...

Hope you didn't forget the inside of the power supply...

And one more I forgot, the heat-sink paste is likely turned to cement...
might think of removing cpu and cleaning thoroughly with alcohol.
MEK is best, but dangerous if mishandled.

Enjoy!

---

### Post by buckwheat on 2008-09-15
> **niteshifter said:**
> Hi,

... Hmmm, the fun-factor. Hadn't considered that, but egalval does have a point.

... Mr. D2 died last week. Drive OK, the controller / computer part is dead. Never saw it coming.

... But these things do fail, and I failed to consider the serviceability of the unit.

Thanks, hadn't really considered the serviceability part. It's the 'black box' bit, it's great when it works but can be a real hassle when it breaks.  And it's eventually gonna break.

Good thing is was the controller and not the drive(s)...

And the fun-factor weighs in as much as anything.  I've been jealous of the Linux adopters for years, I think I'll use this as the excuse I've been looking for.

---

### Post by buckwheat on 2008-09-15
> **egalvan said:**
> then make sure you are running some sort of mirroring.

That was the plan, haven't done it before, but in the famous words of Indiana Jone, 'How hard can it be?'

> Hope you didn't forget the inside of the power supply...

And one more I forgot, the heat-sink paste is likely turned to cement...
might think of removing cpu and cleaning thoroughly with alcohol.
MEK is best, but dangerous if mishandled.

Got the power supply, but never considered the heat sink on the CPU.  I'll look at that, but something about trying to pull it after 8+ years makes me a little worried.  I'll give 'er a wiggle and see what happens.

Thanks

---

### Post by egalvan on 2008-09-15
> **buckwheat said:**
> That was the plan, haven't done it before, but in the famous words of Indiana Jone, 'How hard can it be?'

and in the even more famous words of Han Solo "Trust me"


> Got the power supply, but never considered the heat sink on the CPU.   something about trying to pull it after 8+ years makes me a little worried.  I'll give 'er a wiggle and see what happens.

Thanks

Yes, that is the problem... the paste solidifies and becomes more than useless.

But since pcprogress.com  sells those old FCPGA cpu's shipped for under $15

"why worry?"

---

### Post by Whiffle on 2008-09-15
I'd be strongly tempted by the NAS, its going to use quite a bit less power than a full on PC.  I calculated that running my p4 desktop 24/7 would run me ~$75 a year, assuming its idle most of the time.  Might not be an issue for you, but I figured I'd bring it up.

---

### Post by egalvan on 2008-09-15
> **Whiffle said:**
> I'd be strongly tempted by the NAS, its going to use quite a bit less power than a full on PC.  I calculated that running my p4 desktop 24/7 would run me ~$75 a year, assuming its idle most of the time.  Might not be an issue for you, but I figured I'd bring it up.

Aw gee, we were just trying to have fun :)


But seriously, i agree on the $$ for electricity. There will be a difference.

---

