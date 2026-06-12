---
title: "Why wxWidgets naming change?"
date: 2016-03-24
forum: Packaging and Compiling Programs
---

### Post by pyth0n on 2016-03-24
Hi!

Why did Ubuntu change wxWidgets submodules naming? Old was like libwxgtk3.0-0, new is like libwxgtk3.0-0v5. This breaks 3-rd party software...

---

### Post by mc4man on 2016-03-24
Actually it was from Debian as part of gcc5 transistion - 
> wxwidgets3.0 (3.0.2+dfsg-1.1) experimental; urgency=medium

  * Non maintainer upload.
  * Rename library packages, follow-up for the libstdc++6 ABI transition.
    Addresses: #791311.
  * Add Breaks/Replaces to the old library packages.

 -- Matthias Klose <doko@debian.org>  Thu, 30 Jul 2015 13:26:47 +0200
If you have concerns file a bug with Debian & link it in a Launchpad bug

---

