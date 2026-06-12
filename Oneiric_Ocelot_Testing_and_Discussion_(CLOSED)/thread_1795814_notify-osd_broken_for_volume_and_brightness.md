---
title: "notify-osd broken for volume and brightness"
date: 2011-07-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-07-03
testing the netbook I've seen notify-osd is not working correctly for audio and brightness.

when I press volume hotkeys I can see in notifyosd only volume to max and to min, but no intermediate levels. (it changes actually the volume)

when I change brightness from hotkeys instead of showin notify osd with brightness level I see the stock gnome notification in the middle of screen.

probably related to migration of notify osd to gkt3?

---

### Post by perga on 2011-07-11
I have the same problem. Did you report this bug on launchpad?

---

### Post by lucazade on 2011-07-11
> **perga said:**
> I have the same problem. Did you report this bug on launchpad?

no, I was lazy this time :P
anyway now only brightness doesn't work, volume notify-osd is ok.

---

### Post by lucazade on 2011-07-11
maybe this will solve.

notify-osd (0.9.31-0ubuntu1) oneiric; urgency=low

  * New upstream version:
    - use gtk3 (lp: #655232)
  * debian/control:
    - updated the build-depends

Date: Mon, 11 Jul 2011 18:24:23 +0200

---

### Post by Starks on 2011-07-11
this bug: [https://bugs.launchpad.net/unity/+bug/806181](https://bugs.launchpad.net/unity/+bug/806181)

---

### Post by lucazade on 2011-07-11
> **Starks said:**
> this bug: [https://bugs.launchpad.net/unity/+bug/806181](https://bugs.launchpad.net/unity/+bug/806181)

mmmh.. u sure is the correct bug? maybe typo?

---

### Post by Starks on 2011-07-11
no, it's the right bug

---

### Post by lucazade on 2011-07-11
ok, I trust you :)

---

