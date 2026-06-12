---
title: "Howto prevent Gnome from messing up your dual-screen setup"
date: 2007-01-26
forum: Outdated Tutorials &amp; Tips
---

### Post by christoph_steinbeck on 2007-01-26
I had set up a dual-screen xorg.conf with an ATI firegl on an IBM T41p which suddenly stopped working. With dual screen, I mean that the gnome desktop spans my two LCD monitor (laptop-built-in and additional one standing right of it).

With "stopped working" I meand that the systems boots until the GDM login screen where the dual screen setup is still ok, but during the login process, the system reverts to a mirrored mode where both screens show the same content.

The reason was that I used System->Preferences>Screen Resolution to switch between two resolutions for testing. That created a respective Key in the Gnome Preferences which, at login, somehow messes up the x-server configuration.

The fix was to use gconf-editor and delete two key under desktop->gnome->screen->0 related to resolution and refresh rate.

Cheers, Chris

---

