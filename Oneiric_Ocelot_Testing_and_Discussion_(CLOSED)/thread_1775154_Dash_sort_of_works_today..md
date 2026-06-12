---
title: "Dash sort of works today."
date: 2011-06-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lan3y on 2011-06-04
after performing some updates this morning and logging in to unity, dash seems to be working, although there is a bug that it seems to 'stick' to my desktop background, (which is black at the moment).

another strain is that the 'disable mouse while typing' option seems to be going on way too long (about 2 seconds after i finish typing).

anyone else experiencing anything like this?

lan3y

---
edit: this is what happens to my desktop (hope this isn't a feature imported from windows :P)

[http://imageshack.us/photo/my-images/6/screenshotmp.png/](http://imageshack.us/photo/my-images/6/screenshotmp.png/)

---

### Post by fluteflute on 2011-06-04
> **lan3y said:**
> this is what happens to my desktop (hope this isn't a feature imported from windows :P)

[http://imageshack.us/photo/my-images/6/screenshotmp.png/](http://imageshack.us/photo/my-images/6/screenshotmp.png/)
That's a known bug. To get around it then set yourself a new Desktop background :)

---

### Post by _oOMOo_ on 2011-06-04
Syndaemon is set to 2 seconds (Lord alone knows why). I had a dig around to find out where this is set but not uncovered it yet, but in the meantime

```
killall syndaemon; syndaemon -i 0.8 -K -R &
```

sets it back to 0.8 seconds. Let me know if you find the config option :)

---

### Post by wildmanne39 on 2011-06-04
Hi, is there a work around for dash? mine still does not work and I have installed the updates. Thanks for any help, I appreciate it.

---

