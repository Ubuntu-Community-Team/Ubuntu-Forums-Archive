---
title: "Scaling on HiDPI"
date: 2020-11-23
forum: New to Ubuntu
---

### Post by joubqa on 2020-11-23
Using Ubuntu on a 4k tv. I have it set to 1080p, 12& fractional scaling. In some (Snap?) apps the UI is tiny. I was able to fix it in Spotify with force scaling, Godot had scaling in it's settings. Now installed Steam and it has the same problem. Is there something I can do globally so I don't need to search for a solution for every program?

---

### Post by CelticWarrior on 2020-11-23
Have you tried setting it to the native resolution and then apply the desired scaling factor?
Any monitor should work best with its native resolution.

---

### Post by joubqa on 2020-11-23
> **CelticWarrior said:**
> Have you tried setting it to the native resolution and then apply the desired scaling factor?
Any monitor should work best with its native resolution.

I think the problem with that was that it introduced problems when using two monitors (1080p laptop and the 4k TV). I'll try that again and see what problems I get with that setup

edit: It scales the laptop screen also at 200%, making it unusable. I guess you can't have different scaling factors with multiple monitors?

---

### Post by DuckHook on 2020-11-24
> **joubqa said:**
> …I guess you can't have different scaling factors with multiple monitors?
You can, but it requires serious xorg.conf Fu: [https://www.x.org/releases/current/doc/man/man5/xorg.conf.5.xhtml](https://www.x.org/releases/current/doc/man/man5/xorg.conf.5.xhtml)

As you can see, not for the faint of heart.

Sorry, but my own xorg.conf Fu has atrophied to the point where it is now minimal, so can't help you with details.

---

### Post by joubqa on 2020-11-26
I'm just using 2160p with 200% when using the TV and it automatically switches to 1080p when I open the laptop monitor. This works fine.

---

