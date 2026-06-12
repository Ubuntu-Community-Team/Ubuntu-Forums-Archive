---
title: "iBus icon not seen in top panel"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by Milind on 2011-10-14
I upgraded from Ubuntu 11.04 to 11.10 today, and the iBus icon is no longer visible in the top panel. iBus works, and in its settings, "Show icon in system tray" is selected.

How can I get the icon back?

---

### Post by jtarin on 2011-10-14
You can look [here]("http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html") for guidance to recover your icon. Choose the most appropriate scenario for your situation.

---

### Post by Milind on 2011-10-14
> **jtarin said:**
> You can look [here]("http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html") for guidance to recover your icon. Choose the most appropriate scenario for your situation.

@jtarin : Thanks for the help. I tried this from the terminal as that site advised:

*gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"*

and it solved my problem.:P

---

### Post by jtarin on 2011-10-14
Glad to hear your problem is solved. Happy to help.:p

---

