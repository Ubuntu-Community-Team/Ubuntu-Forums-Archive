---
title: "How to re-enable new mail notifications"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by mujaheiden2 on 2013-10-14
Hi,

I disabled my new mail notification bubbles in 12.04, but on second thought, i would like to re-enable them, as just the blue envelope isnt doing it for me, but no idea where the setting is stored?

Sorry for being such a n00b....

---

### Post by slickymaster on 2013-10-14
Hi mujaheiden2, welcome to the forums.

You can use a GUI tool called "dconf-editor" to re-enable it```
sudo apt-get install dconf-tools
```Once installed open a terminal window and run```
dconf-editor
```then navigate to desktop > unity > panel and enable it  the Notification Area (Systray)

---

