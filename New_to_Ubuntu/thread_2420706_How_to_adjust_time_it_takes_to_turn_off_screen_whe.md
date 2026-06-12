---
title: "How to adjust time it takes to turn off screen when Ubuntu is locked?"
date: 2019-06-09
forum: New to Ubuntu
---

### Post by oottela on 2019-06-09
So e.g., when waking the computer from suspend, there's a 15 second delay until Ubuntu (19.04) turns the screen off again. This is annoying as sometimes it's not possible to login at that same exact moment. How can the delay be increased?

---

### Post by Xian on 2019-06-09
See if this screen lock article is useful:

[https://help.ubuntu.com/stable/ubuntu-help/session-screenlocks.html.en](https://help.ubuntu.com/stable/ubuntu-help/session-screenlocks.html.en)

---

### Post by oottela on 2019-06-10
> **Xian said:**
> See if this screen lock article is useful:

[https://help.ubuntu.com/stable/ubuntu-help/session-screenlocks.html.en](https://help.ubuntu.com/stable/ubuntu-help/session-screenlocks.html.en)

Unfortunately it isn't. The screen lock timeout affects automatic locking when the OS is unlocked. My problem is screens turning off (again) too soon when the OS is woken from suspend (the OS is already locked at that point).

---

### Post by him610 on 2019-06-10
Maybe you can find this one of some use, [https://help.ubuntu.com/stable/ubuntu-help/display-blank.html.en]("https://help.ubuntu.com/stable/ubuntu-help/display-blank.html.en")
or if that doesn't help, here are links to all topics related to Display & Screen, [https://help.ubuntu.com/stable/ubuntu-help/prefs-display.html.en]("https://help.ubuntu.com/stable/ubuntu-help/prefs-display.html.en")
You should be able to figure something out.

---

### Post by oottela on 2019-06-10
[FONT=arial]> **him610 said:**
> Maybe you can find this one of some use, [https://help.ubuntu.com/stable/ubuntu-help/display-blank.html.en](https://help.ubuntu.com/stable/ubuntu-help/display-blank.html.en)
or if that doesn't help, here are links to all topics related to Display & Screen, [https://help.ubuntu.com/stable/ubuntu-help/prefs-display.html.en](https://help.ubuntu.com/stable/ubuntu-help/prefs-display.html.en)
You should be able to figure something out.

The Settings > Power > "Blank screen" is set to 15 minutes, that's not the correct setting. None of the adjustments in normal settings or gnome-tweak-tool seem to do the trick. I also tried CompizConfig Settings Manager and dconf editor but so far found nothing related to this.

I  tried `[/FONT][FONT=arial]gsettings list-recursively |grep 15`

but even that doesn't return relevant settings that have the value. I even tried to grep values close to 15 (seconds) but nothing relevant.
[/FONT]

---

