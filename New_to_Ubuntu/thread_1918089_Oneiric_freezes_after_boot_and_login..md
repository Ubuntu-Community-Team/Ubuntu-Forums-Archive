---
title: "Oneiric freezes after boot and login."
date: 2012-01-31
forum: New to Ubuntu
---

### Post by misssarahdee on 2012-01-31
Every time I boot into Oneiric, to which I have newly upgraded, my laptop freezes very soon after the login screen. No mouse, no keyboard. No icons in the bar at the top right (battery, power, network status etc).

This happens regardless of whether I have properly shutdown in the previous session.

If I reboot, I have to run a fsck, and then it boots fine, and I'm very happy with the upgrade from 10.04.

Further, if my computer suspends, it doesnt want to wake up from a black screen with blinking cursor.

Any ideas? I'm sure there's a simple explanation, but I'm a bit of a noob.

---

### Post by Double.J on 2012-01-31
Hi there, there's been a few compiz issues for some people upgrading.. not sure if it's the same for you, but could try giving it a go?

```
unity --reset
```

If this fails are you able to boot into ubuntu 2D by clicking the cog next to the user name box on the login screen?

Hope it helps!

---

