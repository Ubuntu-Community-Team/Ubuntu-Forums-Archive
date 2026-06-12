---
title: "synaptic trouble with 302s via proxy"
date: 2006-04-10
forum: Repositories &amp; Backports
---

### Post by ccf on 2006-04-10
For some reason, *synaptic*, and possibly *apt* in general, seems to have trouble grabbing packages from behind a proxy, because it is seeing HTTP 302 coming back ("Moved Temporarily", with the target returned in the "Location:" header).  Is this deliberate, or should I go to the trouble of filing a bug upstream (for all the good it will do)?

Cheers

---

