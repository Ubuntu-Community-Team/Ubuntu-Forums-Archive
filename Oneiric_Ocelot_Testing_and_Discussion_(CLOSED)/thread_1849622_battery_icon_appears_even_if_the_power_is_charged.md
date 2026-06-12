---
title: "battery icon appears even if the power is charged"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by chenzhiwei on 2011-09-24
Hello,everyone.
the battery icon always on the panel, and I don't know how to hide it.

gnome-power-manager is Power statistics now, I don't know if ubuntu 11.10 has some changes about Power-manager.

The attached images bellow may show you my problem.

Thank you!

---

### Post by mc4man on 2011-09-24
What you're showing in sceen 1 is an indicator (indicator-power
It shows up if installed, doesn't if not. 
There isn't any apparent in-between & doesn't even  'care' if there is no battery at all other than a changed look

---

### Post by chenzhiwei on 2011-09-24
But why this battery icon still exist even if the power is charged?
Ubuntu 11.04 has not this problem.

---

### Post by mc4man on 2011-09-24
> **chenzhiwei said:**
> But why this battery icon still exist even if the power is charged?
Ubuntu 11.04 has not this problem.

because - 
'It shows up _if installed_, doesn't if not.'

---

### Post by xyzzyman on 2011-09-24
In 11.04 there was an option to make it disappear when fully charged, but it appears it has been removed in 11.10 for some reason...

---

### Post by chenzhiwei on 2011-09-24
> **xyzzyman said:**
> In 11.04 there was an option to make it disappear when fully charged, but it appears it has been removed in 11.10 for some reason...

Thank you!

---

### Post by alphacrucis2 on 2011-09-25
After upgrading Natty to Oneric I now have two battery indicators although one of them doesn't appear to actually do anything.

---

### Post by bbrg548 on 2011-09-28
> **alphacrucis2 said:**
> After upgrading Natty to Oneric I now have two battery indicators although one of them doesn't appear to actually do anything.

I'm seeing the same issue. This is a known bug in gnome-settings-daemon, [Bug #83397]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/833397"). Looks like they're still trying to figure it out.

---

### Post by LCollins on 2011-10-09
From what I gather from this thread, this indicator is* deliberately* designed to appear even when the battery is not fully charged.

Does anyone know if the above is true (i.e. that this is not a bug)? That is, if there will be an option (if not now, then later) to hide the power indicator if the battery is fully charged (like in Natty)?

---

### Post by Quackers on 2011-10-09
Lol, I've got the opposite problem. I can't get a battery icon to show at all in gnome-shell :-) Over the last few weeks it has disappeared with certain updates, then re-appeared after newer updates. Now it seems to have disappeared for good! :-(

---

### Post by mc4man on 2011-10-09
for hiding, maybe it will be fixed in 11.10
[https://bugs.launchpad.net/ubuntu/+source/indicator-power/+bug/811769](https://bugs.launchpad.net/ubuntu/+source/indicator-power/+bug/811769)

---

