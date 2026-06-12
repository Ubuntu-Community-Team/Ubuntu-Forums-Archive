---
title: "Restricted drivers vs envy?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by wolf3491 on 2008-04-25
With gutsy, the restricted drivers for graphics and wireless worked fine since the beginning.  For Hardy, I'm going to put ultimate edition 1.8 x64 on here in place of gutsy, which comes with envy. What are the differences and advantages/drawbacks of using envy over restricted drivers manager?

---

### Post by piratesmack on 2008-04-25
> **wolf3491 said:**
> With gutsy, the restricted drivers for graphics and wireless worked fine since the beginning.  For Hardy, I'm going to put ultimate edition 1.8 x64 on here in place of gutsy, which comes with envy. What are the differences and advantages/drawbacks of using envy over restricted drivers manager?

Envy actually compiles the latest driver for you

the restricted manager installs the driver from the repository (Which may not be the latest)

I believe that right now the Hardy repositories have the latest nvidia driver

---

### Post by wolf3491 on 2008-04-25
So I should stick with the restricted driver rather than envy?

---

### Post by crjackson on 2008-04-25
> **wolf3491 said:**
> So I should stick with the restricted driver rather than envy?

Personally I like envy and it would seem that the developers do as well since it's now in the repositories.

That said, I have used both and they both worked fine for me.  I can't see any difference between the restricted drivers from the repos, and the latest/greatest driver installed using envy.

---

### Post by alienexplorers on 2008-04-25
I use Envy since the Restricted Driver Manager does not load the correct driver for my video card.  If you have a newer video card I would use the Restricted Drivers, but if you have an older card like mine I would stick with Envy.

---

### Post by wolf3491 on 2008-04-25
I have a newer graphics card, so I will just stick with the restricted drivers if I can.  Thanks all!

---

### Post by lunarcloud on 2008-04-25
my issue has always been that I cannot go back to the repository version of the drivers after i've installed them via envy, they just dont work and chaos ensues.

---

### Post by axor1337 on 2008-04-26
I have never had any luck with ENVY every time I use it I have to use a bunch of terminal to uninstall for me it has never installed the right drive I like the restricted drivers better this is most true with ATI cards  Nvidia seem to have better luck with ENVY

---

### Post by piratesmack on 2008-04-26
> **wolf3491 said:**
> So I should stick with the restricted driver rather than envy?

Right now I don't think it'd matter. I'm pretty sure they already have the latest version of the Nvidia driver in the repositories so installing from the restricted manager would install the same driver.

With envy, it'd have to also install all the build dependencies to compile it so the restricted manager would probably be the better way to go

---

### Post by PartisanEntity on 2008-04-26
If the restricted driver manager loads the right driver for you and if it is the latest driver then I would stick with that. Envy is a useful tool if and when there are newer drivers outside the repo or your card is not correctly identified.

---

