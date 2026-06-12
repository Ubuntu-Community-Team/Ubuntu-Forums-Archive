---
title: "apt-get -b source, version number, and upgrading"
date: 2007-04-25
forum: Packaging and Compiling Programs
---

### Post by strider1551 on 2007-04-25
Hey all,

I posted this the other day in the general help forum, and then today I randomly stumbled into this subforum and thought "wow, I wish I had noticed this yesterday."  Oh well...

After reading this, I made myself a quick python script to recompile whatever package I tell it so that I can have the benefit of things being compiled for my specific hardware. After recompiling a few things I came across an interesting problem. The update manage will pester me to upgrade some of the packages but not others.

For example, I recompiled gedit and spe. The update manager wants me to upgrade spe to the same exact version, but doesn't mention gedit. I looked in synaptic and looked at the versions available under the properties of spe:

```

0.8.2a+repack-1 (feisty)
0.8.2a+repack-1 (now)

```

Gedit only lists a feisty version, not a "now" version.

Anyone know what's going on?

---

### Post by strider1551 on 2007-07-22
I'm still having this problem, so I'm going to dig this thread out of the grave.  Nothing has changed in the past few months; gedit builds from source just fine, while gnome-terminal wants to "upgrade".

If you wish to follow in my footsteps:
```

sudo -i
mkdir ~/tmp
cd ~/tmp
apt-get build-dep -y gnome-terminal
apt-get -b source gnome-terminal
dpkg -i *.deb
cd
rm -r ~/tmp
exit
```

I think I might see if there's a way for me to change the version (2.18.0-0ubuntu1 => 2.18.0-1ubuntu1).  That's not the solution I want, but I think it would work...

---

### Post by strider1551 on 2007-07-29
Wow, I think I actually figured out a work around. Edit /etc/apt/preferences and add:

```
Package: *
Pin: release a=now
Pin-Priority: 999
```

This seems to have solved everything for me, not that anyone else has taken notice of this thread.  Now that I have this solved I plan on making a nice little gui to compile packages.  I'm afraid someone will actually have to show interest in that before I post a link to it someday.

---

