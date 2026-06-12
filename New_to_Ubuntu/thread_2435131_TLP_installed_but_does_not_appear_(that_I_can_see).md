---
title: "TLP installed but does not appear (that I can see)"
date: 2020-01-16
forum: New to Ubuntu
---

### Post by davepool on 2020-01-16
I read online ([https://www.howtogeek.com/444121/what’s-new-in-ubuntu-19.10-eoan-ermine-available-now/](https://www.howtogeek.com/444121/what’s-new-in-ubuntu-19.10-eoan-ermine-available-now/) under the sub-topic What Didn't Make the Cut) about something called TLP which definitely sounded to me like a "nice to have"...but even though I installed it (per instructions) it doesn't show up in the menu as an app.  Is it something that just works in the background?  With the statement "[COLOR=#404040][FONT=Roboto]TLP provides a wide range of settings for your computer’s subsystems." [/FONT][/COLOR]that sounded to me like something quite user-configurable.

---

### Post by coffeecat on 2020-01-16
From the TLP package description:

> TLP is a pure command line tool with automated background tasks, it does
not contain a GUI.

Try: ```
man tlp
```

Proceed carefully. Another bit of the package description:

> ...  can enable or disable bluetooth, WiFi and WWAN radio devices upon system
startup.

---

### Post by davepool on 2020-01-16
> **coffeecat said:**
> From the TLP package description:



Try: ```
man tlp
```

Proceed carefully. Another bit of the package description:

Thanks, @coffeecat!  You say "proceed carefully"...is that advice to be wary of the tool? I was going by the fact that (reportedly) it had been considered by the Ubuntu team as a "built in" to 19.10 but, ultimately, not added.

---

### Post by coffeecat on 2020-01-16
I have no experience of tlp. My "proceed carefully" was inspired by thinking of something that could disable wifi or other services on system startup. Unintentionally misconfiguring command line utilities is always a possibility.

Have fun! :)

---

