---
title: "Just checking, reinstall with home partition already set up."
date: 2008-11-11
forum: New to Ubuntu
---

### Post by barbedsaber on 2008-11-11
Just double checking, If I reinstall, and during install, get my current ubuntu partition to format, and be mounted at /, and my current home partition to be mounted at /home, and not formated, all my current config files will still be there?

On a side note, I need to fsck home manually, because fsck has been failing, because I resized my home partition. So, in a livecd I ran ```
fsck /media/sda2
``` and I tried with -p, but nothing seems to have happened. How do I do this?

---

### Post by bumanie on 2008-11-11
Hi barbedsabre,
I always do manual partitioning on a new installation how you are proposing - works fine. You will find the installer will want to format swap too - but that's no problem :) - just make sure /home is not set for a format and everything should be fine.

---

