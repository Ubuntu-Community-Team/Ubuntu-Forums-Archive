---
title: "Adjusting to KDE vs Gnome"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by FredJones on 2008-05-18
I had Ubuntu 8.04 but had a problem (that this forum couldn't quite solve) so I am trying Kubuntu 8.04 (KDE 3) and it's a bit different. A few questions I have:

1. Is it possible to get netspeed to appear on the panel like I had in Gnome? If so, how? I have it installed in the system but it's not in my 'add to panel' list. The KDE one is not nearly as good for me.

2. How can I install Gnome Time Tracker? The package gtt or gttr is not found. I installed gnome-utils but it's still not in my KDE menus.

3. Why is that that virtualbox packages that I can install using apt-get (like the modules-generic or some such that I had to install) do not appear in Adept?

Thanks.

---

### Post by cardinals_fan on 2008-05-18
Install knetstats.  Then add it to the panel.

---

### Post by sdennie on 2008-05-18
2. To install gnome time tracker, it should just be:

```

sudo apt-get install gnotime

```

However, I would look at karm (should be installed by default).  It's actually much nicer than gnotime.

---

### Post by FredJones on 2008-05-19
> **cardinals_fan said:**
> Install knetstats.  Then add it to the panel.

Great. Thanks!

> **vor said:**
> 2. To install gnome time tracker, it should just be:

```

sudo apt-get install gnotime

```

However, I would look at karm (should be installed by default).  It's actually much nicer than gnotime.

Yes, I looked at karm, but I don't see any real reporting features there. gnotime has a full set of reports available--I in particular like to see a list of time segments created for each day.

Thanks for the 'gnotime' however! :)

---

