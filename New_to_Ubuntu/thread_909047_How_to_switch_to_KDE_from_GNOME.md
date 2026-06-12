---
title: "How to switch to KDE from GNOME?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by Qu0ll on 2008-09-03
I would like to try KDE in Ubuntu 8.04 but can't see how to switch to it from GNOME.  How do I do it?

Thanks,

-Qu0ll

---

### Post by hyper_ch on 2008-09-03
```

sudo apt-get install kubuntu-desktop

```

And then at the login screen select KDE as session type.

---

### Post by owenll on 2008-09-03
I would advise you to read this first:

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by SkonesMickLoud on 2008-09-03
> **hyper_ch said:**
> ```

sudo apt-get install kubuntu-desktop

```

And then at the login screen select KDE as session type.

I would advise using "aptitude" as it makes it much easier to remove if one doesn't like it.

```
sudo aptitude install kubuntu-desktop
```

And for removal, should you decide to:

```
sudo aptitude remove kubuntu-desktop
```

If you use "apt-get" to install, removal consists of:

```
sudo apt-get remove packageA packageB packageC and on and on until all of KDE is gone
```

---

### Post by hyper_ch on 2008-09-03
aptitude often also wants to remove packages because of certain recommended dependencies.

---

