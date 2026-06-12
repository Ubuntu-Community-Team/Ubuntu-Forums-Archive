---
title: "Moving files from Home to their appropriate location"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by Drowz0r on 2013-04-08
Hello everyone

I've found that many things install by default to the Home directory. As you can imagine this isn't really where they are meant to go. It seems most of them belong in the "opt" folder but when trying to drag and drop them, it seems I need some kind of special permission (like super user or something).

I'm not entirely sure on how to move them. Can it only be done with the terminal?

Thank you all

---

### Post by PowerBarry43 on 2013-04-08
run from a terminal

```
sudo nautilus
```

not sure what kind of thing you're talking about when you say things installing to the home directory by default

---

### Post by Drowz0r on 2013-04-08
Ah ha, yeah that's it.

Games seem to default and some other apps too. It would seem they are meant to be in the opt folder.

Thank you!

---

### Post by wildmanne39 on 2013-04-08
If you start moving things around you will probably make them stop working.

In the home folder you do not need root to run them if you move them you may end up needing root.

---

### Post by mamamia88 on 2013-04-08
Also you may think stuff installs to home but more than likely it's just storing configuration files etc there.

---

### Post by deadflowr on 2013-04-08
> **Drowz0r said:**
> Ah ha, yeah that's it.

Games seem to default and some other apps too. It would seem they are meant to be in the opt folder.

Thank you!

Are these things you've manually tried to install, or is it how the system's installation process does it?

If it's the way the system did it, then how it was is probably for the best.

I know a few games install data files in the home folder, with the engines and libraries where they need to be.
And wine games always install to the home folder.

---

### Post by Algus on 2013-04-09
Linux uses the same kind of directory system as Windows and OS X so you may think that they all operate quite similarly.  This is a mistake with Linux though as even though it looks familiar, especially if you are peering at the folders via a graphical file manager, the way Linux organizes those directories and what it expects to find in each one is quite different from Windows.

---

