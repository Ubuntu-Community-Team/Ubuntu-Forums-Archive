---
title: "GTK+3 in Ricotz PPA breaks Gnome-shell"
date: 2011-09-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-09-14
The newest GTK+3 build of today (3.1.90-0ubuntu1~11.10~ricotz0) in the Rocotz Testing PPA breaks gnome-shell.
Upgrading to this version makes my system boot into the fallback session (gnome-panel).
Then, downgrading to the official Oneiric version (3.1.8-0ubuntu3) solves the issue.

---

### Post by sgage on 2011-09-14
> **Harry33 said:**
> The newest GTK+3 build of today (3.1.90-0ubuntu1~11.10~ricotz0) in the Rocotz Testing PPA breaks gnome-shell.
Upgrading to this version makes my system boot into the fallback session (gnome-panel).
Then, downgrading to the official Oneiric version (3.1.8-0ubuntu3) solves the issue.

Hmmm... that version is working fine here. (I should mention that I'm back to a 32-bit installation.)

---

### Post by Harry33 on 2011-09-14
In Ricotz Testing PPA a number of packages are being updated now.
This may be because of the new GTK+3 3.1.90.

---

### Post by sgage on 2011-09-14
> **Harry33 said:**
> In Ricotz Testing PPA a number of packages are being updated now.
This may be because of the new GTK+3 3.1.90.

I just upgraded the whole batch at 5:00 EDT (US), and having logged out/in, all seems to be ticking along smoothly.

---

### Post by jjcv on 2011-09-14
All working fine here after and update on a 64bit system.

---

### Post by Harry33 on 2011-09-15
Same here, the newer mutter did solve this issue for me.
Marking this as solved now.

GTK+3 v. 3.1.90 is already in Oneiric repos.
New versions of mutter and gnome-shell (3.1.91.1) are in Ricotz PPA now.

---

