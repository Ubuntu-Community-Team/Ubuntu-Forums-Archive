---
title: "gnome terminal not load"
date: 2014-06-07
forum: New to Ubuntu
---

### Post by m.riz on 2014-06-07
when i select gnome terminal i wont load.
and i type gnome-terminal in xterm it gives follows
> Error constructing proxy for org.gnome.Terminal:/org/gnome/Terminal/Factory0: Error calling StartServiceByName for org.gnome.Terminal: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/gnome-terminal/gnome-terminal-server exited with status 1 
how to fix this

---

### Post by Elmer Fudd on 2014-06-07
What are Ubuntu and desktop versions?

---

### Post by m.riz on 2014-06-07
sorry i forget to post that :D
ubuntugnome 14.04 lts 64 bit

gnome 3.12.2

---

### Post by m.riz on 2014-06-10
bump

---

### Post by tgalati4 on 2014-06-10
Try to run *xterm* or *uxterm* and see what happens.

Alt-F2 xterm
or
Alt-F2 uxterm

---

### Post by m.riz on 2014-06-11
xterm or uxterm are running well

---

### Post by tgalati4 on 2014-06-11
xterm uses simple X-Windows commands and not the Gnome Took Kit (gtk), so it appears that your gnome installation is broken in a subtle way.

Let us first check if it is a permissions problem:

```
gksudo gnome-terminal
```

If that works then somehow a permission got changed in a gnome library that is now interfering with a normal user trying to invoke the gnome-terminal.

Check your *history* and see what you were doing previously that may have triggered this issue:

In xterm:

```
history | more
```

Spacebar to page forward, "q" to quit.

---

