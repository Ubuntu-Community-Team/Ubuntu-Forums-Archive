---
title: "Security updates"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by Rob P. on 2012-11-01
Is there a way to get archived security updates of outdated versions?

I recently had to do a full wipe & reinstall of Hardy 8.04 and I no longer have the published security updates for my system.

---

### Post by MG&amp;TL on 2012-11-01
They still seem to be there: [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

...does just updating them not work?

---

### Post by Rob P. on 2012-11-01
I'm not getting any security updates with my update manager.

I see the archives in your link but have no idea how to install the updates from there.

Help?

---

### Post by MG&amp;TL on 2012-11-02
What's the contents  of the file /etc/apt/sources.list?

My understanding was that ubuntu stopped supporting Hardy, but kept the repositories as they were around for people still using it.

---

### Post by squakie on 2012-11-02
Which brings me to the obvious question - if you had to do a complete wipe and fresh install, is there a reason for not going with a newer release such as 12.04 or 12.10?

---

### Post by Cheesemill on 2012-11-02
The repositories are frozen and kept online when a release reaches end-of-life, but they are moved to a new location.

You need to edit your /etc/apt/sources.list file and change the domain part of all relevant lines to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

Edit - 8.04 Server is still supported for another 5 months, the standard repositories are still online in their usual location.

---

### Post by Rob P. on 2012-11-02
> **squakie said:**
> Which brings me to the obvious question - if you had to do a complete wipe and fresh install, is there a reason for not going with a newer release such as 12.04 or 12.10?

In my case I tried to update my Hardy to 10.04 a week ago.  The end result was such a mess I wiped and reinstalled Hardy.  10.04 doesn't support my hardware and there are no drivers available to patch it together.  None of the fixes worked either.  I spent a week trying to get this to work and then just wiped and reinstalled the OS that DID work.

Sometimes updating the OS is a bad idea.  I'm also getting the impression that ubuntu has evolved to the point where new versions are being released "just because it's time" rather than because there's a need.  And since the new versions don't support older hardware, that forces everyone to go buy the latest and greatest whizbang hardware add-on rather than being able to continue to use their current stuff.  What is interesting is that the new versions don't seem to be any improvement over the old version being updated in functionality or useability.  So the update nets nothing but new hardware sales.

Since I'm trying to make ancient hardware continue to run, that scheme doesn't work for me.

Back on topic...I did get all the updates finally.  266 of them if I remember the number correctly.  Phew!

---

### Post by squakie on 2012-11-05
What hardware is 10.04 not supporting?  There has been massive progress on video and wireless drives since then.  You really should back up what you need and then install the current release (fresh install - you won't be able to update from the release you are running).  You'll find much better hardware support, plus more people to help you with any problems.

---

