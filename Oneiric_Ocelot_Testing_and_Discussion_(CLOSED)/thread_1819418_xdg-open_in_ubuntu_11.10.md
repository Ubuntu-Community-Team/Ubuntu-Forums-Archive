---
title: "xdg-open in ubuntu 11.10?"
date: 2011-08-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by hakermania on 2011-08-06
As it seems there's not xdg-open in 11.10.
What should we use instead?

---

### Post by kerry_s on 2011-08-06
gnome-open

---

### Post by jbicha on 2011-08-06
Short answer: Install gvfs-bin

Longer answer: gnome-open used to be provided by libgnome which is deprecated and therefore is no longer on the Oneiric CD. gvfs-open is the replacement and is used by xdg-utils; you're getting the error because neither gvfs-open or the fallback, gnome-open are installed. This was reported as [http://pad.lv/804397](http://pad.lv/804397) and gvfs-bin will be added to xdg-utils' recommends soon.

---

### Post by hakermania on 2011-08-07
So, finally, because you confused me, what command should I use (no dependencies please :) )?

---

### Post by jbicha on 2011-08-07
If you're writing a script or program or whatever, you should continue to use xdg-open.

If you're using Ubuntu 11.10, you'll need to install gvfs-bin for xdg-open to work like it's supposed to. That's a bug because xdg-open is a standard and should just work. That bug will be fixed soon.

---

### Post by hakermania on 2011-08-07
> **jbicha said:**
> If you're writing a script or program or whatever, you should continue to use xdg-open.

If you're using Ubuntu 11.10, you'll need to install gvfs-bin for xdg-open to work like it's supposed to. That's a bug because xdg-open is a standard and should just work. That bug will be fixed soon.
So this mean that before the official natty release this bug should be fixed....!?

---

### Post by jbicha on 2011-08-07
The bug will definitely be fixed before Ubuntu 11.10 beta.

---

