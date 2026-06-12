---
title: "Update Issue?"
date: 2010-04-16
forum: Repositories &amp; Backports
---

### Post by 5BallJuggler on 2010-04-16
Not sure if this is posted in the right place, please move if necessary.

I updated to Lucid 8 days ago, no real issues with it so I'm pretty happy, but the system has not updated, I check with the update manager on a daily basis but there are never any.

today my desktop showed a warning symbol (yellow triangle with an exclamation mark in it) saying that my system was outdated, I checked the update manager again and there was nothing.

Is this normal? not seen it before and I've tested beta on the last 2 versions of Ubuntu.

---

### Post by dino99 on 2010-04-25
with synaptic, check that your repos only update from lucid repo and comment every third party and ppa if any. Then into console:

-sudo apt-get update
- sudo apt-get install -f
- sudo apt-get dist-upgrade

---

