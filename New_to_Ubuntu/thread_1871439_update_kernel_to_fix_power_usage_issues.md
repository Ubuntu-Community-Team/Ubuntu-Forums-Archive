---
title: "update kernel to fix power usage issues?"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by Peter Parkorr on 2011-10-28
Hi,

Looking for some advice on what to try next to save more juice on my machine.

I have been using Natty on my Acer 5750G with core i7 2630M and GeForce Gt540 graphics card for a month.

The max battery time has been about 2 hours, with light use, and not much over an hour when streaming a video.

I installed powertop to see if it helped, it showed power use climbs from ~10W to 20W within 1st 5 minutes after powering up and remains at 20 - 23 watts even with no programs running.

I installed Jupiter from wedupd8team but it had little/no effect on my system, which I notice other acer users have reported too.

I disabled bluetooth to save power and also wireless networking as the connection kept dropping and I have ethernet for now.

**First problem**, with powertop I cannot see anything related to Tunables, cannot access Tunables and so it has limited value, I can just see how much power I am using and wakeups per second. I tried #ubuntu IRC help tonight, and it is not an issue with terminal being too narrow, when maximised Tunables are not there either and pressing arrow keys just causes powertop to become erratic.

I added this; to my grub and it did not make a difference. > pcie_aspm=force
Then I added > i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 to grub as well (solution from phoronix according to other threads) but this has caused my display some problems (reduced resolution).

I am going to fix resolution and uninstall/reinstall powertop but **failing these working:** would updating to the latest kernel (3.1) help? Or how about going to an older kernel (someone on another thread improved their battery life by going to 2.6.35, before kworker and other issues appeared)? I am not sure how to change which kernel I use yet, but can I replace a kernel without affecting other aspects of my installation (version, programs)?

Sorry long post, attaching powertop screenshots for reference. One has <10 wakeups per second but still 20w usage...   is it to do with my processor?

Any help/suggestions appreciated,
Shane

---

### Post by rajuvembala on 2011-10-29
Read this

[http://www.fewt.com/2011/09/about-kernel-30-power-regression-myth.html]("http://www.fewt.com/2011/09/about-kernel-30-power-regression-myth.html")

its not a solution but its related to the topic.

---

### Post by Peter Parkorr on 2011-10-29
Thanks rajuvembala,

I got this link already from the IRC help channel. As others in the comments say, denying there is over-use of system resources doesn't help me improve my laptop performance in any way.

Maybe I will try kernel 2.6.35 or something, or TLP/tuned that are mentioned.

Edit: part of my issue is I cant get a newer version of powertop than 1.13 to try turning certain modules off. Somebody must be able to help me with that?

Shane

---

