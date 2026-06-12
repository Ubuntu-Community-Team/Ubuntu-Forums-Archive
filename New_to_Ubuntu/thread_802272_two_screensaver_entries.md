---
title: "two screensaver entries"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by dgbearcat on 2008-05-21
So, a friend recommended that I install the xscreensaver package, which I did. It has some really cool options, and I'd like to keep it.

However, now, under system->preferences, I have two entries for screensaver: ones is the new one, one is the one that was originally with ubuntu. Any idea what the name of that is so I can get rid of it from the terminal?

Thanks

Actually, one other question: on the new interface, I see a whole bunch of screensavers that I don't actually have. I don't see anything in the documentation that tells me how to get them. How to I update the package to include them?

EDIT: never mind, found the answer here...[http://www.linuxquestions.org/questions/debian-26/xscreensaver-missing-screensavers-636141/](http://www.linuxquestions.org/questions/debian-26/xscreensaver-missing-screensavers-636141/)

---

### Post by civillian on 2008-05-21
The default screensave settings app that comes with ubuntu is gnome-screensaver however this may be tied in to all the other gnome-xxxx apps, and as such may not be removeable (i don't know; havent tried). However, if you want you can remove it's entry from the menu using the menu editor (right click on the menu launcher and select edit)

I appreciate that this doesnt apply to this app, but generally if you open both and click on the help tab then select about (or similar) it should give you the name and version number so you can apt-get remove it, or remove it via synaptic.

Hope this helps! and apologies if I was too vague...

---

