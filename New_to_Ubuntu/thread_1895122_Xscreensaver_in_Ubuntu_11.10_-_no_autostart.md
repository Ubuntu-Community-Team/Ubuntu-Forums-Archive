---
title: "Xscreensaver in Ubuntu 11.10 - no autostart"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by Pasacom on 2011-12-14
Hey guys,

This is my first post in this forum, so please go easy on me.  ;-)

I'm running ubuntu 11.10. I **uninstalled gnome-screensaver** and **installed xscreensaver** instead. It's working fine except for it won't autostart after re-boot. So I always have to start it manually. It is listed in the autostart setup application! 
What should I do? :confused:

---

### Post by Testingte on 2011-12-14
In startup applications, what do you have it listed as?

It didn't work for me either 'till I set the startup application command to "xscreensaver -nosplash" (without quotes obviously)

---

### Post by Pasacom on 2011-12-14
Thanks a lot Testingte!
Believe it or not, I had "xscreensaver -no**n**splash" in there. One letter makes all the difference.
Thanks again. It's working now!

---

### Post by Testingte on 2011-12-14
It really does! Lol.

Glad I helped you out! :D

---

