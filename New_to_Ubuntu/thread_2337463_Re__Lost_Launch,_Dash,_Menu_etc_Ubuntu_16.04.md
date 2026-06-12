---
title: "Re:  Lost Launch, Dash, Menu etc Ubuntu 16.04"
date: 2016-09-18
forum: New to Ubuntu
---

### Post by cressrt2 on 2016-09-18
The machine was running slow so I rebooted and all above was missing. I boot direct into Ubuntu. I did run updates recently and this was the first restart since so there may have been an update causing it, I have searched and tried as many solutions as possible but to no avail.
I am able to access the internet through a shortcut that I happened to have on the desktop.
I am at a loss now other than a clean install, any suggestions?

Managed to amend log in from auto, and the guest account is working OK, so I assume I need to reset/delete/restore something on the main account?

---

### Post by yetimon_64 on 2016-09-18
> **cressrt2 said:**
> Managed to amend log in from auto, and the guest account is working OK, so I assume I need to reset/delete/restore something on the main account?

The commands shown in [[COLOR=#0000ff]--this post-- [/COLOR]]("https://ubuntuforums.org/showthread.php?t=2321539&p=13475273#post13475273") should help you reset the unity plugin which controls the launcher, dash, and so on. That post from a staff member here, deadflowr, also shows how to get a terminal up if the keyboard bindings are no longer working. Hope that can help you a bit. yeti.

---

### Post by cressrt2 on 2016-09-19
No difference, it did not work, any other suggestions?

Specifically this:
unity-panel-service stop/waiting
unity stop/waiting
unity-panel-service stop/waiting ,process 2834
unity start/running ,process 2951

then nothing more!

As there was no solution that I could make work, I created a new Admin, ensured all worked and then deleted the old account.

---

