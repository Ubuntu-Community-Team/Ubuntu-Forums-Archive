---
title: "Partial Upgrade?"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by Old-un on 2011-11-12
I made a fresh install of Ubuntu 11.10 and thought everything was fine but this morning i was advised to do a _partial upgrade_. Could someone tell me why this partial upgrade was necessary please

---

### Post by Paqman on 2011-11-12
Partial upgrades are almost never a good idea. Usually they're caused by the repositories being a little out of sync. That should resolve itself in a few hours.

If you're not bothered waiting, just ignore it for now and try the upgrade again tomorrow. If you really want to do it now, try opening Software Sources and switching to a different server for your updates. Then in Update Manager hit "check" again and see if it picks up a list that isn't mangled this time.

---

### Post by Old-un on 2011-11-12
Have to be honest and say that i clicked on the Partial Upgrade prior to my first post concerning this topic. Everything seems to be running fine at least for now.

---

### Post by Paqman on 2011-11-12
I'd go ahead and try a different server to see if you pick up any extra packages. If not, then it seems like all is well.

---

### Post by sadaruwan12 on 2011-11-12
Partial Upgrades happen when the servers are out of reach or down for a maintenance. When that happens the update manager cant reach them so it downloads the healthy packages from the other server while trying to access the downed once.

When it finishes the downloading of the other healthy packages it asks you to do a partial upgrade using the once that have already been downloaded but this is not a very good thing 'cos if your day is not good then this might break something or cause a system crash.

This partial message will disappear as soon as it can access the unreachable server which was down during your first attempt.

What we recommend is that if you get that message click no and wait till it can access all the severs and do the update when it can.

---

