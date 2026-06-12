---
title: "My drawing tablet won't work"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by Artslave on 2012-06-14
I'm brand-new to linux. 

I've heard that drawing tablets work right out of the box on Linux, but mine doesn't seem to.

I have a Wacom Bamboo Fun (Model #CTH-461) which has touch sensitivity.

I have the original driver disks for the tablet, but I know those wont work, right?

I've also tried to look up drivers in the Unbuntu software center, but I'm afraid that the tech jargon was unintelligible to me and I just got lost and confused.

Any help in finding the correct driver would be greatly appreciated!

---

### Post by Favux on 2012-06-14
Hi Artslave,

Welcome to Ubuntu forums!

What release of Ubuntu are you using?  For e.g. Precise (12.04).  I'm guessing you have a version earlier than Precise installed.  That will help tell us what you need to do to get your BambooPT working.

We'll be following the BambooPT HOW TO:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

---

### Post by Artslave on 2012-06-14
Apparently I am using Ubuntu 10.10

---

### Post by Favux on 2012-06-14
Alright, you have a decision to make.  Maverick (10.10) is no longer supported so it doesn't get updates anymore.  You could keep it anyway or change versions.

If you go back to Lucid 10.04 you have 10 months more of support because it is a long term release.  Natty isn't worth installing because Unity was new so either Oneiric 11.10 (also 10 months more support) or Precise 12.04.  Precise is another LTS (long term support) release, but instead of Lucid's 3 years it is for 5.

With Lucid and Maverick you will need to compile input-wacom for a wacom.ko that works with your tablet.  With Precise it should work out of the box I think.  I forget with Oneiric.

---

