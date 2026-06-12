---
title: "Booting a full screen application from startup"
date: 2008-10-27
forum: Programming Talk
---

### Post by compeee2008 on 2008-10-27
Hi,

I was wondering how would boot up a software application from startup. When the machine boot up, the initialization process screen does not display anything and the login screen is disabled but instead launch a software in full-screen say mozilla.

---

### Post by dribeas on 2008-10-27
> **compeee2008 said:**
> Hi,

I was wondering how would boot up a software application from startup. When the machine boot up, the initialization process screen does not display anything and the login screen is disabled but instead launch a software in full-screen say mozilla.

There are a couple of ways of doing it. Probably the simplest is configuring gdm to autologin with a predefined account and having a .Xclients script that just launchs mozilla

```

#!/bin/sh

mozilla # parameters for fullscreen

```

There are other solutions, just google for mozilla/firefox kiosk and you will probably find what you want.

---

