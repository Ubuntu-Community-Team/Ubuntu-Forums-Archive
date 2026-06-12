---
title: "Gconf issues"
date: 2008-02-18
forum: Packaging and Compiling Programs
---

### Post by interval1066 on 2008-02-18
I'm in the middle of writing my first gnome application and so far its been pretty good, I've been able to solve every problem I've come across until now. I'm having issues with Gconf. My application is written using the gtkmm wrappers, and I'm at a point now where I need to write my user prefs object. I so after doing the usual research I came to understand I needed to use gconfmm. So after the usual installation messing about I still had failure. Although the header <gconfmm.h> is most deffinately present in my system (in a directory ../gconfmm-2.6) I can't get the autotools to find it. After more mucking about including creating a symlink to "../gconfmm2.6 <- ../gconfmm" and installing anything having to do with gconf I gave up and decided to write my own wrapper around libgconf. But after a week of screwing with it still no joy. My project can't find gconf/gconf-client! I found gconf-sanity-check-1 & 2 (I found 2 in /usr/lib/gconf2-4), but running them produced no output. How do you use this junk?? I do not relish the idea of duplicating the code by writing my own preference mgmt object as this will mean my app won't have awareness of the gnome env, but that's where I'm headed I guess.

---

### Post by interval1066 on 2008-02-19
Since I can't find any further information on these problems I've decided to write my own preferences handler. I don't have time to screw around. Interestingly the version of libxml that installs with both feisty and gutsy give me the exact same problem, but the latest libxml2 seems to work ok. If anyone has any experience writing to the gnome configuration manager though it would be nice to read about those experiences.

---

### Post by interval1066 on 2008-02-19
Finally figured out the key to everything. Damn autoconf.

---

