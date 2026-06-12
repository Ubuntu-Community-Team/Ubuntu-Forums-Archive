---
title: "Am I missing something?"
date: 2011-06-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by RJ12 on 2011-06-27
On the Daily Builds webpage, I only see PowerPC Images, have the others not been built yet, or did they move the others to another page?

---

### Post by bennachie on 2011-06-27
The effect seems to be restricted to Ubuntu (Kubuntu and Xubuntu have recent non-ppc builds). Judging from the long list of not-yet-available packages evident at the moment when you run Software Update under Ubuntu Oneiric, nightly builds might have been deemed too problematic during the run-up to the scheduled release of A2 on 30 June.

But your guess is at least as good as mine!

---

### Post by RJ12 on 2011-06-27
> **bennachie said:**
> The effect seems to be restricted to Ubuntu (Kubuntu and Xubuntu have recent non-ppc builds). Judging from the long list of not-yet-available packages evident at the moment when you run Software Update under Ubuntu Oneiric, nightly builds might have been deemed too problematic during the run-up to the scheduled release of A2 on 30 June.

But your guess is at least as good as mine!

Hmm... Ok, thanks! I will wait for A2 :)

---

### Post by VinDSL on 2011-06-28
The last Ubuntu 32-bit Daily Build that I acquired was on Saturday, 25-Jun, 10:30 PM.  

This Daily Build was actually from Friday, 24-Jun.

Since then, all I've seen on that page is PowerPC images.

Soooo, I *guess* we can take a breather, until A2 is released...  :D

---

### Post by VinDSL on 2011-06-28
I just did some forensics, and it supports the theory.  :)

I did a Google Search for "Ubuntu Daily Build", then looked at the cache.

The cache timestamp was Sunday, 26-Jun, and it's still showing Friday, 24-Jun, ISOs as the last non-PowerPC Daily Builds:


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-28-jun-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-28-jun-2011.png")[/INDENT]


Thus, it would appear that Friday, 24-Jun was the last of the Daily Builds, for a while.  ;)

---

### Post by VinDSL on 2011-06-28
Bwahahaha!  Cancel that...

They're b-a-c-k  :D

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Gotta go do an update...

---

### Post by jerrylamos on 2011-06-28
Just did a zsync from 24 June to 28 June.  There was relatively little change.  Now to boot the .iso...

Jerry

---

### Post by jerrylamos on 2011-06-28
The .iso booted O.K.

Lightdm crashed when I opened a terminal and entered:
df
Blooey.  No gdm any more.  Back to command line.  I then did:
sudo service lightdm stop
sudo service lightdm start

It's back running again.

There's nothing in /var/crash so I don't know if filing a ubuntu-bug lightdm would show anything.

Jerry

---

### Post by lucazade on 2011-06-28
> **jerrylamos said:**
> The .iso booted O.K.

Lightdm crashed when I opened a terminal and entered:
df
Blooey.  No gdm any more.  Back to command line.  I then did:
sudo service lightdm stop
sudo service lightdm start

It's back running again.

There's nothing in /var/crash so I don't know if filing a ubuntu-bug lightdm would show anything.

Jerry

same here.. this happens from some days in livecd.
I haven't reported as well.

---

### Post by sparker256 on 2011-06-28
> **jerrylamos said:**
> The .iso booted O.K.

Lightdm crashed when I opened a terminal and entered:
df
Blooey.  No gdm any more.  Back to command line.  I then did:
sudo service lightdm stop
sudo service lightdm start

It's back running again.

There's nothing in /var/crash so I don't know if filing a ubuntu-bug lightdm would show anything.

Jerry
Try this command that I have used for a couple of days.
sudo restart lightdm
Seems to always work for me when I need to get back to a desktop.

Bill

---

