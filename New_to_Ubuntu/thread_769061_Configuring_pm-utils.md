---
title: "Configuring pm-utils"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Kralnor on 2008-04-26
Howdy!

I am running 7.10 Gutsy and have been trying to use the default power management app that was bundled with the OS to make the box suspend and/or hibernate, but because of having some issues with resuming USB devices the OS did a proper shutdown when trying to resume.

However, I installed pm-utils and sudo pm-hibernate seems to work flawlessly.

Now my question is, how do I configure pm-utils to make the box go into hibernation after having the desktop idle for a certain amount of time?

---

### Post by cillian.deroiste on 2008-05-12
I've been having no luck with s2disk or s2ram or anything so I'm looking forward to trying this out. I use it on a gentoo box so I should have thought of it myself, so thank you!

Have you found gnome-power-preferences already? That lets you configure things like hibernating automatically after a certain time of inactivity. It should be in the menu under System/Preferences/Power Management.

You should also be able to configure things so that you can hit the hibernate button and it will use pm-hibernate. If I figure it out I'll post here.

---

### Post by Kralnor on 2008-05-12
I upgraded to 8.04 Heron a week ago and now gnome-power-management seems to work just fine.

However, I did need to install the official Ubuntu supported nVidia drivers package by running

```

sudo apt-get install nvidia-glx-new linux-restricted-modules-$(uname -r) --reinstall

```

---

