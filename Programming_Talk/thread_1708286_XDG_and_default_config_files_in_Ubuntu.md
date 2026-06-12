---
title: "XDG and default config files in Ubuntu"
date: 2011-03-16
forum: Programming Talk
---

### Post by LemursDontExist on 2011-03-16
Hi,

I'm writing an application in python which has a couple configuration files; up to now, I've been using the xdg.BaseDirectory module to decide where to put files.  For the config dirs, I get:

```
>>> xdg.BaseDirectory.xdg_config_dirs
['/home/julian/.config', '/etc/xdg/xdg-gnome', '/etc/xdg']
```

and so initially I was going to install the default config files to /etc/xdg, and, if the user modifies the settings, create a modified copy in the ~/.config folder.  However, when I look in my own system's /etc/xdg folder, it is nearly empty (and /etc/xdg/xdg-gnome doesn't exist), and it seems as if most applications in Ubuntu install their configuration files directly to /etc.

So!  Am I misinterpreting the xdg spec?  Is there a better standard to use for Ubuntu?  I haven't been able to find any real indication of what's conventional (and am beginning to understand why linux filesystems are such a mess!)  If I want my program to be usable across linux distributions, what's the best practice?

---

### Post by LemursDontExist on 2011-03-18
BUMP!

Also, does anyone know of a better place to ask questions like this?  I haven't had much luck getting answers to questions on this Forum (I think maybe my questions have been a little too specialized), and it would be nice to know a place where I can find answers!

I'm a pretty reasonable programmer so my questions mostly have to do with application development standards and practices on Linux (rather than how to program).  Does anyone know a forum dedicated just to that?

---

