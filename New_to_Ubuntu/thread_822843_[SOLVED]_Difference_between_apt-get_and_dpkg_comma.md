---
title: "[SOLVED] Difference between apt-get and dpkg commands (and aptitude)?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by ravenvii on 2008-06-08
I installed Rainlendar2 from a .deb file. I ended up not liking it (it was a bit unstable, and I found the calendar Screenlet quite adequate), so I went and uninstalled it the way I knew how - apt-get remove --purge rainlendar2.

But I recently read somewhere in the forums that to uninstall software installed from a .deb file (as opposed to from the repositories), I'm supposed to use the dpkg -r command.

But as far as I see, the apt-get remove --purge command worked perfectly, rainlendar2 is gone from my system, and when I tried the dpkg command, it couldn't find any programs named rainlendar2 installed.

I'm wondering what the difference between those two are, and why I should use dpkg over apt-get to uninstall programs installed from a .deb package?

As an aside, I also heard about the aptitude command. Most of the time I see the apt-get command, but once in a while, I see aptitude being used. What's the difference, and which one should I use?

---

### Post by Rocket2DMn on 2008-06-08
apt-get, aptitude, and synaptic are built on top of debian's dpkg package management program.  They all perform the same basic function - package management, but have some extra features.  Synaptic is a nice GUI interface, apt-get is a convenient program for accessing repositories, similar to aptitude.  Aptitude has a semi-GUI inside a terminal with some other useful features, though I don't use it myself.
When you instll .deb packages, they are all stored under dpkg's list and can be controlled by any of these packages management systems, regardless of which one was used to install.

---

