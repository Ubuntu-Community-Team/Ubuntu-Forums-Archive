---
title: "[SOLVED] Restarting programs with terminal"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-29
I want to restart conky without logging out and back in, is it possible to close or restart it using terminal?

---

### Post by Xerp on 2008-06-29
Yes.

```
sudo kill -HUP <processid>
``` will send a hangup request to a process, usually making it restart.

Many programs have init scripts, so you can do things like

```
sudo /etc/init.d/<program> restart
```

To use a specific instance, to start Konqueror, you'd just type

```
konqueror
``` to start it :)

If you have an icon, you can see the "launcher" information and just type that into a shell.

---

### Post by 91004 on 2008-06-29
Couldn't you just use the command line kill command?

---

### Post by adobrakic on 2008-06-29
> **91004 said:**
> Couldn't you just use the command line kill command?

Probably, but i'm new to linux and I have no idea what that even means. :/

---

### Post by iaculallad on 2008-06-29
Had you tried killall command:

To kill the process:

```
sudo killall conky
```

To start conky:

```
conky
```

Or press Alt+F2, enter "gnome-system-monitor" and use the "Process" tab to locate conky, right-click on it and select "Kill Process" if it exist. Restart it again by typing **conky** in your terminal.

---

