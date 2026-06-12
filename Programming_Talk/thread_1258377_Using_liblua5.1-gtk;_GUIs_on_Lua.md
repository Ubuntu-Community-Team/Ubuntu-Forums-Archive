---
title: "Using liblua5.1-gtk; GUIs on Lua"
date: 2009-09-04
forum: Programming Talk
---

### Post by kumoshk on 2009-09-04
I've been trying to figure out how to use this package for a long time, but there have been several obstacles.

Which port of GTK to lua is this? There are more than one, and I don't know where to find the documentation if I don't know which one.

Where can I find the documentation for this? How do I actually use it?

Basically, I just want to create GUIs with Lua, and I've decided to try it with GTK. I don't want to use WxLua since it's a pain to install properly on Ubuntu.

If you know any alternate GUI libraries for Lua, please let me know. It would be best if they were cross-platform, though, working on at least Ubuntu, Windows and Mac OS. Unicode support is a must. Support for other Linux distributions would be a plus, but Ubuntu (using Gnome) is the main priority.

---

### Post by kumoshk on 2009-09-05
Okay, I figured this out. It seems that liblua5.1-gtk refers to a previous version of what is now known as LuaGnome. Correct me if I'm wrong on this.

The current version is available, although I don't know why it isn't in the package manager in Jaunty while it is on the Ubuntu website.

The following files are needed for the update (uninstall the old ones and install these in the order listed):
[liblua5.1-gnome-0]("http://packages.ubuntu.com/karmic/liblua5.1-gnome-0")
[liblua5.1-gnome-dev]("http://packages.ubuntu.com/karmic/liblua5.1-gnome-dev")

---

