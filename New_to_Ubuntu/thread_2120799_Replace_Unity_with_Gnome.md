---
title: "Replace Unity with Gnome"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by coolecho on 2013-02-27
Hi,

Can the Unity desktop be replaced with Gnome desktop?

---

### Post by audiomick on 2013-02-27
Gnome is, in fact, still there under Unity.

> Unity is a shell interface for the GNOME desktop environment developed by Canonical Ltd for its Ubuntu operating system.

[en.wikipedia.org/wiki/Unity_(user_interface)]("en.wikipedia.org/wiki/Unity_(user_interface)")

What you want, I gather, is a desktop environment that looks like the Gnome DE used to look like. That is not as simple as it sounds, because Gnome itself has moved along too.

> GNOME has evolved from a traditional desktop metaphor to a user interface where switching between different tasks and virtual workspaces takes place in a new area called the overview. The redesigned GNOME features several main changes: released as the new interface for Gnome, GNOME Shell replaces the original GNOME Panel; Mutter replaces Metacity as the default window manager; and the minimize and maximize buttons no longer appear on the titlebar by default. Many of the default GNOME applications have also gone through redesigns to provide a more consistent and unified user experience.

[http://en.wikipedia.org/wiki/GNOME]("http://en.wikipedia.org/wiki/GNOME")

All is not lost, though. 

When you log in, click on the cog wheel icon thing next to the box where you put in your password. At least I think that is where it is. You should be able to choose a different DE that is called something like "Classic". I don't have a 12.04 or 12.10 install yet, so I don't know for sure how to get there, but I know it is there.

You can also install other DEs from the software center an try them out. Choosing them, once they are installed, is the same procedure as choosing the "classic" instead of Unity. They appear for selection in the same list.

I have a number of positive comments about the XFCE desktop from those who don't like Unity. That can be installed by itself, or you can install the Xubuntu desktop package. The Lubuntu desktop might be of interest to you as well.

---

### Post by Vegabondsx on 2013-02-27
You can install GNOME Shell or GNOME Fallback (Classic Gnome) from Apt.

Gnome Shell:

```
sudo apt-get install gnome-shell
```

Gnome Fallback/Classic:

```
sudo apt-get install gnome-session-fallback
```

Once you've installed what you want, you can log out and click on the session icon (next to your name) to change what you'll use. You can always switch back this way.

---

### Post by kurt18947 on 2013-03-01
In addition to what Vegabondsx said,  there is something called MATE.  It is a desktop intended to mimic gnome2 but runs on supported gnome3.  I've installed it with Mint 13 to try it out.  It seems to work and the menus etc. seem pretty close to gnome2.  Xfce4 is easy to install from the repository and has a 'traditional' desktop design.  Xfce4 is not 'pretty' installed on Ubuntu 12.x but it seems to function well.

---

