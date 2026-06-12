---
title: "Strange problem with IDLE: cannot see underscores!"
date: 2008-05-29
forum: Programming Talk
---

### Post by svk on 2008-05-29
Hello,

I have an annoying problem with IDLE.  For some reason, it eats a couple lines of pixels from every line of code.  For example, I cannot see the tails on letters like "p" and "y"; but worst of all, I cannot see underscores.  In more technical terms, I cannot see anything below the [baseline]("http://en.wikipedia.org/wiki/Baseline_%28typography%29").  This occurs in both the interactive shell window and all non-interactive code windows.

Very, very strange!

Here's more info about my system: I'm using Hardy Heron, my graphics card is an NVidia Go 6150, I have python 2.5 and IDLE 1.2.2 installed, this happens regardless of whether advanced desktop effects are turned on or not, and this was also a problem in Gutsy.  I'm not sure what this is related to, so I don't know what other information to provide; but I'll be happy to share whatever is needed upon request.

Thank you in advance for any help!

---

### Post by amingv on 2008-05-29
Weird indeed.
I went through the trouble of installing IDLE and noticed it only happens with some fonts (like courier) when they're in font size 10 or 18.
Going to Options>Configure IDLE and changing the font/size values might be a temporary fix.

---

### Post by svk on 2008-05-29
Yes, switching to size 9 instead of 10 fixed the issue.  Not sure what's up with this, but I'm quite relieved nevertheless.

---

