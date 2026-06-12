---
title: "Adjusting Autologin?"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by Greg Mueller on 2011-10-16
If I use autologin it runs a different version of 11.10 (the cartoon version) than if I manually login and choose Gnome Classic.

Is there a way to adjust autologin to choose Gnome Classic?

---

### Post by Greg Mueller on 2011-10-16
[SIZE="3"]Found this fix.....[/SIZE]

[I]If you enable auto log-in in Ubuntu 11.10 Oneiric, it automatically logs into Unity. Some people installed gnome-shell Gnome 3 desktop and want Ubuntu auto log into gnome-shell. Normally, we first disable auto log-in behavior, log out and back into gnome-shell, and finally in Gnome 3 desktop enable auto log-in again.

Unfortunately, this settings doesn’t work for me, but I found a command-line solution (from Ubuntu forum):

To make Ubuntu 11.10 auto log-in gnome-shell, open up a terminal window and run this command:[/I]
[B]
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell[/B]
[I]
If you want to change back to Unity, run:[/I]

**sudo /usr/lib/lightdm/lightdm-set-defaults -s ubuntu**



[http://ubuntuguide.net/ubuntu-11-10-how-to-auto-login-gnome-shell-gnome3-desktop]("http://ubuntuguide.net/ubuntu-11-10-how-to-auto-login-gnome-shell-gnome3-desktop")


:)

---

