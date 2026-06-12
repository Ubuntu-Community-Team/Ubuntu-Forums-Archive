---
title: "junk at login"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-02
when i log in, it shows a bunch of crud before completely loading, for example, there is a pure white bar at the top of the screen, instead of my single taskbar there, and my awm icons are at another part of the screen, or else there are white blocks places. what???

---

### Post by glennric on 2008-05-02
That is a bug in awn when using compiz that has been there for a long time.  I am still waiting for that to be fixed.  I am running the latest bzr version and it still isn't fixed.

---

### Post by frup on 2008-05-02
Possibly stuff starting?

Do you have a lot of excess services starting as you log in to your session? Could it be AWN loading without the GL settings all fully loading? Is your computer fast?

You should have a play around with system> preferences> sessions and see if there is stuff you don't want starting on start up and sysetm> administration > services. You might be able to clear some CPU and ram power to make the "artefacts" less noticeable.

---

