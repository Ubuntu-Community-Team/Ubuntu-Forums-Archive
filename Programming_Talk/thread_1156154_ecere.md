---
title: "ecere"
date: 2009-05-11
forum: Programming Talk
---

### Post by sartic on 2009-05-11
Any comment on this?

[http://www.ecere.com/technologies.html](http://www.ecere.com/technologies.html)

Anyone using it?

---

### Post by sartic on 2009-05-19
I tried on xp (and 3d test as chess works), but on ubuntu 9.04 it gives me X errors and ide is unstable. Sounds promising but no go....

---

### Post by jerstlouis on 2009-07-04
Hey guys... One problem with 9.04 is that only the open source drive is available for Intel chipsets. Now a bug haunting Ecere is the bad support in general in many drivers for the Xrender extension with an 8 bit alpha component picture and a fixed color, which is used among other things by the Ecere font engine. There are plans to change it to using glyphs at some point in the near future, but until them this renders many drivers unusable... This is likely what the X errors are about. Bug tracker is at [http://www.ecere.com/mantis/](http://www.ecere.com/mantis/) . 

Please join us on IRC at #ecere on irc.freenode.net or otherwise contact us for any help / support for Ecere.

Cheers

Jerome

---

### Post by sartic on 2009-07-31
We were in contact by email. (I was complaing about those errors).
Sorry but I decide to wait new version. I want stable development language before learning new language. Your manual is like a Zen. I know C and I moved to Euphoria (it has greatest manual, just the way it should be); but it is short in GUI. I tried all GUI SDK kits.... they suffer to from stability and "betaizam". Looking now on QT but it is big and sounds complex. Stumbled...
ps: and those irc boys 2 much arch slash hack again ;)

---

### Post by sartic on 2010-05-26
Just for curiosity, still not usable at all:

[https://launchpad.net/~ecere-team/+archive/ppa](https://launchpad.net/~ecere-team/+archive/ppa)

Even if you use source to compile u will end width graphic glitches in IDE and/or not working IDE.

To bad, i would learn eC if i can compile for win32/lnx.

Still trying to find some GUI driven IDE width powerfull language for multiplatform.

---

### Post by jerstlouis on 2010-05-26
Hi Sergio,

That PPA is not quite working yet (missing graphics icons and such).

We should update it in the upcoming weeks, along with a slightly updated version. I am coming back from a 1-month holiday tomorrow, so next week I should be able to assist you to compile, get everything running, and get you started learning eC and the Ecere GUI toolkit if you are interested.

We also have new forums at [http://www.ecere.com/forums/](http://www.ecere.com/forums/)

I hope you let us help you make Ecere your software development kit of choice ;)

All the best,

Jerome

---

### Post by sartic on 2010-05-30
I am still waiting new stable version.

---

### Post by jerstlouis on 2012-03-12
Hi Sergio,

I realize a lot of time passed :)

But the Ecere SDK 0.44 is finally out, and we sorted out the PPA issues. We've got daily builds going, importing right from our GitHub repo.

[https://code.launchpad.net/~ecere-team/+archive/ppa](https://code.launchpad.net/~ecere-team/+archive/ppa)

Hoping you'll give Ecere another try!
If you do, please let me know if you encounter any issues.

Best regards,

Jerome

---

