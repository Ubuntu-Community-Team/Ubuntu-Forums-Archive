---
title: "HOWTO- Fix USB auto-mount issues on boot"
date: 2007-02-03
forum: Outdated Tutorials &amp; Tips
---

### Post by dcstar on 2007-02-03
There is a known problem where the desktop starts up too quickly before things like the HAL are ready, and this stuffs up things like USB drive mounting (where the gnome-volume-manager isn't started), this solution has fixed my Edgy Gnome system and may well be of help to others with this issue.

I had disabled auto-login and replaced it a 5 second timed-login (which solved the problem), but I subsequently found this to be a better solution:

   1. Leave Auto-login enabled
   2. Edit **/etc/default/rcS** and set the relevant line to: "**DELAYLOGIN=YES**"

This delays certain login processes until previous ones have completed, and seems to ensure that (on my system, at least) that my USB stick drive is mounted and available on every boot-up.

This fix should be desktop environment independent, so it should work on non-Gnome environments as well.

---

