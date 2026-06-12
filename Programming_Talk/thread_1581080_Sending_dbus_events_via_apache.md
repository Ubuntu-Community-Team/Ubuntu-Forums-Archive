---
title: "Sending dbus events via apache"
date: 2010-09-24
forum: Programming Talk
---

### Post by BlueWolf_ on 2010-09-24
I'm a complete newby with dbus so I wanted to figure out how I could use it. I have Apache with Python running locally and I wanted to make a webpage where I could remote control Rhythmbox and many more programs that use dbus.

I know python has a dbus-module but I wanted to begin as simple as possible. I found a single command using qdbus which would pause Rhythmbox.

```
qdbus org.gnome.Rhythmbox /org/gnome/Rhythmbox/Player org.gnome.Rhythmbox.Player.playPause boolean:True
```

And it works when I run in from the terminal. So got Python to execute this command when I access the page but nothing happens. qdbus reports:

> D-Bus server: org.freedesktop.DBus.Error.Spawn.ExecFailed: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

I'm not sure, but I guess this has something to do with the script running under a different (apache) user? How should I use dbus when it should access a resource from a different account? Documentation seem to be scattered all over the place :(

---

### Post by BlueWolf_ on 2010-09-25
Bump. Still haven't figured it out.

But I did find out that simple executing 'qdbus' from an other account or a headless server results in the same error. Does dbus needs to have a GUI? Does that mean that servers don't use dbus? :S

---

