---
title: "Caffeine doesn't show in systray, 14.04"
date: 2014-06-22
forum: New to Ubuntu
---

### Post by newb85 on 2014-06-22
I just did a fresh install of 14.04, and installed caffeine from the official ppa (caffeine-developers/ppa).  Trouble is, when I try to open it, it doesn't appear in the app indicator area.  I can open it from the launcher as many times as I want, and it will run in the background that many times, but without the indicator, activating it or adjusting preferences is impossible.  So in this state, it's pretty much worthless.

I've read about the whitelist being removed from 14.04, but I don't think I've had to whitelist caffeine in past installs.  (My memory could be off here, though.)

---

### Post by grahammechanical on 2014-06-22
You should read this

[https://launchpad.net/caffeine/+announcement/12676](https://launchpad.net/caffeine/+announcement/12676)

It seems to me that the present release of Caffeine is doing what its developer wants it to do. 

Regards.

---

### Post by newb85 on 2014-06-22
Yeah, that seems to be the problem.  Thanks!

I think the idea of an app that does what the developer has made caffeine do is a good one.  However, I'm not happy that they did it with caffeine.  It's basically a completely different program, and it no longer fulfills my reasons for using it.  I guess I'll have to send a complaint to the developers.

I'm going to wait to mark this as solved for the moment, because while my question was succinctly answered, I don't think the issue was really addressed.  At this point, I'm not sure what would satisfy me, short of the developer giving back the functionality they took away.  But I might be surprised.

---

### Post by 0N3 on 2014-06-23
Uninstall the version you have and remove the PPA go to [https://launchpad.net/~caffeine-developers/+archive/ppa/+packages](https://launchpad.net/~caffeine-developers/+archive/ppa/+packages) and download version 2.5 debian package and install it and you should be good to go with the old version works perfect for me in 14.04. Don't forget to go to Synaptic package manager and lock the version 2.5 you installed and it wont upgrade to the 2.7 for you.

---

### Post by 0N3 on 2014-06-23
Uninstall the version you have and remove the PPA go to [https://launchpad.net/~caffeine-developers/+archive/ppa/+packages](https://launchpad.net/~caffeine-developers/+archive/ppa/+packages) and download version 2.5 debian package and install it and you should be good to go with the old version works perfect for me in 14.04. Don't forget to go to Synaptic package manager and lock the version 2.5 you installed and it wont upgrade to the 2.7 for you.

---

### Post by newb85 on 2014-06-23
On further reading, it appears that the developer has yielded to popular demand, and is going to release an toggle indicator for caffeine.  In anticipation of that, I'll go ahead and mark as solved.

---

