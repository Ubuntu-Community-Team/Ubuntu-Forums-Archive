---
title: "How to: Change Desktop on Ubuntu"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by skozzy on 2008-06-10
I have been looking at the other available releases of ubuntu and notice they have a different desktop interface (gnome, kde etc...) but run the same OS, so I was wondering if I can install other ones without stuffing up the clean working installs of ubuntu. I'd like to see them without having to download a huge ISO and without have to do a reinstall.

---

### Post by Xiong Chiamiov on 2008-06-10
You can install them all by installing the *-desktop package (for helping installing things, see [here]("http://monkeyblog.org/ubuntu/installing/")).  For instance, you can install Kubuntu on top of Ubuntu by installing the kubuntu-desktop package.

There are actually 3 packages (at least for KDE) that differ slightly in what they give.  Kubuntu-desktop installs all of the applications and things that come with a Kubuntu install, just as if you had downloaded Kubuntu instead.  KDE includes KDE (obviously) and a few other meta-packages (some games and such), while kde-core (my package of choice) installs just KDE and the bare minimum to get it to run.  It's also a lot easier to remove if you don't want it anymore.

---

### Post by nothingspecial on 2008-06-10
If you use gnome(Ubuntu) -
```
sudo apt-get install kubuntu-desktop
```
If you use kde (Kubuntu)
```
sudo apt-get install ubuntu-desktop
```

Not tried it with the other flaviurs but I`m sure it would work.

---

### Post by Xiong Chiamiov on 2008-06-10
If you use aptitude instead of apt-get it will make removal quite a bit easier.  And yes, the other flavors are also all there.

---

### Post by nothingspecial on 2008-06-10
What is the difference between aptitude and apt-get?

---

### Post by Xiong Chiamiov on 2008-06-10
Aside from the fact that aptitude has a fake console-gui (ncurses, is that it? try by just entering "aptitude" into a terminal), aptitude does a better job of tracking what packages get automatically installed.  So then, when you install the kubuntu-desktop package, a whole load of other packages are installed (the kubuntu-desktop package itself is rather small).  If you used apt-get to install it, removing it will remove only it, and not all those other packages.  If you used aptitude, however, you'll remove those as well.

---

### Post by skozzy on 2008-06-10
Sounds easy enough. And if using 'aptitude' what would the remove command be?

---

### Post by hyper_ch on 2008-06-10
Have a look at the Playing Around section:  [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Xiong Chiamiov on 2008-06-10
> **skozzy said:**
> Sounds easy enough. And if using 'aptitude' what would the remove command be?
```

sudo aptitude remove kubuntu-desktop

```

You'll find that the aptitude command just kinda [make more sense]("http://pthree.org/2007/08/12/aptitude-vs-apt-get/").

---

### Post by hyper_ch on 2008-06-10
I used to use aptitude but have reverted back to apt... sometimes aptitude just wants to remove other stuff that I still want and that's a big "no no" for me.

---

### Post by d.kusummmanth@gmail.com on 2008-06-10
i think just adding **-remove** to the line, instead of install should be sufficient.

---

