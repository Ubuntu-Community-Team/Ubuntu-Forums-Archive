---
title: "Setting Compiz window rules from code?"
date: 2011-09-07
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-09-07
I'm developing a Python+Qt4 application to work as a panel/launcher/dock for Linux desktop. My primary target environment (what I use and develop on) is Gnome + Compiz on Ubuntu. 

This application needs special window management rules, such as no-decoration, always on top, skip task-bar etc.

Currently I'm using Qt4's own flag system, but it's not as precise as setting Compiz window rules directly. Hence I'm thinking of giving the window rules directly to Compiz, by editing the corresponding Gconf file.

But will that be portable? Does KDE use Gconf? How about other distros, like Fedora? Is there a better way to go about this?

I'm also using Xlib already (to reserve screen space), I guess I may be able to do something with it too, but surely not as in details as with Compiz. Besides X will fall out in the future in favour of Wayland as far as I understood.

Any thoughts / tips?
Thanks

---

