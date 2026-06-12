---
title: "How do I trigger Gnome in Ubuntu 13.10?"
date: 2014-03-11
forum: New to Ubuntu
---

### Post by tichon on 2014-03-11
Been using Ubuntu 12 and I had an option to switch to Gnome at the login screen, however not seeing it with this fresh install pf 13.10.

---

### Post by Vladlenin5000 on 2014-03-11
Well, the fresh install doesn't come with Gnome, only Unity (assuming you installed the standard Ubuntu).

---

### Post by monkeybrain20122 on 2014-03-12
I don't know if it is a good idea to mix gnome-shell (which needs to be installed first) and unity in the same system. I read stories about broken desktops on this forum.

---

### Post by ibjsb4 on 2014-03-12
If you are talking about Gnome Classic (fallback)

```
sudo apt-get install gnome-panel
```

And choose at login.

---

### Post by monkeybrain20122 on 2014-03-12
> **ibjsb4 said:**
> If you are talking about Gnome Classic (fallback)

```
sudo apt-get install gnome-panel
```

And choose at login.

Shouldn't that be gnome-session-flashback?

---

### Post by ibjsb4 on 2014-03-12
> **monkeybrain20122 said:**
> Shouldn't that be gnome-session-flashback?

Installing gnome-panel will also install flashback and installing flashback will also install gnome-panel :)

[http://packages.ubuntu.com/saucy/gnome-panel](http://packages.ubuntu.com/saucy/gnome-panel)

[http://packages.ubuntu.com/saucy/gnome-session-flashback](http://packages.ubuntu.com/saucy/gnome-session-flashback)

Since OP is coming from 12o4 I made reference to Classic (fallback).

---

