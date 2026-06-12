---
title: "when to uncheck ubuntu-backports"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jepong on 2011-09-06
I installed Ubuntu 11.10 Beta 1 last night. I notice in the Software Source that aside from the normal ubuntu-updates and ubuntu-security... ubuntu-backports is checked. 

I know we're still in development stage but will this be unchecked on final release or should we uncheck it now?

thanks a bunch!

---

### Post by 3rdalbum on 2011-09-06
> **jepong said:**
> I installed Ubuntu 11.10 Beta 1 last night. I notice in the Software Source that aside from the normal ubuntu-updates and ubuntu-security... ubuntu-backports is checked. 

I know we're still in development stage but will this be unchecked on final release or should we uncheck it now?

thanks a bunch!

Backports doesn't usually come checked. I don't know if it will be unchecked later, or if this is a purposeful change. But it doesn't hurt to uncheck it, and it doesn't hurt to leave it on. There shouldn't be anything in the Backports repository yet anyway.

---

### Post by coffeecat on 2011-09-20
Just thought I'd bump this up because I missed this thread first time around and I've only just noticed that backports are enabled in Synaptic in two systems. I didn't enable them: one from the Beta1 ISO and one from the 14th September daily.

Seems to be an odd thing to have checked by default. It won't make any difference during testing, but it could be problematic after final release if you don't want backports and it doesn't get disabled automatically in an update before final.

---

### Post by jbicha on 2011-09-20
Backports is now enabled by default but updates have to be explicitly installed since the priority is set low (similar to how it works on Debian. Enabling experimental doesn't update your system to experimental versions unless you specifically tell it to)

[Here's]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-o-backports-ui") some discussion about exposing this in Update Manager but I don't know if it was actually implemented yet.

---

### Post by coffeecat on 2011-09-21
Thanks for that. I'd missed that. That makes a lot of sense.

---

