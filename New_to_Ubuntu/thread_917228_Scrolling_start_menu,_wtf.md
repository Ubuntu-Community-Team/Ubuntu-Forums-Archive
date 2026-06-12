---
title: "Scrolling start menu, wtf?"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by kenlar on 2008-09-11
My start menu looks like this:


[http://2.bp.blogspot.com/_JWR9m8H3nag/SMmVcjC8Q8I/AAAAAAAAAE8/w8Ka3EL5L5c/s1600-h/Screenshot.png](http://2.bp.blogspot.com/_JWR9m8H3nag/SMmVcjC8Q8I/AAAAAAAAAE8/w8Ka3EL5L5c/s1600-h/Screenshot.png)


How do I get rid off the "scrolling".... :confused:

---

### Post by starcannon on 2008-09-11
your link isn't appearing.

---

### Post by starcannon on 2008-09-11
oh that is odd indeed, are you using Ubuntu or Kubuntu?

If your using Ubuntu then the easiest thing to do may be to just delete some of the user preferences files, reboot, and let the OS restore to default.

**For Gnome(Ubuntu)**

Open a terminal {Applications>Accessories>Terminal}

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Then reboot.

[B]---------------------------------------
[/B]
For KDE(Kubuntu)

Looking into it, perhaps a KDE user could answer this one?

---

