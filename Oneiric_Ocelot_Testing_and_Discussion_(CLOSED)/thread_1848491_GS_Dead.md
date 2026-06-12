---
title: "GS Dead"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sammiev on 2011-09-22
Todays updates killed GS to no end. I can not even reinstall GS as it said libraries are missing. :( Hope to see a fix soon.

---

### Post by Harry33 on 2011-09-22
> **sammiev said:**
> Todays updates killed GS to no end. I can not even reinstall GS as it said libraries are missing. :( Hope to see a fix soon.

Perhaps you have installed one of these packages today: libclutter0, libmutter0, libcogl5.

New clutter (libclutter0_1.8.0-1) and mutter (libmutter0_3.1.92) depend on libcogl5 instead of old libcogl2. This is why you cannot install them now or else, gnome-shell is removed. Gnome-shell must also be build against libcogl5. And that build is now waiting for caribou (gir1.2-caribou-1.0, libcaribou0) to be build.
So, just wait.
This is for people using Gnome-shell from Oneiric repos only.

---

### Post by paul_in_london on 2011-09-22
> **Harry33 said:**
> Perhaps you have installed one of these packages today: libclutter0, libmutter0, libcogl5.

New clutter (libclutter0_1.8.0-1) and mutter (libmutter0_3.1.92) depend on libcogl5 instead of old libcogl2. This is why you cannot install them now or else, gnome-shell is removed. Gnome-shell must also be build against libcogl5. And that build is now waiting for caribou (gir1.2-caribou-1.0, libcaribou0) to be build.
So, just wait.
This is for people using Gnome-shell from Oneiric repos only.

Ok here actually, but I'm using the ricotz ppa.

---

### Post by Harry33 on 2011-09-22
> **paul_in_london said:**
> Ok here actually, but I'm using the ricotz ppa.

Yes this problem does not concern Ricotz Testing PPA.
The soname bumb was there earlier and all is well there now.

---

