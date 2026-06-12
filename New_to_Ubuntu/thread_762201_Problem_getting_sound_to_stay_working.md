---
title: "Problem getting sound to stay working"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by MasterCylinder on 2008-04-21
I can get the sound to work, System- Preferences- Sound... but when ever I turn off my computer, at night or when Im going away for a while. When I come back, I have no sound??? Whats up? This has happened to me a couple of times. Is there something I can set or do to fix this?

---

### Post by Incredulous Moose on 2008-04-21
That sounds similar to a problem which I had a while ago and it turned out that the internal sound card on my motherboard was getting in the way of my Audigy.

In a terminal type "asoundconf list" for a list of available sound cards. If you see your card along with another then that might be getting in the way and you'll have to blacklist it.

---

### Post by MasterCylinder on 2008-04-28
How do I blacklist it? 

PS noticed something, sometimes it wont mount sda1 (C: drive) on the desktop, when this happens the sound works perfect, but when it does mount it the sound doesnt work, I can get it to 'test', but other than that I get no sound

---

