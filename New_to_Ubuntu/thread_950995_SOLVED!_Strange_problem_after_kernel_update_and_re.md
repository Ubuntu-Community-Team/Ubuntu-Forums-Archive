---
title: "SOLVED! Strange problem after kernel update and reinstalling drivers with Envy"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by oldrocker99 on 2008-10-17
This might help newbies and others...

I have had some problems with Gnome (like all my drives vanishing from the /etc/fstab file:confused:), so I started using KDE, which is a little annoying after Gnome, but at least showed the drives.

There was a kernel update and I (naturally) reinstalled the nVidia drivers with Envy. I rebooted and the KDE screen was squeezed toward the left side of the screen, leaving a black band about 1.25" on the right side of the screen. I was baffled, especially when I booted into Gnome and the screen was fine. I had a brainstorm and booted back into KDE and ran displayconfig-gtk. Sure enough, a generic nVidia card was shown. I selected the 8000 series (I have an 8600), logged out, and all is fixed.

This might happen to you. If you don't already have displayconfig-gtk, you should get it--it can be very handy.

:guitar:

---

