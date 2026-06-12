---
title: "Window management in Unity"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by chlorox on 2011-10-01
I seem to have lost window management ability in Unity. It works just fine in Gnome-shell. I have attempted unity --reset several times. I can launch apps and they just hug the upper left. I can't move them or maximize them.

Any ideas?

---

### Post by effenberg0x0 on 2011-10-01
Hey,

Inside ccsm (CompizConfig-Settings-Manager), which is available with apt-get, you have some plugins that might help. You can disable snap to edges, work with windows positioning, maximize/minimize, rules for fixed positions and sizes, among many other changes. It's not very stable (it might crash as you activate or deactivate plugins), but it's what everyones else uses to customize the desktop now.

Regards,
Effenberg

---

### Post by VinDSL on 2011-10-01
> **chlorox said:**
> Any ideas?
I've had this happen, a couple of times, recently.

This-or-that update cycle disables the Unity Plugin.

As effenberg0x0 said, your next-step should be going into CCSM and scoping things out.

It *might* be as simple as re-enabling the Unity Plugin...  ;)

If that doesn't work, you might want to wash, rinse and restyle the Compiz modules.

---

### Post by chlorox on 2011-10-01
Oh I have to manually re-enable that plugin every time I reboot these days. Something is conflicting.

What's happening here, is most window chrome is missing. The title bar, which is typically acts as the handle.

When I log out, and then back in, it's all disabled again, and I get the Nautilus desktop. (Just a menu at the top.)

---

