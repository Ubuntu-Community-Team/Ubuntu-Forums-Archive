---
title: "Gnome Shell from ricotz/testing or ricotz/staging"
date: 2011-08-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-08-18
I am not having success installing GS from ricotz repos. When I go to login, there is a longer than usual pause, and then all I get is the desktop - no panels/activities.

What am I missing?

---

### Post by dino99 on 2011-08-18
have been removed

[https://launchpad.net/ubuntu/+ppas?name_filter=ricotz](https://launchpad.net/ubuntu/+ppas?name_filter=ricotz)

but still there if searching about "gnome-shell"

[https://launchpad.net/ubuntu/+ppas?name_filter=gnome-shell](https://launchpad.net/ubuntu/+ppas?name_filter=gnome-shell)

on my side i use genuine repo now

---

### Post by sgage on 2011-08-18
> **dino99 said:**
> have been removed

[https://launchpad.net/ubuntu/+ppas?name_filter=ricotz](https://launchpad.net/ubuntu/+ppas?name_filter=ricotz)

but still there if searching about "gnome-shell"

[https://launchpad.net/ubuntu/+ppas?name_filter=gnome-shell](https://launchpad.net/ubuntu/+ppas?name_filter=gnome-shell)

on my side i use genuine repo now

Genuine repo version works very well for me - that's what I'm running now. It's just that Harry said the ricotz version was running well for him, so I wonder what's up.

---

### Post by Harry33 on 2011-08-18
> **sgage said:**
> I am not having success installing GS from ricotz repos. When I go to login, there is a longer than usual pause, and then all I get is the desktop - no panels/activities.

What am I missing?

True I use Ricotz Staging PPA (not Testing PPA).
I use that on my 64-bit Nvidia-current setup.
And I have upgraded all the packages from PPA .
However I do not need vala. Also Oneiric repos have newer gnome-themes-standard, GTK+3 and glib2.0 packages, so I use the newer ones.

There have never been booting problems with that PPA.
Some days ago I had problems with gobject-introspection, but thta has been fixed now.
So all I can say is, it works.
I haven't tested PPA on my 32-bit setup though.

---

### Post by sgage on 2011-08-18
> **Harry33 said:**
> True I use Ricotz Staging PPA (not Testing PPA).
I use that on my 64-bit Nvidia-current setup.
And I have upgraded all the packages from PPA .
However I do not need vala. Also Oneiric repos have newer gnome-themes-standard, GTK+3 and glib2.0 packages, so I use the newer ones.

There have never been booting problems with that PPA.
Some days ago I had problems with gobject-introspection, but thta has been fixed now.
So all I can say is, it works.
I haven't tested PPA on my 32-bit setup though.

I have tried both testing and staging on my 32-bit system, and the symptom is the same: A long pause after login, followed by the desktop with no panel/activities. Oh well!

---

### Post by Harry33 on 2011-08-18
Just installed the newest gnome-shell and gjs packages from Staging PPA.
64-bit builds are ready now.

So now it depends on the new ABI of libgjs0c and also the newest ABI of evolution-data-server (3.1.5-0ubuntu1).

Working fine.

---

