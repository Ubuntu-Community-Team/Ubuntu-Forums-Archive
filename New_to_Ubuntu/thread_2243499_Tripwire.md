---
title: "Tripwire"
date: 2014-09-09
forum: New to Ubuntu
---

### Post by cacahuatey on 2014-09-09
I posted yesterday saying i have intrusions on my pc, and have been told by a friend to try using tripwire to see if that is true. Thing is that i have been reading a lot and every page says something different about configuration and instalation. Do you have any guide trustable?

---

### Post by Lars Noodén on 2014-09-09
Tripwire and other tools like it work when you start from a known clean system.  It will detect any subsequent changes.  
Its database will have to get refreshed any time you update the system or its packages.

---

### Post by cacahuatey on 2014-09-09
i reinstalled ubuntu and now seems to be all ok, which kind of this toold would you recommend me? The best one for a noob

---

### Post by Lars Noodén on 2014-09-11
I'd recommend reading up on specific tools and get an idea of what they try to do.  Then maybe one of them will stand out as more interesting to try.  Tripwire, Aide, OSSEC and Samhain are all a bit different.  If you can program or write scripts then you could make a simple one yourself in an afternoon or so, but then you'll start adding features and more features and so on and eventually end up with something similar to those four.  

In general, they don't keep people out.  They can be part of a layered defense and help to possibly spot when someone has gotten in already.

---

