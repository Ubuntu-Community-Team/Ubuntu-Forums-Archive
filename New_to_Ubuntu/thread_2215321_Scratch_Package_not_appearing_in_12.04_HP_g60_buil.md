---
title: "Scratch Package not appearing in 12.04 HP g60 build after all updates"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by Gabriel_Kyne on 2014-04-06
I am having a weird problem with one of my HP G60 machine which is running 12.04 LTS full updated software.  When I try and install scratch ( MIT software) it says E: Package 'scratch' has no installation candidate.  I have tried searching for it with sudo apt-cache searcch scratch but it does not come up.

However on other machines running same installation it is finding and installing with out a problem.

What am I missing?

Thank you for taking the time to look at this query.

Newbie

Gabrie

---

### Post by Rob Sayer on 2014-04-06
Something to do with the repos you've enabled I suspect.  I just looked for scratch in synaptic (which I and many others here much more knowledgeable than I) highly recommend for newer users ... it's worth the slight learning curve).  It's there but I'm running 13.10 on this netbook so the repositories may be slightly different.

This link ...

[http://scratch.mit.edu/scratch_1.4/](http://scratch.mit.edu/scratch_1.4/)

... has a debian/ubuntu link that should install it using dpkg.

And again, try synaptic package manager.

---

