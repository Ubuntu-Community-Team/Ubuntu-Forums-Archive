---
title: "Default Apps"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by PashConscious on 2012-03-25
Hi, me again.

Just installed Ubuntu 11.10 on my other PC now as well and, you guessed it, problems.

I can't ge the default applications to work! I've installed VLC and Amarok and changed them in Default Applications, I have also selected default application for .avi (right click menu) as VLC as well and they still open in Movie Player!! REALLY annoying me this morning :(

---

### Post by MG&amp;TL on 2012-03-25
Well, let's try a couple of things. First, let's try running the application as root and applying this system-wide:

Alt-F2:

```
gksu gnome-control-center
```

then click Details->Default Applications and change it there.

If that doesn't work, from my google trawl, let's try this command in a terminal:

```
sudo update-desktop-database
```

Sorry for the seemingly random answers, it's just that there is quite a few things that this could be caused by.

---

