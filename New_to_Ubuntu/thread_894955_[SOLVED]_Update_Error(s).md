---
title: "[SOLVED] Update Error(s)"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by jfbays on 2008-08-19
What is this:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

...and this:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

...and what can I do about it?

Are these sorts of messages common?

---

### Post by halitech on 2008-08-19
> **jfbays said:**
> What is this:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
either your connection to the network is down or the repo is not available or misconfigured

> 
...and this:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

...and what can I do about it?
do you have synaptic open at the same time and did you use sudo before trying to install something?


> 
Are these sorts of messages common?

not really, least not for me unless I do something stupid :)

---

