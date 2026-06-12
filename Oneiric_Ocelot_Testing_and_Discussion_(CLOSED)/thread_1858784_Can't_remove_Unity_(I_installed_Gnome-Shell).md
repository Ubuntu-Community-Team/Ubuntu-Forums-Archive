---
title: "Can't remove Unity? (I installed Gnome-Shell)"
date: 2011-10-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 8_Bit on 2011-10-13
I installed GNOME Shell in a fresh install of Oneiric.

Then I tried removing Unity.

It tells me doing so will also remove gnome-session.

Are you kidding me?

Is it possible at all to purge Unity from my hard drive while keeping Gnome 3 and Gnome-Shell?

[edit] Another question. About proprietary drivers.
In the "Additional Drivers" window, I see the following two listed:

"ATI/AMD proprietary FGLRX graphics driver (**post-release updates**)"
and
"ATI/AMD proprietary FGLRX graphics driver"

Do I install both of these?

---

### Post by Harry33 on 2011-10-13
> **8_Bit said:**
> I installed GNOME Shell in a fresh install of Oneiric.

Then I tried removing Unity.

It tells me doing so will also remove gnome-session.

Are you kidding me?

Is it possible at all to purge Unity from my hard drive while keeping Gnome 3 and Gnome-Shell?

Yes it is.
The only package you need to keep is libunity6. Do not ask me why, it is of no use either with gnome-shell and gnome-panel.
Anyway, nautilus depends on it.

---

### Post by lolpenguin on 2011-10-13
Well, Canonical is persistent on Unity, and you won't be able to remove it...quite annoying for those who prefer the gnome-panel.
As for the proprietary drivers, I think you should install both, but it's most likely safe to experiment with them.
EDIT: If you proceed with the unity uninstallation, if gnome-session is removed, you wont be able to boot into Gnome Shell, Gnome Classic, nor Unity. If a removal of unity is possible without breaking essential components I do not know about it. Personally, I have no objection against Unity though.

---

### Post by Harry33 on 2011-10-13
> **lolpenguin said:**
> Well, Canonical is persistent on Unity, and you won't be able to remove it...quite annoying for those who prefer the gnome-panel.
As for the proprietary drivers, I think you should install both, but it's most likely safe to experiment with them.
EDIT: If you proceed with the unity uninstallation, if gnome-session is removed, you wont be able to boot into Gnome Shell, Gnome Classic, nor Unity. If a removal of unity is possible without breaking essential components I do not know about it. Personally, I have no objection against Unity though.

Unity can be removed, the only library package that cannot be removed is, like I said above, libunity6.
As for the package gnome-session, it is a dependency of Gnome-shell and should not be removed. You start the Gnome-shell session by choosing gnome-session.

I have three setups, where Gnome-shell and Gnome-panel (the fallback) are the only shells installed, so no Unity (3D nor 2D) there.

---

