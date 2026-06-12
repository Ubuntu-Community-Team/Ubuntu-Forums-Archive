---
title: "Install help."
date: 2024-03-05
forum: New to Ubuntu
---

### Post by wamm69 on 2024-03-05
Hi all I'm a complete newbie I have managed to install Ubuntu on my Google pixel 8 and it's working fine but I'm struggling to install the app center I have tried Googling it but can't find one that will work any help would be greatly appreciated.

---

### Post by TheFu on 2024-03-05
App Center?  What's that?  Ubuntu Desktops come with APT as the package manager and there are a few different GUI tools that can be used. Depending on the exact release and exact DE you installed, the name of the package manager would be different.  Look for "Software Center" - that is probably the most common in recent releases.  IDK, I don't use any GUI for software management.

[https://help.ubuntu.com/](https://help.ubuntu.com/) should have everything someone new will need to interact with an Ubuntu Desktop.  Of course, a Pixel isn't really a desktop, so there will be many other challenges.  Most people start using Ubuntu on an x86-64 computer/laptop. There are enough learning challenges on that platform.  Tablets add a whole new layer of complexities, usually best avoided for people new to linux.

---

### Post by ActionParsnip on 2024-03-05
in a terminal, run:
```

sudo apt update
sudo apt full-upgrade

```
Should help

---

### Post by grahammechanical on 2024-03-06
Is this version of Ubuntu actually Ubuntu Touch? It is a version of Ubuntu developed for mobile devices abut discontinued by Ubuntu developers. Development of Ubuntu Touch has been taken over by a group of developers called ubports.

[https://ubports.com/nl/our-story](https://ubports.com/nl/our-story)

You might get better support from the ubports community. I do not think that Ubuntu Touch had an app store because there were few apps developed for this special version of Ubuntu.

I have seen web sites that list some Ubuntu Touch apps.

[https://open-store.io/](https://open-store.io/)

There are other webs sites that offer Android apps and how to install them using something call waydroid.

[https://docs.ubports.com/en/latest/userguide/dailyuse/waydroid.html](https://docs.ubports.com/en/latest/userguide/dailyuse/waydroid.html)

Incidently, I have used waydroid to install and run an Android app on standard Ubuntu running on the wayland compositor.

Regards.

---

