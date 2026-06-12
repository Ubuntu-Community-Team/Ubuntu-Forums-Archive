---
title: "[SOLVED] How do I say no to updates?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-06-12
The updates today in Update Manager are for Gnome Card Games. I don't want them. How do I take them off the list?


.

---

### Post by Grishka on 2008-06-12
you can block a package version from updating by running synaptic, navigating to that package, and choosing package/lock version from the menu.

---

### Post by ibuclaw on 2008-06-12
Personally, I use pinnings on the repositories and only allow Security Updates to Install on my box.

How I set it up:
```

sudo touch /var/lib/synaptic/preferences
sudo ln -s /var/lib/synaptic/preferences /etc/apt/preferences

```
Then to open the preferences file
```
gksu gedit /etc/apt/preferences
```
And to set it up to put Security on full priority and the Main repository as the second in line, put in the following into the file.
```

Package: *
Pin: release a=hardy-security
Pin-Priority: 1001

Package: *
Pin: release a=hardy
Pin-Priority: 900

```

And save.
NOTE: the Pin-Priority: 1001 line will force downgrade packages if there are higher versions than the one in the security repository installed.
To prevent this behaviour, set the Pin-Priority to 1000.

Regards
Iain

---

### Post by Sealbhach on 2008-06-12
That's fantastic, thanks guys.


.

---

