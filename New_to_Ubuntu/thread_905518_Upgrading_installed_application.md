---
title: "Upgrading installed application"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Accinson on 2008-08-30
Hi everybody,
i have a really noob question :)

How can i upgrade to the latest version one of the ubuntu supported applications (i.e. those i can get through synaptics)?

My situation is:i want to use Qt4,but through Synaptics i can get at most the 4.3 version,but the latest one is 4.4.
Is there a way to do it through Synaptics or i can only install it through tarball?
Thanks in advance!

---

### Post by gmxgeek on 2008-08-30
Usually, the most cutting edge version of software will not be in synaptic, as it has to go through vigorous testing before being put in the main hardy repos.

If you really want it however, you can do one of two things.

1.) Enable the Proposed Hardy updates
```

System -> Administration -> Software Sources -> Update Tab -> Check Pre-Release Updates

Close

Run Update Manager

```
*NOTE* This may cause some problems. If you don't know what you're doing, don't do it!

2.) Download the source from the website and build it yourself

---

