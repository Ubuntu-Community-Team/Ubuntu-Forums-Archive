---
title: "Appearances not saving"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by lolwhites on 2008-11-11
I recently installed the Shiki-Colors theme and changed my desktop wallpaper. However, when I log out and back in, it reverts to the old style. I assume this must have something to do with permissions, but which ones, and how do I change them?

---

### Post by Chriss.Hi on 2008-11-12
> **lolwhites said:**
> I recently installed the Shiki-Colors theme and changed my desktop wallpaper. However, when I log out and back in, it reverts to the old style. I assume this must have something to do with permissions, but which ones, and how do I change them?

same problem here (problem since i updated to *hardy*)

---

### Post by Shwefty on 2008-11-12
Just a quick double check, are you running the theme through Emerald Theme Manager?

If you are, you need to set up your System -> Preferences -> Sessions to run the command ```
emerald --replace
``` at start-up.

---

### Post by lolwhites on 2008-11-12
No, I'm not using Emerald. In fact, even if I don't alter the theme and only change the wallpaper, it still switches back when I log back in.

---

### Post by Chriss.Hi on 2008-11-12
works for me now: i completely deleted the ".gconf" folder so all settings were like a new installation. when i now change my settings everything stays as it should stay!

---

### Post by lolwhites on 2008-11-13
I tries Chriss.Hi's solution, but the settings still won't save. What's more, it now starts with the default theme and wallpaper (i.e. Human + the Ibex).

---

### Post by Chriss.Hi on 2008-11-13
yes but what happens when you change the default settings to your shiki-theme?
(about the permission: you have to have all rights for your home folder - check out the properties (permissions tab) of your home folder in nautilus or via terminal)

---

### Post by lolwhites on 2008-11-13
Actually, once I rebooted rather than just logging in and out, it started working properly. Thanks for the tip.

---

