---
title: "Antivirus!"
date: 2010-04-04
forum: Recurring Discussions
---

### Post by gagea on 2010-04-04
I am looking for an antivirus. I installed AVAST and when I try update it, it return an error. Is there any suggestion for free and strong antrivirus?

---

### Post by Pjotr123 on 2010-04-04
Absolutely unnecessary. Read this:
[http://sites.google.com/site/easylinuxtipsproject/security](http://sites.google.com/site/easylinuxtipsproject/security)

Welcome to Linux! :-)

---

### Post by ronnielsen1 on 2010-04-04
I pretty much don't worry about virus protection   unless I'm checking a windows box but there's clamav (klamav) available in the repositories.

There's also AVG,

---

### Post by Revolutionary101 on 2010-04-04
I doubt that you will need it but if you still want to download an anti-virus, download clamtk. Clamtk is a free and easy to use GUI for clamav. To install it just look for clamtk in Synaptic.

---

### Post by Kevbert on 2010-04-04
ClamAv/Clamtk is one of the best. See [[COLOR="Red"]this[/COLOR]]("http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html") for instructions on how to install. You'll probably only ever find Windows/DOS viruses which are unlikely to effect your Linux Operating System.
Another one you may like to try is [COLOR="Red"][BitDefender]("https://help.ubuntu.com/community/BitDefender")[/COLOR].

---

### Post by cariboo on 2010-04-04
This topic has been covered so many times, it should automagically be in recurring, but since it isn't. Moved.

---

### Post by 2hot6ft2 on 2010-04-04
avast fix

```
gksu gedit /proc/sys/kernel/shmmax
```
copy and paste this over the number that is already there
128000000
Save and close.

Source was the avast forum and was given by the one that wrote avast apparently. While this isn't the post from the author that I read before it says exactly the same thing.
[http://forum.avast.com/index.php?PHPSESSID=9cba7077ccb4b141cbb74cf64a2db104&topic=57775.0](http://forum.avast.com/index.php?PHPSESSID=9cba7077ccb4b141cbb74cf64a2db104&topic=57775.0)

Mine is
2147483647
but I don't know where it got that number.

---

### Post by blueshiftoverwatch on 2010-04-04
> **Kevbert said:**
> ClamAv/Clamtk
I read an antivirus of various antivirus suites and they rated Clam as one of the worst.

---

### Post by donkyhotay on 2010-04-05
Recurring antivirus forum thread, recurring rootless root forum post:



Master Foo and the Nervous Novice

There was a novice who learned much at the Master's feet, but felt something to be missing. After meditating on his doubts for some time, he found the courage to approach Master Foo about his problem.

“Master Foo,” he asked “why do Unix users not employ antivirus programs? And defragmentors? And malware cleaners?”

Master Foo smiled, and said “When your house is well constructed, there is no need to add pillars to keep the roof in place.”

The novice replied “Would it not be better to use these things anyway, just to be certain?”

Master Foo reached for a nearby ball of string, and began wrapping it around the novice's feet.

“What are you doing?” the novice asked in surprise.

Master Foo replied simply: “Tying your shoes.”

Upon hearing this, the novice was enlightened.

---

