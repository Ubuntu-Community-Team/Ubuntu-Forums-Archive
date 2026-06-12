---
title: "Problem Removing Mouse Gestures Redox 3.0.3 in FF"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by derrickr on 2011-09-28
I found Mouse Gestures Redox 3.0.3 was causing problems in FireFox with an approximate 5 second delay before mouse contexts showed up.

I've managed to work round the problem by upgrading to the latest version of FF, which Mouse Gestures Redox 3.0.3 is thankfully (for me) incompatible with.

However, I now have the annoying problem  of it still be shown under the Add-ons Manager, but doesn't have a  remove button.

I've looked around the .mozilla directory but can't find anything that directly effects this, even after removing the 'mozgest3' directory.

I'd appreciate any pointers regarding how to completely remove it.

---

### Post by derrickr on 2011-09-28
Thought I'd have a look inside the Package Manager and lo & behold, there was mouse gestures!

I found it a little strange that a FF extension was installed as an Ubuntu package, but at least I found it.

I then easily managed to remove it :D

---

